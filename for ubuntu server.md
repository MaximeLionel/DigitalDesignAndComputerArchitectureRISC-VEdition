`ping: sendmsg: Required key not available` 是一个常见的错误，表明 WireGuard 的配置可能存在问题，或者 VPN 隧道没有成功建立。

以下是针对该问题的排查与解决步骤：

---

## 1. **检查 WireGuard 配置是否启动**
在客户端（Ubuntu Server）和服务器（阿里云）上分别执行以下命令，确保 WireGuard 配置已正确加载：

```bash
sudo wg show
```

你应该看到类似以下输出：
```
interface: wg0
  public key: <你的公钥>
  private key: (hidden)
  listening port: 51820

peer: <对端的公钥>
  endpoint: <对端的公网IP>:51820
  allowed ips: 10.0.0.0/24
  latest handshake: <显示时间>
  transfer: <数据流量>
```

- 如果没有任何输出，说明 WireGuard 配置未加载。
- 如果 `latest handshake` 是空的，则两端的 WireGuard 并未成功通信。

---

### 如果配置未启动：
在两端分别启用 WireGuard：

```bash
sudo systemctl start wg-quick@wg0
```

并确认其状态：
```bash
sudo systemctl status wg-quick@wg0
```

---

## 2. **检查 WireGuard 配置文件**

在两端检查 `/etc/wireguard/wg0.conf` 是否正确，特别注意以下几点：

### **阿里云服务器的配置文件**
（示例 `wg0.conf`）
```ini
[Interface]
PrivateKey = <阿里云服务器的私钥>
Address = 10.0.0.1/24
ListenPort = 51820

[Peer]
PublicKey = <Ubuntu Server的公钥>
AllowedIPs = 10.0.0.2/32
```

### **Ubuntu Server 的配置文件**
（示例 `wg0.conf`）
```ini
[Interface]
PrivateKey = <Ubuntu Server的私钥>
Address = 10.0.0.2/24

[Peer]
PublicKey = <阿里云服务器的公钥>
Endpoint = <阿里云服务器的公网IP>:51820
AllowedIPs = 0.0.0.0/0
PersistentKeepalive = 25
```

- `PrivateKey` 和 `PublicKey` 必须对应。
- `AllowedIPs` 和 `Endpoint` 必须正确设置。
- 注意阿里云服务器上的 `AllowedIPs` 是 `10.0.0.2/32`，而客户端可以设置为 `0.0.0.0/0`（如果需要全局流量走 VPN）。

保存后重新启动 WireGuard：
```bash
sudo systemctl restart wg-quick@wg0
```

---

## 3. **检查防火墙配置**

阿里云服务器和 Ubuntu Server 本地的防火墙规则可能会阻止 WireGuard 流量。

### 在阿里云服务器上：
确保阿里云的安全组允许 `51820/UDP` 端口（或你设置的 WireGuard 端口）对外开放。

1. 登录阿里云控制台，找到对应的实例。
2. 进入 **安全组** 配置，检查是否存在以下规则：
   - **类型**: UDP
   - **端口范围**: 51820
   - **授权对象**: 0.0.0.0/0（或指定的客户端 IP）

---

### 在 Ubuntu Server 上：
使用以下命令检查 `ufw`（如果启用了防火墙）：
```bash
sudo ufw status
```

如果防火墙启用，需要允许 WireGuard 的流量：
```bash
sudo ufw allow 51820/udp
```

还需要允许虚拟网卡 `wg0` 的流量：
```bash
sudo ufw allow in on wg0
sudo ufw allow out on wg0
```

---

## 4. **检查网络连通性**

在 Ubuntu Server 上测试能否到达阿里云服务器的公网 IP：
```bash
ping <阿里云服务器公网IP>
```

- 如果公网 IP 不可达，可能是网络问题，需要排查路由或阿里云服务器的配置。
- 如果公网 IP 可达，但 VPN IP (`10.0.0.1`) 不可达，可能是 WireGuard 配置问题。

---

## 5. **日志排查**

检查 WireGuard 的日志，获取更多调试信息：

### 查看系统日志
```bash
sudo journalctl -u wg-quick@wg0
```

- 如果日志中显示 `Handshake did not complete`，说明两端无法建立通信，可能是密钥或端口配置错误。
- 如果没有任何错误，检查是否有流量从对端进入 WireGuard。

---

## 6. **其他可能原因**
- **密钥对错误**：确保使用的是正确的私钥和公钥，并且每个设备的私钥和对端的公钥对应。
- **NAT 问题**：如果阿里云服务器后面有 NAT，需要确保转发规则正确。
- **路由问题**：检查是否正确配置了 WireGuard 的虚拟网络路由。

可以使用以下命令查看路由表：
```bash
ip route
```

---

## 7. **验证 VPN 隧道通信**

在成功启动 WireGuard 后，尝试通过 `wg` 命令验证通信状态：
```bash
sudo wg
```

- 检查 `latest handshake` 是否有时间戳。如果没有，表示通信未成功。
- 检查 `transfer` 的数据流量是否有增加。如果流量为 0，表示没有数据通过隧道。

---

### 总结

通过以上步骤，可以逐步排查问题。大多数情况下，问题出在以下方面：
1. 配置文件错误（密钥、IP、端口）。
2. 防火墙阻止了流量。
3. WireGuard 服务未正确启动。

完成修正后重新测试 `ping` 是否可以到达对端的 VPN IP（例如 `10.0.0.1`）。
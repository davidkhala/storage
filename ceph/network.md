所以 Ceph 的客户端（包括 OpenPages 的 Ceph driver）会：
1. 先连 MON（3300）
  - RADOS Messenger v2 protocol
3. MON 返回 Ceph OSD 列表
  - OSD: Object Storage Daemon
  - 动态端口，来自ephemeral port range，是由MON统一管理的
  - Linux的默认 ephemeral port range: 32768 – 60999
  - 也可以通过ceph的`ms_bind_port_min`和`ms_bind_port_max` 来强制OSD端口范围，不推荐
4. 客户端再去连每个 OSD 的随机端口
5. 使用 RADOS 协议 读写数据

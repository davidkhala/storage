所以 Ceph 的客户端（包括 OpenPages 的 Ceph driver）会：
1. 先连 MON（6789/3300）
2. MON 返回 OSD 列表
3. 客户端再去连每个 OSD 的随机端口
4. 使用 RADOS 协议 读写数据

# multi-vendor support for Phpipam snmp

目前仅修改了get_vlan_table函数，支持H3C vlan获取。
为了方便修改，docker部署时请将文件映射出来，修改后重启容器即可。

```- ./phpipam/functions/classes/class.SNMP.php:/phpipam/functions/classes/class.SNMP.php```

1. 在 phpIPAM 的 设备 中，添加一个名为 `manufacturer`的必填自定义字段。
2. 添加设备时填写字段信息，添加的信息需与php文件内保持一致（不区分大小写）。
3. 修改class.snmp.php，添加新厂商支持：
    在 set_snmp_queries() 中添加厂商的 OID 映射，
    参考 get_vlan_table() 函数修改其他函数或添加其他厂商支持。
4. 替换文件，重启容器或服务。
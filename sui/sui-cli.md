
查询版本号
sui --version
sui -V

### 地址
查询当前保存了密钥的所有地址
sui client addresses

查询当前在用的地址
sui client active-address

导入地址
sui keytool import "<助记词>" ed25519

切换地址
sui client switch --address <addr>

移除地址
sui client remove-address <addr>

### 网络
查询当下所有的网络
sui client envs

添加新的网络
sui client new-env --alias <ALIAS> --rpc <RPC>

切换网络
sui client switch --env [network alias]




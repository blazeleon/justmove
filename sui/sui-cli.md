

### client
- 查询当前保存了密钥的所有地址
    ```bash
    sui client addresses
    ```

- 查询当前激活在用的地址
    ```bash
    sui client active-address
    ```

- 创建新的地址
    ```bash
    sui client new-address ed25519
    ```

- 切换地址
    ```bash
    sui client switch --address <addr>
    ```

- 移除地址
    ```bash
    sui client remove-address <addr>
    ```

### keytool
- 导入地址
    ```bash
    sui keytool import "<助记词>" ed25519
    ```

### network
- 查询当下所有的网络
    ```bash
    sui client envs
    ```

- 添加新的网络
    ```bash
    sui client new-env --alias <ALIAS> --rpc <RPC>
    ```

- 切换网络
    ```bash
    sui client switch --env [network alias]
    ```




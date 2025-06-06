

### `Address` 常用操作
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

- 导入地址
    ```bash
    sui keytool import "<助记词>" ed25519
    ```

- 切换地址
    ```bash
    sui client switch --address <addr>
    ```

- 移除地址
    ```bash
    sui client remove-address <addr>
    ```

- 查询当前地址可用于支付的gas
    ```bash
    sui client gas
    ```

- 获取 gas （开发测试环境）
    ```bash
    sui client faucet
    ```
    > 一般会让去浏览器领取，防止 gas 代币被恶意获取消耗

    > 另外也可以执行以下命令获取 gas 
    ```bash
    curl --location --request POST 'https://faucet.testnet.sui.io/v2/gas' \
    --header 'Content-Type: application/json' \
    --data-raw '{
        "FixedAmountRequest": {
            "recipient": "<your-address>"
        }
    }'
    ```

### `Network` 常用操作
- 查询当下所有的网络
    ```bash
    sui client envs
    ```

- 添加新的网络
    ```bash
    sui client new-env --alias <ALIAS> --rpc <RPC>
    ```
    > 例如添加主网：
    > sui client new-env --alias=mainnet --rpc https://fullnode.mainnet.sui.io:443


- 切换网络
    ```bash
    sui client switch --env [network alias]
    ```

### 合约开发
- 创建智能合约项目
    ```bash
    sui move new <project-name>
    ```

- 对当前项目进行编译
    ```bash
    sui move build
    ```

- 执行单元测试
    ```bash
    sui move test
    ```

- 发布合约至区块链网络
    ```bash
    sui client publish
    ```
    > 为此次交易设置的最大 Gas 费用预算（单位：MIST，1 SUI = 1e9 MIST）。需预估合理范围，过低会导致交易失败
    例如：
    ```bash
    sui client publish --gas-budget 10000000
    ```

- 合约调用
    ```bash
    sui client call [OPTIONS]
    ```

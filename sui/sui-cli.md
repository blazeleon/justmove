

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
    sui client new-address ed25519 [alias]
    ```
    > alias 可选，不填会默认随意生成一个别名。对于常用的地址建议自行设置一个别名，管理和使用都方便。如果创建时或后续想修改别名，你可以在 `～/.sui/sui_config`目录下找到 `sui.aliases`文件进行手动修改。

- 导入地址
    ```bash
    sui keytool import "<助记词>" ed25519
    ```

- 切换地址
    ```bash
    sui client switch --address <address or alias>
    ```

- 移除地址
    ```bash
    sui client remove-address <address or alias>
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

- 合约升级
    ```bash
    sui client upgrade --upgrade-capability <upgrade object id>
    ```

- 合约调用
    ```bash
    sui client call [OPTIONS]
    ```
    > 例如：调用 `sui-framework` 下 `coin` 模块的 `mint_and_transfer<T>(c: &mut TreasuryCap<T>,amount: u64,recipient: address,ctx: &mut TxContext) ` 函数

    ```bash
        sui client call \
        --package 0x2 \
        --module coin \
        --function mint_and_transfer \
        --type-args "0x..." \
        --args "0x..." "1000000000000000" "0x...""
    ```

    > 特别注意的是 `type-args` 是指函数上的范型的类型，有多个范型，传参也就传多个。 命令行换行用 `\`
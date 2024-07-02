# Trump at Work (TRUMP) Token

## 概述
Trump at Work (TRUMP) 是一个基于Solana的代币，总供应量为10亿个。该代币的智能合约地址为：

地址: `7fHekYQ9R4cz4kPwCMH3ZjbQAtvgRBFmhF3GwxBVS6Sg`

## 代币信息
- **名称**: Trump at Work
- **符号**: TRUMP
- **总供应量**: 1,000,000,000 TRUMP

### 查询代币余额
```javascript
// 使用智能合约地址与TRUMP代币交互
const contractAddress = '7fHekYQ9R4cz4kPwCMH3ZjbQAtvgRBFmhF3GwxBVS6Sg';

// 使用Solana Web3.js与智能合约交互的示例代码
const solanaWeb3 = require('@solana/web3.js');

// 创建连接
const connection = new solanaWeb3.Connection(solanaWeb3.clusterApiUrl('mainnet-beta'));

// 定义代币合约地址
const tokenAddress = new solanaWeb3.PublicKey(contractAddress);

// 查询余额函数
async function getBalance(walletAddress) {
    const publicKey = new solanaWeb3.PublicKey(walletAddress);
    const balance = await connection.getTokenAccountBalance(publicKey);
    console.log(`Balance: ${balance.value.uiAmount} TRUMP`);
}

// 调用函数
const walletAddress = '用户钱包地址';
getBalance(walletAddress);

转账

// 执行代币转账操作
const contractAddress = '7fHekYQ9R4cz4kPwCMH3ZjbQAtvgRBFmhF3GwxBVS6Sg';

// 使用Solana Web3.js执行转账的示例代码
const solanaWeb3 = require('@solana/web3.js');

// 定义转账函数
async function transferTokens(fromWallet, toWallet, amount) {
    const fromPublicKey = new solanaWeb3.PublicKey(fromWallet);
    const toPublicKey = new solanaWeb3.PublicKey(toWallet);

    // 构建转账交易
    const transaction = new solanaWeb3.Transaction().add(
        solanaWeb3.SystemProgram.transfer({
            fromPubkey: fromPublicKey,
            toPubkey: toPublicKey,
            lamports: amount,
        })
    );

    // 签名并发送交易
    const signature = await solanaWeb3.sendAndConfirmTransaction(connection, transaction, [fromWallet]);
    console.log(`Transaction successful with signature: ${signature}`);
}

// 调用函数
const fromWallet = '发起转账的钱包地址';
const toWallet = '接收转账的钱包地址';
const amount = 1000000; // 转账数量，以Lamports为单位
transferTokens(fromWallet, toWallet, amount);
贡献
欢迎大家提交Issue和Pull Request，参与我们的代币项目开发！

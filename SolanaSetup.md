# Solana 开发学习之安装和运行

## 相关链接
- [官方文档](https://docs.solanalabs.com/cli/install)
- [Solana Cookbook 中文版](https://solanacookbook.com/zh/getting-started/installation.html#%E5%AE%89%E8%A3%85%E5%91%BD%E4%BB%A4%E8%A1%8C%E5%B7%A5%E5%85%B7)
- [Solana 中文课程](https://www.solanazh.com/course/1-4)
- [开发者指南](https://solana.com/zh/developers/guides/getstarted/setup-local-development)

## 实操

### 安装

本地开发环境设置指南：
https://solana.com/developers/guides/getstarted/setup-local-development

其他： 

参考 https://mp.weixin.qq.com/s/_v63t3t9PgAbeLb4sLepBQ 

Solana 开发学习之Solana 基础知识 / 寻月隐君
### Install the Solana CLI
```bash
//downloading v1.18.2 installer ✨ 1.18.22
sh -c "$(curl -sSfL https://release.anza.xyz/v1.18.22/install)"

// initializedAdding to .profile
export PATH="/home/samman/.local/share/solana/install/active_release/bin:$PATH"

...

// initializedAdding to /Users/qiaopengjun/.profile
export PATH="/Users/qiaopengjun/.local/share/solana/install/active_release/bin:$PATH" 

...
```

通过运行以下命令确认您已安装了所需的 Solana 版本：

```bash
solana --version
# 实操solana --versionsolana-cli 1.18.2 (src:13656e30; feat:3352961542, client:SolanaLabs)
```

切换版本
```
solana-install init 1.16.4
```

我们会用到TypeScript语言来编写交易测试脚本，所以还需要安装node.js和TypeScript相关的工具链：
```
# 1. 安装 nvm
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.1/install.sh | bash

# 2. 让 nvm 在命令行生效，我这里是.zshrc，你的可能是.bashrc，看你的具体环境
source ~/.zshrc

# 3. 安装 node 长期支持版本（--lts）
nvm install --lts
nvm use --lts

# 4. 安装 yarn（node安装好，就有了npm命令）
npm install -g yarn

# 我安装的版本：
# nvm  0.40.1
# node v22.11.0
# npm  10.9.0
# yarn 1.22.22
```

### 设置网络环境
官方RPC地址分别是：
```
DevNet: https://api.devnet.solana.com
TestNet: https://api.testnet.solana.com
MainNet: https://api.mainnet-beta.solana.com
```

### 安装Anchor
--------

`anchor`是solana的开发框架，开发solana合约要经常使用，它的底层封装了solana-web3.js，用于跟solana链上程序交互，可以类比为以太坊中的hardhat框架。

```
# cargo是rust的包管理器和构建工具\
# 上文安装好了rust，就自带了cargo命令\
cargo install --git https://github.com/coral-xyz/anchor avm --locked --force

# 使用最新的anchor版本就行，我的是 anchor-cli 0.30.1\
avm install latest\
avm use latest`
```

### 初始化一个Anchor程序
```
# solana-guide是自定义的，你可以使用任何名称
anchor init solana-guide
cd solana-guide
anchor build
```

Error: lock file version 4 requires `-Znext-lockfile-bump`
Change `Cargo.lock` at head
```
- version = 4
+ version = 3
```

### 启动一个solana测试节点
打开一个新的shell（原来的anchor项目shell不要关），执行如下命令：
```
# 1. 配置solana在本地运行
solana config set --url localhost 

# 2. 启动一个本地节点
solana-test-validator
```

### 生成一个solana钱包，并运行测试
回到anchor项目所在的shell，执行如下命令：
```
# 1. 生成solana钱包地址
solana-keygen new -o ~/.config/solana/id.json

# 2. 查看钱包地址
solana address

# 3. 给生成的钱包空投 sol 测试币
solana airdrop 100 {钱包地址}

# 4. 配置 program_id 与 Anchor 密钥同步
anchor keys sync

# 5. 执行测试命令
anchor test --skip-local-validator
```

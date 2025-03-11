# Solana 开发学习之Solana 基础知识
## Install the Solana CLI

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
```bash
//downloading v1.18.2 installer ✨ 1.18.2
sh -c "$(curl -sSfL https://release.solana.com/v1.18.2/install)"

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
curl -fsSL https://deb.nodesource.com/setup_15.x | sudo -E bash -
sudo apt-get install -y nodejs npm
npm install -g typescript
npm install -g ts-node
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


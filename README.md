# Public_Test_Bridge_Tools
Tools for interacting with the bridge smart contracts on Ropsten Testnet. The bridge for *testnet* is:

**Address**: [0xbE39479b1fE065Fdd3510E8997738eb22DfA3357](https://ropsten.etherscan.io/address/0xbE39479b1fE065Fdd3510E8997738eb22DfA3357)

Bridges for other networks are available in the [docs folder](./docs/bridges.md)
## Test Tokens:
| Token Name | Token Address | Details |
|:----------:|:-------------:|:-------:|
|    tDai    | [0xBe3304136265290BDdBc0930CB6F26c3428929e2](https://ropsten.etherscan.io/token/0xBe3304136265290BDdBc0930CB6F26c3428929e2)              | [x](./docs/tokens.md#tdai)        |
|    tBTC    | [0x7778F85d0Ceb51950cD9AE24086af723069865fC](https://ropsten.etherscan.io/token/0x7778F85d0Ceb51950cD9AE24086af723069865fC)              | [x](./docs/tokens.md#tbtc)        |
|    tUSDC   | [0x2c6984bff4f8a3e13f071112085773D78B28F1F2](https://ropsten.etherscan.io/token/0x2c6984bff4f8a3e13f071112085773D78B28F1F2)              | [x](./docs/tokens.md#tusdc)        |
|    tEURO   | [0x0f4c414fe20C998023A14207FA6E1176D4D4F4fb](https://ropsten.etherscan.io/token/0xbE39479b1fE065Fdd3510E8997738eb22DfA3357)              | [x](./docs/tokens.md#teuro)        |
|    tVOTE   | [0xBab9201f25642e9917C3CDFb0d491A5ea13Df8A0](https://ropsten.etherscan.io/token/0xBab9201f25642e9917C3CDFb0d491A5ea13Df8A0)              | [x](./docs/tokens.md#tvote)        |

All of these tokens have the `faucet()` function and are already supported on testnet.

**NOTE**: It's highly suggested for you to install the MetaMask plugin for [Chrome](https://chrome.google.com/webstore/detail/metamask/nkbihfbeogaeaoehlefnkodbefgpgknn?hl=en) or [Firefox](https://addons.mozilla.org/en-GB/firefox/addon/ether-metamask/). Just install the plugin and follow the instructions on-screen to create your wallet. Once installed, click on the Network at the top of the plugin screen and select "**Ropsten Test Network**" (see image below)


# Console
Faucets for all of the tokens above are available from within Vega Console. After logging in to an appropriate [Vega Wallet](https://github.com/vegaprotocol/go-wallet), open up the Account drawer, go to 'Manage' under the appropriate asset, and follow the instructions there

# Interacting with the contracts
Sometimes, you don't want the Vega Console to do everything for you. Here's how to request tokens fromm the contracts directly. To follow the instructions below, you'll need to have some Ropsten Ether to cover the gas costs. [Instructions available here]](./dopcs/ropsten_eth.md).

## Token Faucet:
**NOTE: These instructions will work for any of the above-listed test tokens**

To deposit test tokens into Vega via the ERC20 bridge, you must first have the tokens.

Luckily, there's a faucet for that!

**If you want to follow a quick how-to to add a test token to your wallet:**

1. Go to: https://www.myetherwallet.com/ (**make sure is the .com, any other is a scam/phishing website that would corrupt your wallet and steal everything!!!**)
2. Click on "Access my Wallet"
3. Select "MEW CX" and allow the access to your wallet
4. Click on "Contract" -> "Interact with Contract"
5. In the new page, copy the desired Test Token address from the list above.
6. In the ABI/JSON interface, copy and paste the content of the JSON file available here https://github.com/vegaprotocol/Public_Test_Bridge_Tools/blob/master/TOKEN%20ABI/token_abi.json
7. Click "Continue"
8. Click "Select an Item" and in the dropdown list select "Faucet"

<p align="center"><img width="478" alt="Dropdown list" src="https://user-images.githubusercontent.com/66724202/88392705-62959900-cdb4-11ea-9958-de1af0f9520e.png" class="center"></p>

9. Leave ETH field with 0 and just click "Write"
10. A window from MetaMask will popup and you just need to select "Continue" (see image below)

<p align="center"><img width="238" alt="MetaMask popup" src="https://user-images.githubusercontent.com/66724202/88390894-0da45380-cdb1-11ea-9221-056afab68a1b.png" class="center"></p>

11. Wait some time until you get the notification that the transaction has been completed, and if you click on the MetaMask plugin, and select "Assets" you should be able to see the token asset like in the image below

<p align="center"><img width="238" alt="MetaMask Assets" src="https://user-images.githubusercontent.com/66724202/88391027-417f7900-cdb1-11ea-831d-b1a79fca570e.png" class="center"></p>

## Depositing test tokens into ERC20 Bridge

### MyEtherWallet.com (MEW) + MetaMask
First of all you need to obtain tokens from the test token faucet using the instructions above.

**Approve ERC20 Bridge to move your test tokens** (You need **MetaMask** installed - see above)

1. Go to: https://www.myetherwallet.com/ (**make sure is the .com, any other is a scam/phishing website that would corrupt your wallet and steal everything!!!**)
2. Click on "Access my Wallet"
3. Select "MEW CX" and allow the access to your wallet
4. Click on "Contract" -> "Interact with Contract"
5. In the new page, under "Contract Address" copy the Test Token address from the list above
6. In the ABI/JSON interface, copy and paste the content of the JSON file available here https://github.com/vegaprotocol/Public_Test_Bridge_Tools/blob/master/TOKEN%20ABI/token_abi.json
7. Click "Continue"
8. Click "Select an Item" and in the dropdown list select "Approve"

<p align="center"><img width="478" alt="Dropdown list" src="https://user-images.githubusercontent.com/66724202/88393164-20208c00-cdb5-11ea-8163-524524c68dcb.png" class="center"></p>

9. In the "Spender (address)" field copy/paste the Target ERC20 BRIDGE (Ropsten) address from the list above.
10. In the "Value (uint256)" field write in the number of tokens you would like to deposit followed by 5 zeros (00000) (example: if you want to limit to 1000 tokens you need to write: `100000000`)
11. leave the ETH at 0 (DON'T TOUCH IT) and click "Write"
12. MetaMask will request to confirm that you allow MEW to spend your tokens, click "Confirm" (see image below)

<p align="center"><img width="238" alt="Here select CONFIRM" src="https://user-images.githubusercontent.com/66724202/88394400-4ba47600-cdb7-11ea-8e66-e2df46e87c61.png"></p>

12. Wait for the transaction to be completed.

**Run `deposit_asset` function on ERC20 Bridge - Deposit assets on Vega PubKey**

1. If you are already on https://www.myetherwallet.com/ with an address selected, click "Clear all" at the bottom and move to step 6, otherwise continue to the next step
2. Go to: https://www.myetherwallet.com/ (**make sure is the .com, any other is a scam/phishing website that would corrupt your wallet and steal everything!!!**)
3. Click on "Access my Wallet"
4. Select "MEW CX" and allow the access to your wallet
5. Click on "Contract" -> "Interact with Contract"
6. In the new page, under "Contract Address" copy the Vega ERC20 BRIDGE (Ropsten) address from the list above
7. In the ABI/JSON interface, copy and paste the content of the JSON file available here https://github.com/vegaprotocol/Public_Test_Bridge_Tools/blob/master/bridge/Vega_Bridge_ERC20_abi.json
8. Click "Continue"
9. Click "Select an Item" and in the dropdown list select "deposit_asset"

<p align="center"><img width="478" alt="Dropdown list" src="https://user-images.githubusercontent.com/66724202/88395091-6aefd300-cdb8-11ea-9a6f-f029a41d9020.png"></p>

10. In the "Asset_source (address)" field paste the Test Token (Ropsten) address from the list above
11. In the "Asset_id (uint256)" field leave zero (0)
12. In the "Amount (uint256)" field write the amount of tokens you would like to deposit followed by 5 zeros (00000) (example: if you want to deposit 1 token you need to write: `100000`) **NOTE: It cannot be above the previously selected limit**
13. In the "Vega_public_key (bytes32)" copy/paste the Vega PubKey (**prepend the PubKey with 0x**) for the Vega Account you would like the tokens to be credited for this deposit. You can find it in Console by clicking on "Hosted Wallet" (top right), then below "Select Key for Trading" click on "view" next to the relevant key, and then click "copy" (see images below)

<p align="center"><img width="238" alt="Click on Hosted Wallet" src="https://user-images.githubusercontent.com/66724202/88395723-6c6dcb00-cdb9-11ea-9e53-bbd831d837f0.png"> <img width="238" alt="Click on View" src="https://user-images.githubusercontent.com/66724202/88395750-742d6f80-cdb9-11ea-8cc6-5f8c976d4d93.png"> <img width="238" alt="Click copy" src="https://user-images.githubusercontent.com/66724202/88395772-7db6d780-cdb9-11ea-9d6e-47d240488ed2.png"></p>

14. Leave the ETH field with 0 (Don't touch it!) and click "Write"
15. MetaMask will request to confirm that you allow MEW to spend your test tokens, click "Confirm" (see image below)

<p align="center"><img width="238" alt="Here select CONFIRM" src="https://user-images.githubusercontent.com/66724202/88396301-43016f00-cdba-11ea-8711-d5d56cab9668.png"></p>

16. Wait for the transaction to be completed
17. Your tokens have been deposited into Vega and will be credited to the provided Vega Public Key

## Autogeneration of ABI documentation in CI

The CI pipeline looks for files named `*_abi.json`, and builds them into readme files using [`@vegaprotocol/simple-abi-docgen`](https://github.com/vegaprotocol/simple-abi-docgen).

Updated readme files are pushed with a git commit message of "`Update ABI documentation [NOCI]`".

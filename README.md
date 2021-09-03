# Multi-Blockchain Wallet in Python

We recently expended our portfolio management services from supporting traditional assets to including crypto-assets. We created a HD wallets to manage the vast diversity of the cryptocurrencies. We used a command line tool, `hd-wallet-derive` that supports not only BIP32, BIP39, and BIP44, but also supports non-standard derivation paths for the most popular wallets. This enables us to manage billions of addresses across 300+ coins and tokens, which giving us an edge against our competitors.



# We installed the following operating systems and dependencies: 

- [HD Wallet Derive Installation Guide](Resources/HD_Wallet_Derive_Install_Guide.md) 
- [Blockchain TX Installation Guide](Resources/Blockchain_TX_Install_Guide.md).
- installed PHP operating system
- Python Bitcoin library.
- Web3.py, Python Ethereum library.


We completed the following steps:

- set up the project by creating a directory `wallet`, cloned the `hd-wallet-derive` tool into a folder and install it using the [HD Wallet Derive Installation Guide]

- created a symlink, `derive` for the `hd-wallet-derive/hd-wallet-derive.php` script by running the following commaned `ln -s hd-wallet-derive/hd-wallet-derive.php derive`. 

- Create a file called `wallet.py` -- this will be your universal wallet script. You can use [this starter code](Starter-Code/wallet.py) as a starting point.


# In a separate file, `constants.py`, we set the following constants:
  - `BTC = 'btc'`
  - `ETH = 'eth'`
  - `BTCTEST = 'btc-test'`

# In `wallet.py`, we imported all constants: `from constants import *`


- Generated a 12 word mnemonic by using (https://iancoleman.io/bip39/).

- Set the mnemonic as an environment variable by storing an `.env` file and importing it into my `wallet.py`.



### Derived the wallet keys

- Create a function called `derive_wallets`

- Use the `subprocess` library to create a shell command that calls the `./derive` script from Python.

- Use Mnemonic (`--mnemonic`) was set from an environment variable.

- Create a dictionary object called `coins` that uses the `derive_wallets` function to derive `ETH` and `BTCTEST` wallets.

- Use `bit` and `web3.py` to leverage the keys stored in the `coins` object by creating functions such as `priv_key_to_account`. 

- For `ETH`, return an object containing `to`, `from`, `value`, `gas`, `gasPrice`, `nonce`, and `chainID`.
             
- For `BTCTEST`, return `PrivateKeyTestnet.prepare_transaction(account.address, [(to, amount, BTC)])`


### Send transactions

- We fund these wallets using testnet faucets.
- run the command `python` to open the Python shell. 
- Within the Python shell, run the command `from wallet import *`.
- We set the account with  `priv_key_to_account` and use `send_tx` to send transactions.

  - **Bitcoin Testnet transaction**

    - Funded a `BTCTEST` address using [this testnet faucet](https://testnet-faucet.mempool.co/).


  - **Local PoA Ethereum transaction**

    - Added one of the `ETH` addresses to the pre-allocated accounts
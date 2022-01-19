# Background
-	Your new startup is focusing on building a portfolio management system that supports not only traditional assets like gold, silver, stocks, etc, but crypto-assets as well! The problem is, there are so many coins out there! It's a good thing you understand how HD wallets work, since you'll need to build out a system that can create them.
-	You're in a race to get to the market. There aren't as many tools available in Python for this sort of thing, yet. Thankfully, you've found a command line tool, hd-wallet-derive that supports not only BIP32, BIP39, and BIP44, but also supports non-standard derivation paths for the most popular wallets out there today! However, you need to integrate the script into your backend with your dear old friend, Python.
-	Once you've integrated this "universal" wallet, you can begin to manage billions of addresses across 300+ coins, giving you a serious edge against the competition.
# Dependencies
-	PHP must be installed on your operating system
-	We have to clone the hd-wallet-derive tool
-	bit Python Bitcoin library
-	web3.py Python Ethereum library
# Set-up
-	Clone the hd-wallet-derive tool into this folder and install it using the HD Wallet Derive Installation Guide
-	Create a symlink called derive for the hd-wallet-derive/hd-wallet-derive.php script. This will clean up the command needed to run the script in our code, as we can call ./derive instead of ./hd-wallet-derive/hd-wallet-derive.php:
-	Make sure you are in the top level project directory - in this case the directory named wallet. Run the following command: ln -s hd-wallet-derive/hd-wallet-derive.php derive. Test that you can run the ./derive script properly, by running the following command. 
o	./derive --key=xprv9zbB6Xchu2zRkf6jSEnH9vuy7tpBuq2njDRr9efSGBXSYr1QtN8QHRur28QLQvKRqFThCxopdS1UD61a5q6jGyuJPGLDV9XfYHQto72DAE8 --cols=path,address --coin=ZEC --numderive=3 -g
	 
o	Create a file called wallet.py -- this will be your universal wallet script. You can use this starter code as a starting point.

# Setup Constants
-	In a separate file, constants.py, set the following constants:
-	In wallet.py, import all constants: from constants import *
-	Use these anytime you reference these strings, both in function calls, and in setting object keys
# Generate a mnemonic
a.	Generate a new 12 word mnemonic using hd-wallet-derive or by using this tool.
b.	Set this mnemonic as an environment variable, and include the one you generated as a fallback using:mnemonic = os.getenv('MNEMONIC', 'insert mnemonic here')
# Deriving a wallet
-	Pass as variables Mnemonic (--mnemonic), Coin (--coin) and Numderive (--numderive), then set the --format=json flag, parse the output into a JSON object using json.loads(output).And finally pass all into one function, called 'derive_wallets'.
-	When done properly, the final object should look something like this (there are only 3 children each in this image):


# Linking the transaction libraries
-	BTCTest transaction
-	```btc_acc = priv_key_to_account(BTCTEST,btc_PrivateKey) ``` ```create_trx(BTCTEST,btc_acc,"miZgMxdGzSxCTpWazfD2KqhewoUvcQ6CC1", 0.1)``` ```send_trx(BTCTEST,btc_acc,'miZgMxdGzSxCTpWazfD2KqhewoUvcQ6CC1',0.1)```
c.	Confirmation of Executed Transaction

# ETH transaction - using local private blockchain
-	```eth_acc = priv_key_to_account(ETH,eth_PrivateKey) ```
-	```create_trx(ETH,eth_acc,"0xba51af165c60A32B3d23Df9B332b4A86cED4A1B9", 1000)``` 
-	```send_trx(ETH, eth_acc,"0xba51af165c60A32B3d23Df9B332b4A86cED4A1B9", 1000)```
i.	

## Air-gapped communication & transacting with Sparrow Wallet
Sparrow Wallet is a Bitcoin wallet designed to be connected with your own node and ran from your desktop or laptop computer. This is a user-friendly wallet with an intuitive interface and many advanced features for a range of capabilities. To learn more about Sparrow Wallet and for installation instructions, visit the [Sparrow Wallet website](https://www.sparrowwallet.com/).

In this guide you will see how to connect your COLDCARD to Sparrow Wallet using your own BitcoinCore node. If you don't have your own Bitcoin node, you can use reputable public Electrum servers as demonstrated in the [UltraQuick guide](https://github.com/econoalchemist/ColdCard-UltraQuick). However, there are privacy tradeoffs that come with using the convenience of a public Electrum server. Luckily there are a number of resources available to help you spin up your own Bitcoin node, to learn more check out:

- [BitcoinCore.org](https://bitcoincore.org/en/about/)
- [Ministry of Nodes](https://www.ministryofnodes.com.au/) 
- [Sparrow Wallet Documentation](https://www.sparrowwallet.com/docs/connect-node.html)  

Once you have your BitcoinCore node ready, there are a couple steps needed to configure it to work with Sparrow Wallet. 

If you have BitcoinCore running on the same computer as Sparrow Wallet, then all you need to do is open the `bitcoin.conf` configuration file and add `server=1` near the top and save it. Then relaunch BitcoinCore. You may have a blank configuration file if this was a new BitcoinCore install and that is fine.  

Alternatively, if you are running BitcoinCore on a remote computer, you need to add a username & password and the Remote Procedure Calls (RPC) binding local IP addresses in the configuration file. To do this, navigate to the `bitcoin.conf` configuration file and open it in your preferred text editor. Then add the local IP address for your node and the local IP address for your desktop. For example:

`rpcuser=pi`

`rpcpassword=Nakamoto21`

`rpcbind=127.0.0.1`

`rpcbind=192.168.0.11 #(your node)`

`rpcallowip=127.0.0.1`

`rpcallowip=192.168.0.12 #(desktop)`

<p align="center">
  <img width="605" height="378" src="Assets/Sparrow20.png">
</p>

Save those changes and then you should be able to connect to your BitcoinCore node from your computer on the same local network. Make sure you restart BitcoinCore after saving those changes. 

Now you are ready to configure Sparrow Wallet to talk to your BitcoinCore node. Once you have Sparrow Wallet installed and launched, you will be presented with an empty user interface. Navigate to `File` > `Preferences`.

<p align="center">
  <img width="814" height="611" src="Assets/Sparrow0.png">
</p>

Then click on the <kbd>Server</kbd> tab on the left-hand side. Click on the <kbd>Bitcoin Core</kbd> tab for the `Server Type`. If running BitcoinCore on the same computer, use the `127.0.0.1` rpcbind IP address with `8332` as the port and the default authentication option. Or if running BitcoinCore on a different computer, use the same User/Pass that you entered in the `bitcoin.conf` file. Either way, set the Data Folder directory to the same folder the `bitcoin.conf` file is being written. This should be the same directory that BitcoinCore writes the `.cookie` file that Sparrow Wallet needs to read. Test the network connection from Sparrow Wallet. If it’s good, you should see the green check mark next to <kbd>Test Connection</kbd> and some information populated in the dialog box below that. Then you can close that window.   

<p align="center">
  <img width="752" height="662" src="Assets/Sparrow21.png">
</p>

Unfortunately, BitcoinCore stores your public keys and balances unencrypted on the computer it is running on. Although your bitcoin are not directly at risk of theft, if this computer is regularly connected to the internet, it is at risk to hackers - which has the potential to make you a target if your balance and geographic location are discovered. To learn more about Sparrow Wallet best practices, check out [this Sparrow Wallet resource](https://www.sparrowwallet.com/docs/best-practices.html). 

Now that Sparrow Wallet is connected with BitcoinCore, this is a good time to get the watch-only wallet file exported from the COLDCARD. Then it can be imported to Sparrow Wallet. So connect your COLDCARD to the COLDPOWER adaptor and log into the COLDCARD. 

In order to keep your COLDCARD air-gapped, the Partially Signed Bitcoin Transaction (PSBT) can be utilized to spend bitcoin from the COLDCARD without ever connecting it to the internet. Basically, the public information from the COLDCARD called an XPUB will be used to import the necessary information into Sparrow Wallet on our desktop. By doing this, Sparrow Wallet will be able to generate receive addresses and QR codes, monitor the COLDCARD's balance, and initiate PSBT's. All without exposing any of the private information from the COLDCARD, like the signing key. 

You will use the microSD card to transfer information between the desktop and the COLDCARD. Ensure the microSD card is inserted to the COLDCARD. 

First, the `.json` file needs to be exported from the COLDCARD, which will contain all the public information necessary so that Sparrow Wallet can import this watch-only wallet. From the COLDCARD main menu select `Advanced` > `MicroSD Card` > `Export Wallet` > `Generic JSON`. 

<p align="center">
  <img width="400" height="352" src="Assets/IMG_5780.JPG">
  <img width="400" height="352" src="Assets/IMG_5789.JPG">
</p>

<p align="center">
  <img width="400" height="352" src="Assets/IMG_5798.JPG">
  <img width="400" height="352" src="Assets/IMG_5809.JPG">
</p>

This is going to write the file to the microSD card, then you can connect that microSD card to your desktop computer with your USB adaptor. Copy/paste the exported `.json` file to your desktop from the microSD card. Note the file location and now you will switch back to Sparrow Wallet to get it ready to import the `.json` file. 

In Sparrow Wallet, create a new wallet by selecting `File` > `New Wallet`, then you will be asked to name this wallet. Name the wallet whatever you want then click on <kbd>Create Wallet</kbd>. You will notice in the Sparrow Wallet interface lower right-hand corner that the color has changed to green on the toggle switch. This indicates that your wallet is using your instance of BitcoinCore as the back end.

<p align="center">
  <img width="814" height="611" src="Assets/Sparrow22.png">
</p>

You will see the following screen, you can leave all the settings on the defaults. Then select <kbd>Airgapped Hardware Wallet</kbd>. 

<p align="center">
  <img width="814" height="611" src="Assets/Sparrow23.png">
</p>

A screen will pop up and you can click on the <kbd>Import File...</kbd> button next to the COLDCARD icon. This will open your file explorer where you can point Sparrow Wallet to the file location containing the exported COLDCARD `.json` file. Select that file and click on <kbd>open</kbd>. 

<p align="center">
  <img width="452" height="339" src="Assets/Sparrow24.png">
</p>

After a moment, you will see a summary of the wallet you are about to apply. You will notice a "Master fingerprint" dialog box with 8-characters in it. You can use this unique identifier to confirm that you are importing the correct wallet from your COLDCARD. 

On your COLDCARD, from the main menu, navigate down to `Advanced` > `View Identity` and you can compare the displayed fingerprint to the one displayed in Sparrow Wallet. This is especially important to confirm if you have added a passphrase which will be covered in the [Paranoid guide](https://github.com/econoalchemist/ColdCard-Paranoid)

If everything looks good, then click on <kbd>Apply</kbd> in Sparrow Wallet. 

<p align="center">
  <img width="814" height="611" src="Assets/Sparrow25.png">
  <img width="814" height="350" src="Assets/Sparrow26.png">
</p>

After clicking on <kbd>Apply</kbd>, you will have the opportunity to add a password to your wallet. This is a password which will encrypt the Sparrow Wallet data file that is saved on your computer. This password can protect your wallet if someone else gains access to your desktop and Sparrow Wallet file. If you forget your password, you will need to create a new wallet file by repeating this whole process. 

<p align="center">
  <img width="814" height="611" src="Assets/Sparrow27.png">
</p>

You can also save a list of deposit addresses from your COLDCARD and compare this saved list to Sparrow Wallet to ensure the correct wallet is loaded without having to retrieve your COLDCARD, login to it, and compare the deposit addresses there. To do this, select the `Receive` tab in Sparrow Wallet then you can view the first receiving address from your COLDCARD and its QR code. On your COLDCARD, make sure you insert the microSD card and enter your passphrase if applicable. Then from the main menu, select `Address Explorer`. This will bring up a few address types that you can choose to view. Your COLDCARD can use legacy P2PKH Bitcoin addresses that start with "1", or nested SegWit P2SH Bitcoin addresses that start with "3", or Native SegWit Bech32 Bitcoin addresses that start with "bc1". Then you want to press <kbd>1</kbd> and this will save the first 250 addresses to a `.csv` file on your microSD card. You can also open the `addresses.csv` file with a text editor on your desktop to view the 250 addresses you exported from your COLDCARD and compare them to your Sparrow Wallet just for the added assurance. 

<p align="center">
  <img width="950" height="470" src="Assets/Sparrow64.png">
</p>

After applying the changes, you can now navigate through your watch-only wallet in Sparrow Wallet. On the left-hand side of the Sparrow Wallet interface there are six tabs. The <kbd>Transactions</kbd> tab is where you can see information related to the transactions in this watch-only wallet. The <kbd>Send</kbd> tab is where you can create the PSBTs to then export for signing by the COLDCARD. The <kbd>Receive</kbd> tab is where you can generate receive address for your COLDCARD without having to plug in your COLDCARD and log into it. The <kbd>Addresses</kbd> tab shows several deposit and change addresses as well as any balances. The <kbd>UTXOs</kbd> tab shows any unspent transaction outputs and a small graph charting the history. Finally, the <kbd>Settings</kbd> tab is where you can see detailed information about the watch-only wallet such as the master fingerprint, derivation path, & xpub.   

Now you can click on the <kbd>Receive</kbd> tab on the left-hand side of the Sparrow Wallet interface. Then you will be presented with a bitcoin receiving address, a QR code, and some additional details. You can scan this QR code with your mobile Bitcoin wallet, for example, and deposit some bitcoin to your COLDCARD. You should see the transaction show up in Sparrow Wallet after a moment along with a pop-up notification. Also, in BitcoinCore, the transactions should show up there as well. The transaction will remain in a pending status until it receives some blockchain confirmations. In the mean-time, you can click on the <kbd>Transactions</kbd> tab and review further details about your transaction. You can also copy/paste your transaction ID in [mempool.space](https://mempool.space/) to watch for your first confirmation, or use whatever your preferred block explorer is. [Tor Browser](https://www.torproject.org/download/) is a privacy-focused browser.  

<p align="center">
  <img width="950" height="405" src="Assets/Sparrow28.png">
  <img width="950" height="676" src="Assets/Sparrow29.png">
  <img width="950" height="399" src="Assets/Sparrow30.png">
  </p>

Now you can power off and secure your COLDCARD in a safe place until you want to sign a transaction and spend from it, several addresses will be cataloged in Sparrow Wallet so you can continue depositing to your COLDCARD via Sparrow Wallet without having to reconnect it every time. It is best practice to confirm each receiving address on the COLDCARD itself and or your saved `.csv` file and additionally to only use each address once. 

When you are ready to sign a transaction to spend bitcoin, it is necessary to create a PSBT in order to maintain the air-gapped benefit. You can deposit bitcoin with your COLDCARD disconnected but to spend bitcoin, the COLDCARD needs to sign the transaction. Sparrow Wallet is used to build the transaction based on your available Unspent Transaction Outputs (UTXOs) and the information you enter when constructing the transaction. The PSBT details are passed between Sparrow Wallet and the COLDCARD using the microSD card. 

To create a PSBT, navigate to the <kbd>Spend</kbd> tab on the left-hand side in Sparrow Wallet. There, you can paste the address you are sending to, add a label, enter an amount to send, and choose a miners fee rate, etc. Once you have everything set, click on <kbd>Create Transaction</kbd>. On the next screen, double check the details then click on <kbd>Finalize Transaction for signing</kbd>. Then you will be asked what you want to do with the finalized PSBT. In this case, click on <kbd>Save Transaction</kbd> and Sparrow Wallet will launch the file explorer. Navigate to the microSD card and save the PSBT there. Then safely eject the microSD card.  

<p align="center">
  <img width="315" height="225" src="Assets/Sparrow31.png">
  <img width="315" height="225" src="Assets/Sparrow32.png">
  <img width="315" height="225" src="Assets/Sparrow33.png">
  </p>
  
Insert the microSD card into the COLDCARD. If necessary, power on your COLDCARD using the COLDPOWER 9v battery adaptor or USB adaptor. Then enter your COLDCARD PIN prefix, verify your anti-phishing words, and enter the PIN suffix. From the main menu choose `Ready to Sign`. Then the details of the PSBT will be displayed and you can confirm that the address and the amount and the miners fee are correct.    

<p align="center">
  <img width="300" height="236" src="Assets/IMG_5831.JPG">
  <img width="315" height="236" src="Assets/IMG_5839.JPG">
  <img width="300" height="236" src="Assets/IMG_5847.JPG">
  </p>
  
Then hit <kbd>OK</kbd> to sign. Once the file is signed it will be saved as a new file to the microSD card. You can then eject the microSD card and securely log out of your COLDCARD and power it down. 
 
<p align="center">
  <img width="600" height="473" src="Assets/IMG_5870.JPG">
</p>

Eject the microSD card from the COLDCARD, insert to the USB adaptor, insert the adaptor into the desktop computer. Ensure BitcoinCore and Sparrow Wallet are open. Then from the file explorer, simply double-click on the signed PSBT file and it should open automatically in Sparrow Wallet. Alternatively, from Sparrow Wallet navigate to `File` > `Open Transaction` then choose `File` from the menu of options and navigate to the file location of the signed PSBT. Either way, then click on the <kbd>Broadcast Transaction</kbd> button to send the signed transaction to the Bitcoin Network. 

<p align="center">
  <img width="814" height="611" src="Assets/Sparrow35.png">
  <img width="814" height="611" src="Assets/Sparrow34.png">
</p>
                                                          
At the time of broadcast you should see the transaction in BitcoinCore as well as receive a notification in Sparrow Wallet. Again, you can copy the transaction ID and paste in your preferred block explorer to watch for confirmations.
                                                          
<p align="center">
  <img width="950" height="410" src="Assets/Sparrow36.png">
</p>

The main point here is that your COLDCARD is the required signing device while your Sparrow Wallet is your interface, transaction builder, & broadcaster. In this configuration, Sparrow Wallet can do many things like catalog addresses and build transactions but without the signature from your COLDCARD, Sparrow Wallet cannot authorize spending of any of your bitcoin. 


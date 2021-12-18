# ColdCard Middle Ground Guide
A middle ground guide for experienced users to get started with an air-gapped cold storage wallet. 

<p align="center">
  <img width="750" height="406" src="Assets/MiddleGroundTitleImage-M.png">
</p>

This guide covers:
- Checking the tamper-evident bag
- Setting up a PIN
- Generating a seed phrase with some dice rolls
- Creating a passphrase
- Air-gapped communication between ColdCard and [Sparrow Wallet](https://www.sparrowwallet.com/)
- Backup recommendations

## Checking the tamper-evident bag:
Upon receiving your ColdCard, ensure that the tamper-evident bag has not been compromised. If anything seems amiss or if you have any problems contact [support@coinkite.com.](mailto:support@coinkite.com?subject=%5BContact%5D%20-%20) Visually inspect the surfaces and edges of the bag for indications of tampering, openings, or damage.

<p align="center">
  <img width="400" height="300" src="Assets/Bag0.png">
  <img width="400" height="300" src="Assets/Bag1.png">
</p>

<p align="center">
  <img width="400" height="300" src="Assets/Bag2.png">
  <img width="400" height="300" src="Assets/Bag3.png">
</p>

You will see the tamper-evident words "void" appear when the seal is opened. Inside you will find your new ColdCard, the Wallet Recovery Backup Card, sticker(s), and an additional copy of the bag number which should match the bag number printed on the outside of the bag. 

<p align="center">
  <img width="388" height="208" src="Assets/IMG_6079.JPG">
  <img width="399" height="277" src="Assets/IMG_6080.JPG">
</p>

If everything looks good, then you are ready to power on your new ColdCard and get it setup. 

## Setting up a PIN
Here is a diagram you can reference to learn the ColdCard's navigation:

<p align="center">
  <img width="853" height="505" src="Assets/Navigation.png">
</p>

A great security feature of the ColdCard is that it can be used completely air-gapped. Meaning that you never have to connect it to a computer, although that option is there if you choose to use it. You can use a standard USB outlet transformer or even a 9v battery with the ColdPower adaptor, which CoinKite offers [here](https://store.coinkite.com/store/cldpwr). To power on the ColdCard simply connect a USB to micro-USB [cable](https://store.coinkite.com/store/category/accessories) to the port on top of the ColdCard and the other end to a USB port on your ColdPower adaptor & 9v battery.

<p align="center">
  <img width="403" height="302" src="Assets/IMG_5557.JPG">
  <img width="403" height="302" src="Assets/IMG_5556.JPG">
</p>

Once powered on, first read and accept the terms of sale & use. Then you will be asked to confirm the bag number. If there are any discrepancies, contact [support@coinkite.com](mailto:support@coinkite.com?subject=%5BContact%5D%20-%20).

<p align="center">
  <img width="605" height="454" src="Assets/BagNumber.jpg">
</p>

Make careful considerations with your PIN number. You don't want to use one that is easy to guess. Your PIN will have two parts, a prefix and suffix. The idea is that once you enter the prefix, you will be presented with two anti-phishing words. If the words are the same as the words that were originally presented to you at initial startup, then you know that your ColdCard has not been tampered with since the last time you accessed it. 


First, select "Choose PIN Code", then you will see a brief description of how the PIN code works. Each part of your PIN code can be between 2 and 6 digits. There is absolutely no way to access a forgotten or lost PIN. Also, if you enter a PIN incorrectly too many times, it will brick your ColdCard as a security feature.

<p align="center">
  <img width="605" height="454" src="Assets/Choose PIN.jpg">
</p>

After hitting "OK" you will get one more warning about the risk of losing or forgetting your PIN. After reading that, you can enter your PIN prefix. Use the included notecard to write down your PIN prefix then hit "OK". 

<p align="center">
  <img width="454" height="341" src="Assets/EnterPreFix.jpg">
  <img width="454" height="341" src="Assets/EnterPreFix2.jpg">
</p>

Next you will be presented with your two anti-phishing words. Write these down on your notecard.

<p align="center">
  <img width="605" height="454" src="Assets/AntiPhishingWords.jpg">
</p>

Next, enter your PIN suffix, then write it down on the notecard and hit "OK".

<p align="center">
  <img width="454" height="341" src="Assets/EnterSuffix.jpg">
  <img width="454" height="341" src="Assets/EnterSuffix2.jpg">
</p>

Then you will be asked to re-enter your PIN prefix, confirm the two anti-phishing words, and enter your PIN suffix. The ColdCard will save that information and then open up the wallet where you can generate your seed phrase.

---
layout: post
title:  "A blockchain voting pass"
date:   2017-07-03 10:18:00
excerpt_separator: <!--more-->
---
The Dutch electoral voting system is designed in a way that does not fit in the current era of the digital transformation. Almost every procedure during the elections is done manually and change in policy is very difficult as it requires a change in legislation. This also applies to the voting pass, or stempas. A couple of weeks prior to the elections, this document is sent to the citizens by mail. Eventually, on election day, this document is needed along with a passport at the polling station in order to prove that the citizen is eligible to vote. <!--more-->

For the past ten weeks, I have been working with three other students (Wilko Meijer, Jonathan Raes and Rico Tubbing), the department of Distributed Systems at the Delft University of Technology and our client Milvum towards a more trustworthy, transparent and less expensive way of verifying the suffrage of a citizen. During this project, we built a fully functional ecosystem which makes it possible to replace the paper voting pass completely.

    "One step towards the digitalization of the entire voting process" 

This article will give you a quick introduction on how the system functions and explains the technology we used.
Technology

During the first part of the research we focused on the upcoming blockchain technology. Considering blockchain, this technology is a decentralized ledger of transactions. These transactions can send money or assets, just like the transactions in your bank account. However, every transaction on the blockchain is immutable and need to be cryptographically signed by the sender. Due to a decentralized design, the network is resilient against DDoS attacks and has no single point of failure.

The second part we have been working on, is the biometric passport standard. Dutch travel documents (passports, identity cards and driver's licences) are issued with a so called ePassport chip. This chip can be read via standard NFC and contains several details about the holder of the passport. For example, your name, place of birth and even your photo is stored on the chip. Besides this information, the chip also contains a couple of cryptographic tools. For example, a cryptographic signing function.
Proposed solution

In our proposed solution, we are combining these two technologies, blockchain and the ePassport chip, in order to make the paper voting pass superfluous. In this new situation, a couple of weeks prior to the elections, a voting pass for every citizen is stored on the blockchain. Eventually, on election day, the only thing the citizen needs to bring, is his passport, which chip is scanned at the polling station. Then the voting pass can be redeemed by signing a transaction using the cryptographic function in the passport. By using this methodology, we are 100% sure that the person who redeemed the voting pass was eligible to vote and could not tamper with the system.
Implementation

The implementation consists of two parts: a blockchain and an Android app which can be used by the polling station official in order to redeem the suffrage of a citizen.

During the implementation of the blockchain, we had to tackle an issue with the compatibility of the cryptographic standards. The so called elliptic curve which is used in the chosen blockchain implementation is different from the elliptic curve used by Dutch travel documents. In order to make them compatible we had to modify the source of the blockchain.

The second challenge was the implementation of the app for the polling station. Fortunately, the chip in a passport has a security measure that makes it impossible to scan it from a distance without actual possession to the passport. Before we can access the chip, the so called machine readable zone needs to be send to the chip. This machine readable zone is the group of letters on the bottom of the first page of your passport. However, we wanted the app to be easy to use, so we implemented an optical character recognition system, which enters these letters automatically.

Now we are able to access the chip in the passport by holding it to the back of an Android smartphone. The app checks if there is a voting pass stored on the blockchain. If there is a voting pass, a new transaction to redeem this voting pass is signed immediately. However, this transaction is not broadcast over the blockchain network, because the app shows the amount of voting passes that are found on the blockchain first. When this information is correct, pressing redeem vote will broadcast the transaction. After a few seconds a confirmation will show up, guaranteeing that the transaction is stored into a block on the blockchain.

So, in conclusion, this thesis presents a fully working prototype that can substitute the existing system of voting passes in the Netherlands for a digital one. It removes the necessity of sending paper voting passes to all Dutch citizens that are eligible to vote and improves the time needed for counting votes due to less manual labor.

This solution of a passport combined with a blockchain can be used by all kinds of organizations struggling with the identity problem. For example, this technology can be used in order to register as an organ donor or more commercially: a ticket for a concert can be redeemed using a passport or identity card.


---
layout: blog
topic: Blockchain
title: Bitcoin White Paper
tags: bitcoin blockchain
comments: true
date: 2022-02-05
---

# Blockchain Dark Forest Self Guard Handbook

![](/assets/Blockchain-Dark-Forest-Self-Guard-Handbook-d83367cf.png)

Access the most updated version [here](https://github.com/slowmist/Blockchain-dark-forest-selfguard-handbook)

Written by 余弦 [@evilcos](https://twitter.com/evilcos) from [SlowMist](https://www.slowmist.com/en/#home), a blockchain security firm.

I helped translating the [Wallet Backup](https://github.com/slowmist/Blockchain-dark-forest-selfguard-handbook#%E5%A4%87%E4%BB%BD%E9%92%B1%E5%8C%85) section from Chinese to English and attached my script below.

* * *


## Wallet Backup

This is where many people fall into the trap, including myself. I did not back up properly and I lost it. I knew it would happen sooner or later. Luckily, it was not my main wallet and my friends at DarkMist helped me recover some of the assets.  Still, it is a scary experience, and I don’t think anyone would want that to happen to them. So buckle up and let’s learn how to back up your wallet safely.

## Types of Seed Phrase / Private Key
When we talk about backing up a wallet, we are essentially talking about backing up a mnemonic phrase (which is an unencrypted version of the private key. For convenience, in the following paragraphs, we will only refer to it as a mnemonic phrase). Most mnemonic phrases can be categorized as follows:
* Plain Text
* Password-Encrypted (Passphrase)
* Multi-signature
* Shamir's Secret Sharing, or SSS for short

I will briefly explain each type.

### Plain Text

Plain text is easy to understand. Once you have those 12 English words, you own the assets in the wallet. You can consider doing some special shuffling, or even replace one of the words. However, you will have a big headache if you forget about your own rules. Do not think your memory is bulletproof. Believe me, one, two, or five years down the road, your memory will tangle up. A few years ago, when I used the Ledger hardware wallet, I fell into the trap. When I write down the 24-word-mnemonic phrase. I changed the order. After a few years, I forgot the order and I don’t remember if I changed any word. As mentioned earlier, my problem was solved using a special code breaker program that uses brute force to guess the correct sequence and words.

### Password-Encrypted (Passphrase)

According to the standard, mnemonic phrases can have a password. It’s still the same phrase but with the password, a different seed phrase will be obtained. The seed phrase is used to derive a series of private keys, public keys and corresponding addresses. So you should not only back up the mnemonic phrases, but also the password. By the way, private keys can also have a password and it has its own standards, such as BIP 38 for bitcoin and Keystore for ethereum.

### Multi-Signature

As the name suggests, it needs signatures from multiple persons to access the wallets. It’s very flexible as you can set your own rules. For example, if 3 people have the key (mnemonic words or private keys), you can require at least two persons to sign to access the wallets. Each blockchain has its own multi-signature solution. Many well-known Bitcoin wallets support multi-signature functions. However, in Ethereum, multi-signature is mainly realized through smart contracts, such as Gnosis Safe. Furthermore, MPC, or Secure Multi-Party Computation is gaining popularity right now. It is similar to the traditional multi-signature experience, but the technology is very different. Unlike multi-signature, MPC is blockchain agnostic and can work with all protocols.

### SSS, Shamir's Secret Sharing Scheme
Shamir Backup splits the seed into multiple shares (each share usually consists of 20 words). To recover the wallet, a specified number of shares has to be collected and used. Specific reference to industry best practices can be found here:

* [Keystore](https://support.keyst.one/advanced-features/recovery-phrase/import-or-create-shamir-backup)
* [Trezor](https://wiki.trezor.io/Shamir_backup)

Using schemes such as multi-signature and SSS will give you peace of mind and avoid single-point risks, but it could make management relatively complicated and sometimes multiple parties will be involved. There is always a compromise between convenience and security. It is up to the individual to decide but never be lazy in principles.

## Encryption

Encryption is a very, very broad concept. It doesn't matter if the encryption is symmetric, asymmetric or uses other advanced technologies; as long as an encrypted message can be easily decrypted by you or your disaster recovery team and not anyone else after many years, it is good encryption.

Based on the security principle of "zero trust", when we are backing up wallets, we have to assume that each step could be hacked, including the hardware environment like a safe. Keep in mind that there is none other than yourself who can be completely trusted. In fact, sometimes you can’t even trust yourself. You may forget something or get confused. But don’t be too scared; otherwise you may still screw it up. (not exactly sure what this last sentence is trying to say)

When backing up, special consideration must be given to disaster recovery. The main purpose of disaster recovery is to avoid a single point of risk. What will happen if you are gone or the environment where your backup is located is lost? Therefore, for important stuff, there must be disaster recovery personnel and there must be multiple backups.

I won’t elaborate too much on the disaster recovery personnel because it depends on who you trust. I will focus on multiple backups. Let's take a look at several basic forms of backup locations:

* Cloud
* Paper
* Device
* Brain

### Cloud
Many people are worried about cloud backup; they think it is vulnerable to hacker attacks.  At the end of the day, it is all about which side - the attacker or the defender - put in the most effort, whether it is labor or capital. Personally, I have more faith in cloud services provided by Google, Apple, Microsoft, etc., because I know how strong their security teams are and how big their budgets are. But in addition to guarding against external hackers, I am also very concerned about internal security risk control and private data protection. The few service providers I trust are relatively better in terms of risk management and avoidance. But nothing is absolute. If I choose these cloud providers to back up important data (like wallets), I will definitely encrypt the wallets at least one more time.

I strongly recommend mastering GPG. It not only provides for the aforementioned "signature verification" functionality, but also provides sufficient security in terms of encryption and decryption. You can learn more about GPG at [https://www.ruanyifeng.com/blog/2013/07/gpg.html](https://www.ruanyifeng.com/blog/2013/07/gpg.html)

Okay, you have mastered GPG :) Now that you have encrypted the password to your wallet (mnemonic phrase or private key) with GPG in a safe offline environment, you can throw the encrypted files directly into these cloud services and save it. All will be good. But here I need to remind you: never lose your GPG private key or the private key password...

At this point, you might find this extra level of security is quite troublesome: you have to learn about GPG and back up your GPG private key and passwords. In reality, if you have done all the aforementioned steps, you are already familiar with the process and won’t find it as difficult or troublesome. I will say no more because practice makes perfect.

If you want to be lazy, there is another possibility but its security may be discounted. I can't measure the exact discount but sometimes I will be lazy and I will consider using well-known tools to assist me. That tool is 1Password. The newest version of 1Password already supports direct storage of wallet-related content, such as mnemonic words, passwords, wallet addresses, etc., which is convenient for users. Other similar tools (such as Bitwarden) can also be used, but they are not as convenient.

### Paper

Many hardware wallets come with several high-quality paper cards on which you can write down your mnemonic phrases (in plaintext, SSS, etc.). In addition to paper, some people also use steel plates (fire-resistant, water-resistant and corrosion-resistant, of course, I have not tried those). Test it after you copy the mnemonic phrases and if everything works, put it in a place where you feel secure, such as in a safe. I personally like using paper because if properly stored, paper has a much longer lifespan than electronics.

### Device
It refers to all kinds of equipment; electronics are a common type for backup, such as a computer, an iPad, an iPhone, or a hard drive, etc, depending on personal preference. We also have to think about the secure transmission between devices. I feel comfortable using peer-to-peer methods such as AirDrop and USB where it is difficult for a middleman to hijack the process. I am just naturally uneasy about the fact that electronic equipment may break down after a couple of years, so I will maintain the habit of checking the device at least once a year. There are some repeated steps (such as encryption) which you can refer to the Cloud section.

### Brain
Relying on your memory is exciting. In fact, everyone has their own "memory palace". Memory is not mysterious and can be trained to make it work better. There are certain things that are indeed safer with memory. Whether to rely solely on the brain is a personal choice. But pay attention to two risks: first, time can cause memory to fade or cause confusion; the other risk is that you may have an accident. I will stop here and let you explore more.

Now you are all backed up. Don’t use too much encryption, otherwise you won’t remember anything after many years. According to the security principle of  "continuous verification", your encryption and backup methods, whether excessive or not, must be verified continuously, both regularly as well as randomly. The verification frequency depends on your memory and you do not have to complete the whole process. As long as the process is correct, partial verification is also possible. Finally, it is also necessary to pay attention to the confidentiality and security of the authentication process.

Okay, let’s take a deep breath here. Getting started is the hardest part. Now that you are ready, let’s enter this dark forest :)

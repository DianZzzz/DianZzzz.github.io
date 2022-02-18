---
layout: blog
course: Blockchain-and-Money
title: Blockchain Basics & Transactions
tags: blockchain crypto defi finance bitcoin btc cryptography
comments: true
date: 2022-02-15
---

# Blockchain Basics & Transactions

## Bitcoin Transaction Format

### Input
*  Previous Transaction ID
*  Index (indicate how much bitcoin for transaction)
*  Signature

### Output
*  Value in Satoshis
*  Public Key (bitcoin address)


## Coinbase Transaction
*  Generation of a freshly minited bitcoin
*  The only input is the coinbase block reward
*  Reward halves every 210,000 blocks (originally 50 bitcoins per block)
*  May include 100 bytes of arbitray data
*  The Genesis Bock included Headline from Financial Times: "The Times 03/Jan/2009 Chancellor on brink of second bailout for banks"

> 01000000 - version
> 
> 0000000000000000000000000000000000000000000000000000000000000000 - prev block
> 
> 3BA3EDFD7A7B12B27AC72C3E67768F617FC81BC3888A51323A9FB8AA4B1E5E4A - merkle root
> 
> 29AB5F49 - timestamp
> 
> FFFF001D - bits
> 
> 1DAC2B7C - nonce
> 
> 01 - number of transactions
> 
> 01000000 - version
> 
> 01 - input
> 
> 0000000000000000000000000000000000000000000000000000000000000000FFFFFFFF - prev output
> 
> 4D - script length
> 
> 04FFFF001D0104455468652054696D65732030332F4A616E2F32303039204368616E63656C6C6F72206F6E206272696E6B206F66207365636F6E64206261696C6F757420666F722062616E6B73 - scriptsig
> 
> FFFFFFFF - sequence
> 
> 01 - outputs
> 
> 00F2052A01000000 - 50 BTC
> 
> 43 - pk_script length
> 
> 4104678AFDB0FE5548271967F1A67130B7105CD6A828E03909A67962E0EA1F61DEB649F6BC3F4CEF38C4F35504E51EC112DE5C384DF7BA0B8D578A4C702B6BF11D5FAC - pk_script
> 
> 00000000 - lock time

translated into 

> 00000000   01 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00   ................
> 
> 00000010   00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00   ................
> 
> 00000020   00 00 00 00 3B A3 ED FD  7A 7B 12 B2 7A C7 2C 3E   ....;£íýz{.²zÇ,>
> 
> 00000030   67 76 8F 61 7F C8 1B C3  88 8A 51 32 3A 9F B8 AA   gv.a.È.ÃˆŠQ2:Ÿ¸ª
> 
> 00000040   4B 1E 5E 4A 29 AB 5F 49  FF FF 00 1D 1D AC 2B 7C   K.^J)«_Iÿÿ...¬+|
> 
> 00000050   01 01 00 00 00 01 00 00  00 00 00 00 00 00 00 00   ................
> 
> 00000060   00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00   ................
> 
> 00000070   00 00 00 00 00 00 FF FF  FF FF 4D 04 FF FF 00 1D   ......ÿÿÿÿM.ÿÿ..
> 
> 00000080   01 04 45 54 68 65 20 54  69 6D 65 73 20 30 33 2F   ..EThe Times 03/
> 
> 00000090   4A 61 6E 2F 32 30 30 39  20 43 68 61 6E 63 65 6C   Jan/2009 Chancel
> 
> 000000A0   6C 6F 72 20 6F 6E 20 62  72 69 6E 6B 20 6F 66 20   lor on brink of 
> 
> 000000B0   73 65 63 6F 6E 64 20 62  61 69 6C 6F 75 74 20 66   second bailout f
> 
> 000000C0   6F 72 20 62 61 6E 6B 73  FF FF FF FF 01 00 F2 05   or banksÿÿÿÿ..ò.
> 
> 000000D0   2A 01 00 00 00 43 41 04  67 8A FD B0 FE 55 48 27   *....CA.gŠý°þUH'
> 
> 000000E0   19 67 F1 A6 71 30 B7 10  5C D6 A8 28 E0 39 09 A6   .gñ¦q0·.\Ö¨(à9.¦
> 
> 000000F0   79 62 E0 EA 1F 61 DE B6  49 F6 BC 3F 4C EF 38 C4   ybàê.aÞ¶Iö¼?Lï8Ä
> 
> 00000100   F3 55 04 E5 1E C1 12 DE  5C 38 4D F7 BA 0B 8D 57   óU.å.Á.Þ\8M÷º..W
> 
> 00000110   8A 4C 70 2B 6B F1 1D 5F  AC 00 00 00 00            ŠLp+kñ._¬....

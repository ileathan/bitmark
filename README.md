**Forking** Why fork this when you can fork [Pfennig](https://github.com/project-bitmark/pfennig) - it's made to be cloned.


Project Bitmark is a multi faceted project which aims to provide:

1. A **relatively stable cryptographic currency network** which balances the requirements of all parties involved.
2. A **far reaching adoption initiative** under the guise of novel reputation+currency system called [Marking](https://github.com/project-bitmark/marking/wiki)

This repository contains the Bitmark cryptograpic currency software, and a wiki which provides all details pertaining to the software, it's configuration and the rationale of all design decisions.

# Bitmark

[![Join the chat at https://gitter.im/project-bitmark/bitmark](https://badges.gitter.im/Join%20Chat.svg)](https://gitter.im/project-bitmark/bitmark?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

Bitmark aims to be a relatively stable, user focussed, crypto currency, which refines and implements maturing innovations from the crypto currency sector.

### Overview
**Technically**: Light and stable with a modern codebase, [maturing features from the alternative currency sector](https://github.com/project-bitmark/bitmark/wiki#maturing-innovations) which *benefit* users added on a faster timeline than bitcoin. Think of it more as [standardization rather than innovation](https://github.com/project-bitmark/bitmark/wiki#relatively-stable).

**User focussed**: Daily development effort and innovation goes in to making bitmark as [user friendly, and simple to integrate](https://github.com/project-bitmark/bitmark/wiki#user-focussed) as possible.

**Earned Value**: Every aspect of Project Bitmark is focused on earned value. It's a project to make a viable every day currency, any value will be earned. 

**Longevity**: A well funded Bitmark Foundation is being created and funded by the community to support long term development. The foundation is to be specified and formed by the 13th July 2015.

**Distribution**: A [configuration](https://github.com/project-bitmark/bitmark/wiki#block-chain-parameters) which aims to ensure [fair distribution](https://github.com/project-bitmark/bitmark/wiki/Currency#supply-and-distribution) whilst using [proven PoW](https://github.com/project-bitmark/bitmark/wiki#proof-of-work) which has had substantial investment in hardware. Extensive distribution of the currency is achieved through wide spread adoption under the banner of [Marking](https://github.com/project-bitmark/marking/wiki).

**Balance**: Every aspect of Bitmark has been designed in order to balance the interests of everybody involved or associated with the project. This includes [Investor Public Mining (IPM)](https://github.com/project-bitmark/bitmark/wiki/IPM-Pool) which balances Investors, Miners, and Developers in a way that is mutually beneficial and which critically enables those at the core to provide the best network experience to those who rely on it, the users.

* [Project Project - Documentation and Plan](https://github.com/project-bitmark/bitmark/wiki)
* [Discussion and Updates](https://bitcointalk.org/index.php?topic=660544.0)

## Getting Bitmark

All Bitmark software releases are published through the github release process, you can download the [latest release](https://github.com/project-bitmark/bitmark/releases) from the releases tab above.

## mPOW Hard Fork (branch 0.9.7)

We are now in the testing phase of the hard fork that allows for multiple proof-of-work algorithms (SHA256D, SCRYPT, ARGON2, LYRA2R2, X17). Each algorithm has its difficulty adjusted independently, with a target spacing of 10 min (so 2 min as before if we consider blocks mined by any algorithm). The subsidy reduces at the same emission points as before, but each algorithm contributes only 1/5 of the number of emitted coins. The peak hash rate that determines the subsidy scaling factor is now dynamic (depends on at most 1 year of hashing history for each algorithm) and the scaling factor remains constant throughout each 24 hour period (it is updated every 144 blocks).

To test, you can download the current version from this branch, and put the following settings in your bitmark.conf

rpcuser=bitmarkrpc
rpcpassword=YoUrPaSsWoRd
testnet=1
debug=1
listen=1

You can mine all algorithms but Argon2 using cpuminer-multi (https://github.com/tpruvot/cpuminer-multi), with the following command:

`cpuminer -a <algo> -o http://localhost:19266 -u bitmarkrpc -p YoUrPaSsWoRd`

`<algo>` is `sha256d`, `scrypt`, `x17`, or `lyra2REv2`

Note: you have to change the `miningAlgo` variable in src/rpcmining.cpp

You can also use the bitmark-cli command to mine. For example, to mine argon2,

`bitmark-cli setgenerate true <ncores> 3`

---
title: What is higan and how I build it
date: "2020-05-04"
spoiler: R.I.P.
cta: "react"
---


## What is higan

https://higan-bana.com/

Higan is a public, trustable, and unforgotten database for people who needs to be remembered.

For people who died because of COVID-19.

What does that mean?

Until now, there are [248,811](https://corona-stats.online/) people who died because of COVID-19. Many people lost their families, friends, and heroes in this disaster. I think we need a place to remember these people.

- Public - You can submit some information about people you know. And that information will be public, which means anyone can access it.

- Trustable - The project is open source, you can build your own service and synchronize all the data.

- Unforgotten - This is a blockchain project where all data is tracked and recorded. When more people are involved, the data is harder to tamper with and less likely to be lost.

In addition to COVID19, you can also record those people you love and respect. You can think of Higan as an Internet tombstone.

`Higan` is a Japanese word(Chinese: 彼岸) for another place where the dead are going.
`Higan Bana` is a Japanese word(Chinese: 彼岸花). It's a flower that is described in Chinese to guide the dead into the next reincarnation.

## How I built it.

There are two separate projects, Higan and Higan-ui.

### Higan

https://github.com/daoleno/higan

Higan is a blockchain project based on [cosmos-sdk](https://github.com/cosmos/cosmos-sdk).

The Cosmos-SDK is a framework for building blockchain applications in Golang. It's like ruby-on-rails for ruby.

![Tendermint stack](https://dev-to-uploads.s3.amazonaws.com/i/z1l75r6k27s1ghylrl9f.jpg)

Higan is a `cosmos-sdk` application. So as shown in the figure.

- `higancli`(command line tool of higan) will start a rest server that accepts API requests.
- The rest server sends a request message to `higand` (ABCI APP developed through cosmos-sdk) via `tendermint`.
- `higand` will validate the message, handle it, and store the transaction in multistore, which is multiple key-value databases built into `cosmos-sdk`.
- Status and transactions will be synchronized in the P2P network via `tendermint`.

Here, cosmos-sdk has developed many modules such as auth, bank, etc. that allow you to easily develop a [PoS](https://en.wikipedia.org/wiki/Proof_of_stake)-based blockchain.

Tendermint does the very heavy work of [pBFT](https://en.wikipedia.org/wiki/Byzantine_fault)-based consistency layer, p2p layer, etc. and can easily synchronize the state between nodes

So what I need to do is develop a module called `tombstone`.
This module handles my custom messages and writes the record to the multistore.

Eventually, there will be two programs, `higand` to run the blockchain and `higancli` to send or query transactions to `higand`.

### Higan-ui

https://github.com/daoleno/higan-ui

It is a very simple front end of the `higand` server. It can display the records that have been stored on the blockchain, submit a record, show the height of the block, and show the number of records. It also has a very rudimentary search feature.

I use react, react-hooks, and tailwindcss to build it.

I really hate `CSS`, thanks [tailwindcss](https://tailwindcss.com/) and [tailwindui](https://tailwindui.com/). Saved my life. Helped me build my first front-end project.

## How I deployed it

### Deploy higand and higancli rest-server to aws

I started an EC2 instance on AWS.

I use ansible to manage higan projects. If anyone is interested, I can open source it.

The ansible script performs some initialization work, creating a systemd service for higand and a systemd service for higancli rest-server.

Then there is an nginx that forwards the request to the REST service. Nginx configures some `cors` header and turns on https.

I use [cerbot](https://certbot.eff.org/) to configure let's encrypt. It's very simple.

### Deploy higan-ui to netlify

Just let netlify connect to my gitHub, and netlify will perform an automated deployment and provide free let's encrypt based encryption. I applied for my domain on godaddy. Then I switched to netlify's DNS resolution.

## Finally

Welcome to contribute.

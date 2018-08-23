---
title: SecureVote Docs

language_tabs: [] # must be one of https://git.io/vQNgJ
  # - shell
  # - ruby
  # - python
  # - javascript

toc_footers:
  - <a href="https://lib.docs.secure.vote">SV Lib docs</a>
  - <a href="https://api.docs.secure.vote">SV Light API docs</a>

includes: []
  # - errors

search: true
---

# Introduction

Welcome to the SecureVote docs. Here you'll find details on our smart contracts, links to other documentation, and more. (It's a work in progress atm.)



# Component Overviews / Operation


## BBFarm

This is the normal BBFarm. Exists on the same chain as the Index. Holds all ballots using std voting as of Aug 2018.
Ballots are created by the index only, though the ballot owner has limited control, e.g. deprecating the ballot, publishing
the secret key, and choosing a new owner.

## RemoteBBFarm and RemoteBBFarmProxy

This pair of BBFarms share the actions of a normal BBFarm.

RemoteBBFarmProxy holds the metadata about the ballot (specHash, start/end times, etc). It will revert or give you obvious garbage for things that are unsupported. (Obvious garbage being the number of votes from `getDetails`.) Additionally any ballot modification methods should be called here.

RemoteBBFarm holds the votes and is instantiated on a foreign network. It does not know about which ballots are valid and which are not,
and so when scraping votes later you must use the `getVoteAndTime` method, not `getVote`. The reason is you must validate the timestamp of votes
to ensure they were all cast in the allowed window. Essentially it is just a container for votes. `getDetails` works as expected here.

# Ethereum Networks

Networks used are:

* Mainnet (Ethereum Foundation)
* SecureVote PoA Network (Network ID 0xF0, [parity chain spec](https://github.com/secure-vote/sv-parity-setup/blob/master/sv-poa-spec.json))
* Classic
* Kovan
* Ropsten

## Stats

We maintain `eth-stats` instances for each group of nodes:

* https://stats.eth.secure.vote (mainnet)
* https://stats.poa.eth.secure.vote
* https://stats.classic.eth.secure.vote
* https://stats.kovan.eth.secure.vote
* https://stats.ropsten.eth.secure.vote

## Explorer (PoA)

We have an instance of Etherchain Light running at https://explorer.poa.eth.secure.vote for exploring that chain.

# Smart Contracts

## Libraries

These are deployed to the same address across mainnet, SV PoA, kovan, ropsten, and classic.

Deployed Date | Name | Address
--- | --- | ---
2018-08-10 | BBLibV7 | 0x1f8c387ebd02240A1BcB6b2864087464F719aDf6
2018-06-xx | StringLib | 0x63Dbc2DA4FBA06Ea2Bdbba0551744c7595Cc8e2A
2018-06-xx | Base32Lib | 0x45a337efe2adb2617a3a5272c6c84a89ef56afcf
2018-06-xx | MemArrApp | 0xedd7ac11f2437de048882d4859ed30d871cc4324
2018-06-xx | BBLib | 0x0484c599E228e13bEFB61129888e8bD2b63A9619

## Production

(list of production SCs go here)

Deployed Date | Network | Name of SC | Address | Notes
------------- | ---------- | ------- | ------- | ---
2018-08-22 | SV PoA | BBFarmRemote | 0xebccfb6af3e030ca73e5f00f2cc77ef2a60a1887 | .
2018-07-30 | Mainnet | BBFarmAux2 | 0x91f34190ffcd934115bb2bd04c29e89362989121 | aux contract to make some BBFarm calls nicer
2018-07-xx | Mainnet | TokenAbbreviationLookup | 0x216265865e46D4c6FE506877EfAAE7dd7Ae2faCE | .
2018-06-xx | Mainnet | EnsOwnerPx | 0xa00919a6c9e1c31be81d0203532bdb7724052b04 | index.tokenvote.eth owner px
2018-06-xx | Mainnet | CommunityAuctionSimple | 0x5A0E6Ff846C237E5E8f5AFd388B488292E1c8627 | .
2018-06-xx | Mainnet | BBFarm | 0xB105035C563Ed14C17f6BeaCe07F4659C823322a | .
2018-06-xx | Mainnet | SVPayments | 0xB9C0291cbbb67CF5368F4FAc5EaE9d8bB98f67bA | .
2018-06-xx | Mainnet | SVIndexBackend | 0x45250f268a3ef4adafc9275073d7fa126fb75101 | .
2018-06-xx | Mainnet | SVIndex | 0x04B710D1FC77C8e7002F539bB48feB560CB2892C | .
2018-03-06 | Mainnet | SVDelegationV0101 | 0x4dD28be042F85e287E9AaCe4147152bf1CD835e9 | deprecates SVDelegation contract
2018-02-28 | Mainnet | SVDelegation | 0xd78d4beabfd3054390d10aeb4258dc2d867f5e17 | deprecated as doesn't allow reverse lookup easily
2018-03-01 | Mainnet | SVLightIndex | 0xa8a8509A17a5872d01e489fC85B152eb2A0C092E | Early prototype of index, used for a few SWM ballots
2018-03-01 | Mainnet | SwarmVotingMVP | 0x1e6b7d459AF96E916548D27B0e72ce17ccb7dB74 | .
2018-03-01 | Mainnet | SwarmVotingMVP | 0x6B649662dA40F10361F008b481143029296a69D6 | Upgraded version, used for a few ballots
2017-10-29 | Mainnet | SwarmVotingMVP | 0x2Bb10945E9f0C9483022dc473aB4951BC2a77d0f | Initial MVP contract for Swarm

## Testnet (TN1)

Deployed Date | Network | Name of SC | Address
------------- | ---------- | ------- | -------
2018-08-10 | Ropsten | UnsafeEd25519SelfDelegation | 0x2cdb6b361ecc7a834ce8a3a78556e70c3e74660e
2018-08-10 | Ropsten | RemoteBBFarm | 0xc3d10af066bde2357c92bc4af25fb5f42e73f1a4
2018-08-10 | Kovan | RemoteBBFarmProxy | 0xd3141c94d3beddbe1d280822ecc633b7c6a32464
2018-07-xx | Kovan | BBFarmAux2 | 0x8d9d49f602e1e95b8dca42af1766963c3e4f7565
2018-06-xx | Kovan | SVIndex | 0xcad76eE606FB794dD1DA2c7E3C8663F648ba431d

# Ballot Box Farms

## Namespaces (Production)

Date | Namespace (bytes4) | BBFarmID | Network | Type | Address | Notes
---|---|---|---|---|---|---
2018-06-xx | 0x00000001 | 0 | Mainnet | BBFarm | 0xB105035C563Ed14C17f6BeaCe07F4659C823322a | .
2018-08-23 | 0xF0F00001 | 1 | SV PoA | BBFarmRemote | 0xebccfb6af3e030ca73e5f00f2cc77ef2a60a1887 | .
2018-08-24 | 0xF0F00001 | 1 | Mainnet | BBFarmRemoteProxy | .. | .

## Namespaces (Testnet - TN1)

Date | Namespace (bytes4) | BBFarmID | Network | Type | Address | Notes
---|---|---|---|---|---|---
2018-08-10 | 0x03030001 | 1 | Kovan | RemoteBBFarmProxy | 0xd3141c94d3beddbe1d280822ecc633b7c6a32464 | .
2018-08-10 | 0x03030001 | 1 | Ropsten | RemoteBBFarm | 0xc3d10af066bde2357c92bc4af25fb5f42e73f1a4 | .
2018-06-xx | 0x00000001 | 0 | Kovan | BBFarm | 0x8384AD2bd15A80c15ccE6B5830a9324442853899 | .


<!--
# Authentication

> To authorize, use this code:

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
```

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here"
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
```

> Make sure to replace `meowmeowmeow` with your API key.

Kittn uses API keys to allow access to the API. You can register a new Kittn API key at our [developer portal](http://example.com/developers).

Kittn expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: meowmeowmeow`

<aside class="notice">
You must replace <code>meowmeowmeow</code> with your personal API key.
</aside>

# Kittens

## Get All Kittens

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get()
```

```shell
curl "http://example.com/api/kittens"
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let kittens = api.kittens.get();
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "name": "Fluffums",
    "breed": "calico",
    "fluffiness": 6,
    "cuteness": 7
  },
  {
    "id": 2,
    "name": "Max",
    "breed": "unknown",
    "fluffiness": 5,
    "cuteness": 10
  }
]
```

This endpoint retrieves all kittens.

### HTTP Request

`GET http://example.com/api/kittens`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include kittens that have already been adopted.

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>

## Get a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get(2)
```

```shell
curl "http://example.com/api/kittens/2"
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.get(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Max",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint retrieves a specific kitten.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to retrieve

## Delete a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.delete(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.delete(2)
```

```shell
curl "http://example.com/api/kittens/2"
  -X DELETE
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.delete(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ":("
}
```

This endpoint deletes a specific kitten.

### HTTP Request

`DELETE http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to delete -->

---
title: SecureVote Docs

language_tabs: [] # must be one of https://git.io/vQNgJ
  # - shell
  # - ruby
  # - python
  # - javascript

toc_footers:
  # - <a href='#'>Sign Up for a Developer Key</a>
  # - <a href='https://github.com/lord/slate'>Documentation Powered by Slate</a>
  - <a href="https://lib.docs.secure.vote">SV Lib docs</a>
  - <a href="https://api.docs.secure.vote">SV Light API docs</a>

includes: []
  # - errors

search: true
---

# Introduction

Welcome to the SecureVote docs. Here you'll find details on our smart contracts, links to other documentation, and more. (It's a work in progress atm.)







# Smart Contracts

## Libraries

These are deployed to the same address across mainnet, kovan, ropsten, and classic.

Deployed Date | Name | Address
--- | --- | ---
2018-08-10 | BBLibV7 | 0x1f8c387ebd02240A1BcB6b2864087464F719aDf6
2018-06-xx | StringLib | 0x63Dbc2DA4FBA06Ea2Bdbba0551744c7595Cc8e2A
2018-06-xx | Base32Lib | 0x45a337efe2adb2617a3a5272c6c84a89ef56afcf
2018-06-xx | MemArrApp | 0xedd7ac11f2437de048882d4859ed30d871cc4324
2018-06-xx | BBLib | 0x0484c599E228e13bEFB61129888e8bD2b63A9619

## Production

(list of production SCs go here)

Deployed Date | Network | Name of SC | Address
------------- | ---------- | ------- | -------
2018-08-10 | Mainnet | td | todo

## Testnet (TN1)

Deployed Date | Network | Name of SC | Address
------------- | ---------- | ------- | -------
2018-08-10 | Ropsten | UnsafeEd25519SelfDelegation | 0x2cdb6b361ecc7a834ce8a3a78556e70c3e74660e
2018-08-10 | Ropsten | RemoteBBFarm | 0xc3d10af066bde2357c92bc4af25fb5f42e73f1a4
2018-08-10 | Kovan | RemoteBBFarmProxy | 0xd3141c94d3beddbe1d280822ecc633b7c6a32464
2018-06-xx | Kovan | SVIndex | 0xcad76eE606FB794dD1DA2c7E3C8663F648ba431d

# Ballot Box Farms

## Namespaces (Production)

Date | Namespace (bytes4) | BBFarmID | Network | Type | Address | Notes
---|---|---|---|---|---|---
2018-06-xx | 0x00000001 | 0 | Mainnet | BBFarm | 0xB105035C563Ed14C17f6BeaCe07F4659C823322a | .

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

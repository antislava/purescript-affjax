# purescript-affjax

[![Latest release](http://img.shields.io/github/release/slamdata/purescript-affjax.svg)](https://github.com/slamdata/purescript-affjax/releases)
[![Build status](https://travis-ci.org/slamdata/purescript-affjax.svg?branch=master)](https://travis-ci.org/slamdata/purescript-affjax)

A library taking advantage of [`purescript-aff`](https://github.com/slamdata/purescript-aff) to enable pain-free asynchronous AJAX requests and response handling.

# Getting Started

## Installation

```
bower install purescript-affjax
```

If you are intending to use the library in a Node.js setting rather than the browser, you will need an additional dependency from `npm`:

```
npm install xhr2
```

## Introduction

You can construct requests with the `request` function:

```purescript
module Main where

import Prelude

import Affjax as AX
import Affjax.ResponseFormat as ResponseFormat
import Data.Argonaut.Core as J
import Data.Either (Either(..))
import Data.HTTP.Method (Method(..))
import Effect.Aff (launchAff)
import Effect.Class (liftEffect)
import Effect.Console (log)

main = launchAff $ do
  res <- AX.request ResponseFormat.json (AX.defaultRequest { url = "/api", method = Left GET })
  liftEffect $ log $ "GET /api response: " <> J.stringify res.response
```

(`defaultRequest` is a record value that has all the required fields pre-set for convenient overriding when making a request.)

Or use of a number of helpers for common cases:

```purescript
import Affjax.RequestBody as RequestBody

main = launchAff $ do
  res1 <- AX.get ResponseFormat.json "/api"
  liftEffect $ log $ "GET /api response: " <> J.stringify res1.response

  res2 <- AX.post ResponseFormat.json "/api" (RequestBody.json (J.fromString "test"))
  liftEffect $ log $ "POST /api response: " <> J.stringify res2.response
```

See the module documentation for a full list of these helpers.

## Module documentation

Module documentation is [published on Pursuit](http://pursuit.purescript.org/packages/purescript-affjax).

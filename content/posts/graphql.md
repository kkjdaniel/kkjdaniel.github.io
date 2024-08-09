+++
title = 'Making the BGG API better with GraphQL & Go'
date = 2024-03-12T02:29:34Z
draft = false
tags = [ "Tutorial", "Go", "GraphQL" ]
categories = [ "Coding" ]
+++

It would be fair to say the BGG API ([BoardGameGeek](https://boardgamegeek.com/) for the uninitiated), is neither the most elegant nor easy to work with API out there. Featuring a peculiar mix of awkward XML, lacking documentation and awkward request limiting. However, what it does do is provide access to an unbeatable wealth of data on nearly every tabletop game imagineable.

The intention of this article is to provide some insight into how GraphQL can be a useuful tool for wrapping and even augmenting legacy APIs, without needing to modify the old API.

## Initialising Go

Before we can begin setting up GraphQL we first need to create a new Go module as follows.

```
mkdir bggQL
cd bggQL
go mod init bggQL
```

## Setting up GraphQL

To begin with we need to setup our GraphQL service with Go, in order to achieve this we will be using GQLGen. This involves adding the following to our `tools.go` file.

```go
//go:build tools
// +build tools

package tools

import (
	_ "github.com/99designs/gqlgen"
	_ "github.com/99designs/gqlgen/graphql/introspection"
)
```

Then we simply need to run the following command in order to install the modules we've referenced.

```
go mod tidy
```

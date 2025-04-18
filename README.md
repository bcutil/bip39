[![PkgGoDev](https://pkg.go.dev/badge/bcutil/bip39)](https://pkg.go.dev/github.com/bcutil/bip39)
[![Latest release](https://img.shields.io/github/v/tag/bcutil/bip39?label=release&sort=semver)](https://github.com/bcutil/bip39/releases)
[![MIT License](https://img.shields.io/github/license/bcutil/bip39.svg?maxAge=2592000&color=blue)](https://github.com/bcutil/bip39/blob/master/LICENSE)
[![Contributors](https://img.shields.io/github/contributors/bcutil/bip39.svg?color=blue)](https://github.com/bcutil/bip39/graphs/contributors)

[![Build check](https://github.com/bcutil/bip39/workflows/build-check/badge.svg?branch=master)](https://github.com/bcutil/bip39/actions?query=workflow%3Abuild-check+branch%3Amaster)
[![Go Report Card](https://goreportcard.com/badge/github.com/bcutil/bip39)](https://goreportcard.com/report/github.com/bcutil/bip39)
[![Coverage Status](https://coveralls.io/repos/github/bcutil/bip39/badge.svg?branch=master)](https://coveralls.io/github/bcutil/bip39?branch=master)

## Example

```go
package main

import (
  "fmt"
  "github.com/bcutil/bip39"
  "github.com/bcutil/bip32"
)

func main(){
  // Generate a mnemonic for memorization or user-friendly seeds
  entropy, _ := bip39.NewEntropy(256)
  mnemonic, _ := bip39.NewMnemonic(entropy)

  // Generate a Bip32 HD wallet for the mnemonic and a user supplied password
  seed := bip39.NewSeed(mnemonic, "Secret Passphrase")

  masterKey, _ := bip32.NewMasterKey(seed)
  publicKey := masterKey.PublicKey()

  // Display mnemonic and keys
  fmt.Println("Mnemonic: ", mnemonic)
  fmt.Println("Master private key: ", masterKey)
  fmt.Println("Master public key: ", publicKey)
}
```

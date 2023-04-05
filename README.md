# Cashu TS

⚠️ **Don't be reckless:** This project is in early development, it does however work with real sats! Always use amounts you don't mind loosing.

Cashu TS is a JavaScript library for [Cashu](https://github.com/cashubtc) wallets written in Typescript.

Wallet Features:

- [x] connect to mint (load keys)
- [x] request minting tokens
- [x] minting tokens
- [x] sending tokens (get encoded token for chosen value)
- [x] receiving tokens
- [x] melting tokens
- [x] check if tokens are spent
- [ ] ...

Implemented [NUTs](https://github.com/cashubtc/nuts/):

- [x] [NUT-00](https://github.com/cashubtc/nuts/blob/main/00.md)
- [x] [NUT-01](https://github.com/cashubtc/nuts/blob/main/01.md)
- [x] [NUT-02](https://github.com/cashubtc/nuts/blob/main/02.md)
- [x] [NUT-03](https://github.com/cashubtc/nuts/blob/main/03.md)
- [x] [NUT-04](https://github.com/cashubtc/nuts/blob/main/04.md)
- [x] [NUT-05](https://github.com/cashubtc/nuts/blob/main/05.md)
- [x] [NUT-06](https://github.com/cashubtc/nuts/blob/main/06.md)
- [x] [NUT-07](https://github.com/cashubtc/nuts/blob/main/07.md)
- [x] [NUT-08](https://github.com/cashubtc/nuts/blob/main/08.md)
- [x] [NUT-09](https://github.com/cashubtc/nuts/blob/main/09.md)

Supported token formats:

- [x] v1 read
- [x] v2 read (deprecated)
- [x] v3 read/write

## Usage

### Install

```shell
npm i @cashu/cashu-ts
```

### Import

```typescript
import { CashuMint, CashuWallet, getEncodedToken } from '@cashu/cashu-ts';

const mint = new CashuMint('{MINT_HOST}', '{/path/to/api/root/}', '{MINT_PORT}');
const keys = await mint.getKeys();
const wallet = new CashuWallet(keys, mint);

const { pr, hash } = await wallet.requestMint(200);

//pay this LN invoice
console.log({ pr }, { hash });

async function invoiceHasBeenPaid() {
	const proofs = await wallet.requestTokens(200, hash);
	//Encoded proofs can be spent at the mint
	const encoded = getEncodedToken(proofs);
	console.log(encoded);
}
```

## Contribute

Contributions are very welcome.

If you want to contribute, please open an Issue or a PR.

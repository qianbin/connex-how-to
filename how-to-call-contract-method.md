# How to call contract method?

Calling contract method means performing read-only call to contract method without state-mutating transaction, or to say dry-run, evaluate or explain. This is one of the most common operations when building Dapps. Fortunately, it's quite easy to do with **Connex**.

Let's try to play with the builtin contract *Energy*, call its public method *totalSupply* to query total supplied VTHO.

## Step 1

We know the address of *Energy* contract is *0x0000000000000000000000000000456E65726779*. So we can make an *AccountVisitor* named to *acc*

```javascript
const acc = connex.thor.account('0x0000000000000000000000000000456E65726779')
```


## Step 2

Look up *Energy* contract [ABI definition](https://github.com/vechain/b32/blob/master/ABIs/energy.json). We can either pick out needed piece

```javascript
const totalSupplyABI = {
        "constant": true,
        "inputs": [],
        "name": "totalSupply",
        "outputs": [
            {
                "name": "",
                "type": "uint256"
            }
        ],
        "payable": false,
        "stateMutability": "view",
        "type": "function"
}
```

or runtimely locate from ABI array

```javascript
const abis = [...] // assumed to be the full definition
const totalSupplyABI = abis.find(e => e.name === 'totalSupply')
```


## Step 3

Create the method object, and finally perform the call

```javascript
const totalSupplyMethod = acc.method(totalSupplyABI)
const result = await totalSupplyMethod.call()
```

If no error occurred, we'll get the *result* looks like 

```json
{ data:
   '0x000000000000000000000000000000000000000032c04cf852e8a48339152000',
  events: [],
  transfers: [],
  gasUsed: 494,
  reverted: false,
  vmError: '',
  decoded: { '0': '15706727729052696400000000000' } }
```

Where `result.decoded[0]` is the return value of method *totalSupply*. 

Note that if we want to display the result value in unit VTHO, it must be divided by *1e18* according to pre-defined decimal place. To avoid loss of precision, it is recommended to use *bignumber.js* for calculations.
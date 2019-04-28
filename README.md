hpb-web3j provides a convenient way to quickly build your own HPB wallet for Android developers.

### Features
•	Create Account

•	Import Account

•	Sign transactions
### Download

```
android {
  ...
  repositories {
    flatDir {
        dirs 'libs'   // aar contents
    }
  }
}

dependencies {
  compile(name: 'hpb-web3j-1.0.0', ext: 'aar')
}

```


### Usage
Below is the basic code,Please refer to the Demo for details.

#### Creat Account

```
Bip39WalletUtil walletUtils = new Bip39WalletUtil(context);
WalletBean  walletBean = walletUtils.generateBip39Wallet(walletName,password,prompt);
```

There are other ways of doing the same thing

```
walletUtils.generateBip39Wallet(walletName);
walletUtils.generateBip39Wallet(walletName, password);
```
#### Import Account
##### Import private key

```
Credentials credentials = Credentials.create(privateKey);
WalletFile walletFile= Wallet.createLight(password, credentials.getEcKeyPair());
```

##### Import mnemonic

```
Credentials credentials = Bip39WalletUtil.loadBip39Credentials("", mnemonic);
WalletFile walletFile= Wallet.createLight(password, credentials.getEcKeyPair());
```

##### Import kstore file

```
ObjectMapper objectMapper = ObjectMapperFactory.getObjectMapper();
WalletFile walletFile = objectMapper.readValue(keystore, WalletFile.class);
```
#### Sign transactions
##### Usual transactions

```
String signData = TransferUtils.signTransaction(BigInteger nonce, BigInteger gasPrice, BigInteger gasLimit, String to,BigInteger value, String data, byte chainId, String privateKey)
```
##### Token transactions

```
String signData = TransferUtils. tokenTransaction(BigInteger nonce,BigInteger gasPrice,BigInteger gasLimit,String privateKey, String contractAddress, String toAddress, BigDecimal amount)
```


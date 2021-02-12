- [Frends.Community.PgpEncryptFile](#Frends.Community.PgpEncryptFile)
   - [Documentation](#documentation)
      - [PgpEncryptFile](#pgpencryptfile)
		 - [Input](#input)
		 - [Result](#result)
   - [Building](#building)
   - [Installing](#installing)
   - [Contributing](#contributing)
   - [License](#license)
   - [Change log](#change-log)
       
# Frends.Community.PgpEncryptFile

This Task is deprecated. Use [Frends.Community.Pgp](https://github.com/CommunityHiQ/Frends.Community.Pgp) Tasks insted.

This repository contais FRENDS4 Community Task to encrypt files with PGP

## Documentation

### PgpEncryptFile

Encrypt file with PGP.

#### Input
| Property            | Type   | Description |Example|
|---------------------|--------|-------------|-------|
| InputFile           | string | Path to file to decrypt.|`C:\temp\message.txt`|
| OutputFile          | string | Path to file that will be created. | `C:\temp\encryptedFile.pgp`|
| PublicKeyFile       | string | Path to recipients public key. | `C:\temp\publicKey.asc`|
| UseArmor            | bool   | Use ascii armor or not. |`true`|
| UseIntegrityCheck   | bool   | Check integrity of output file or not. |`true`|
| UseCompression      | bool   | Should file be compressed prior to encryption?|`true`|
| CompressionType     | enum   | Type of compression to use when encrypting.|`Zip`|
| EncryptionAlgorithm | enum   | Algorithm to use when encrypting.|`Cast5`|
| SignWithPrivateKey  | bool   | True if you want to sign the file with private key. In this case the file is first signed and then encrypted.|`false`|

#### Signing settings
Visible only if the file is to be signed

| Property               | Type   | Description |Example|
|------------------------|--------|-------------|-------|
| PrivateKeyFile         | string | Path to private key file to be used with signing.|`C:\temp\privateKeyFile.gpg`|
| PrivateKeyPassword     | string | Password to the private key.|`***`|
| SignatureHashAlgorithm | enum   | Hash algorithm to use with signature.|`Sha1`|

#### Result
| Property  | Type  | Description |Example|
|-----------|-------|-------------|-------|
| FilePath | string  | Path to file that contains encrypted file. Note: this is same path that was given as input parameter OutputFile. Copying that path to result will enable easy references in Frends, such as #result[PgpEncryptFile].FilePath | `C:\temp\encryptedFile.pgp`

## Building

Clone a copy of the repo

```sh
git clone https://github.com/CommunityHiQ/Frends.Community.PgpEncryptFile.git
```
Restore dependencies

```sh
nuget restore Frends.Community.PgpEncryptFile
```
Rebuild the project with Release configuration

Run Tests with nunit3. Tests can be found under

Frends.Community.PgpEncryptFileTests\bin\Release\Frends.Community.PgpEncryptFile.Tests.dll

Create a nuget package
```sh
nuget pack nuspec/Frends.Community.PgpEncryptFile.nuspec -properties Configuration=Release
```

## Installing
Create a nuget package from the solution and import it with Frends UI

## Contributing
When contributing to this repository, please first discuss the change you wish to make via issue, email, or any other method with the owners of this repository before making a change.

1. Fork the repo on GitHub
2. Clone the project to your own machine
3. Commit changes to your own branch
4. Push your work back up to your fork
5. Submit a Pull request so that we can review your changes

NOTE: Be sure to merge the latest from "upstream" before making a pull request!

## License
This project is licensed under the MIT License - see the LICENSE file for details

## Change Log

| Version | Changes |
| ------- | ------- |
| 1.0.0   | Initial version |
| 1.1.0   | New features:<br/>- Option to sign file<br/>- Compression and compression type is configurable<br/>- Encryption algorithm is configurable<br/>- Signature hash is configurable|

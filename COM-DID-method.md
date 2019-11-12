# Commercio.network DID Method Specification

## Abstract – what is commercio.network

Commercio.network is a cosmos based sovereign blockchain network, built on the base of cosmos sdk and tendermint state machine replication engine, adopting Proof of Stake as a consensus algorithm.

Commercio.network, aims to be known as "The Documents Blockchain" and is to become "the easiest way for companies to manage their business documents using the blockchain technology".

Commercio.newtork ultimate goal is not just to share documents, but to create a network of trusted organizations, on the base of a web of trust, build on the Decentralized Identifier and Verifiable Credentials standard pillars.

In this document we specify the DID Method for Commercio.network, in comformance to the requirements specified in the DID specification[4] currently published by the W3C Credentials Community Group. For more information about DIDs and DID method specifications, please see DID Primer[6] and DID Specification[4].

## Commercio.network DID Method

### Commercio DID scheme

Commercio.network DID scheme consists of the following parts:

 1. url scheme identifier: ```did```
 2. identifier for the DID method: ```com```
 3. Method-specific identifier: ```<commercio.network  address>```, which conforms to the [cosmos.network address scheme](https://cosmos.network/docs/spec/addresses/bech32.html)

An example of commercio.network DID is the following:
```did:com:14zk9u8894eg7fhgw0dsesnqzmlrx85ga9rvnjc```

### DID Document

Commerico DID Document is compliant with [4].

Example of commercio.network DID Document
```json
{
	"@context": "https://www.w3.org/2019/did/v1",
	"id": "did:com:14zk9u8894eg7fhgw0dsesnqzmlrx85ga9rvnjc",
	"publicKey": [{
		"id": "did:com:14zk9u8894eg7fhgw0dsesnqzmlrx85ga9rvnjc#keys-1",
		"type": "RsaVerificationKey2018",
		"controller": "did:com:14zk9u8894eg7fhgw0dsesnqzmlrx85ga9rvnjc ",
		"publicKeyPem": "-----BEGIN PUBLIC KEY----MIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQDMr3V+Auyc+zvt2qX+jpwk3wM+m2DbfLjimByzQDIfrzSHMTQ8erL0kg69YsXHYXVX9mIZKRzk6VNwOBOQJSsIDf2jGbuEgI8EB4c3q1XykakCTvO3Ku3PJgZ9PO4qRw7QVvTkCbc91rT93/pD3/Ar8wqd4pNXtgbfbwJGviZ6kQIDAQAB-----END PUBLIC KEY-----r"
		},{
		"id": "did:com:14zk9u8894eg7fhgw0dsesnqzmlrx85ga9rvnjc#keys-2",
		"type": "Secp256k1VerificationKey2018",
		"controller": "did:com:14zk9u8894eg7fhgw0dsesnqzmlrx85ga9rvnjc ",
		"publicKeyHex": "02b97c30de767f084ce3080168ee293053ba33b235d7116a3263d29f1450936b71"
	}],
	"authentication": "did:com:14zk9u8894eg7fhgw0dsesnqzmlrx85ga9rvnjc#keys-1",
	"proof": {
		"type": "LinkedDataSignature2015",
		"created": "2016-02-08T16:02:20Z",
		"creator": "did:com:14zk9u8894eg7fhgw0dsesnqzmlrx85ga9rvnjc#keys-1",
		"signatureValue": "QNB13Y7Q9...1tzjn4w=="
	}
}
```
Example of commercio.network DID Document including service endpoint:

```json
{
  "@context": "https://www.w3.org/2019/did/v1",
  "id": "did:com:14zk9u8894eg7fhgw0dsesnqzmlrx85ga9rvnjc",
  "publicKey": [
    {
      "id": "did:com:14zk9u8894eg7fhgw0dsesnqzmlrx85ga9rvnjc#keys-1",
      "type": "RsaVerificationKey2018",
      "controller": "did:com:14zk9u8894eg7fhgw0dsesnqzmlrx85ga9rvnjc ",
      "publicKeyPem": "-----BEGIN PUBLIC KEY----MIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQDMr3V+Auyc+zvt2qX+jpwk3wM+m2DbfLjimByzQDIfrzSHMTQ8erL0kg69YsXHYXVX9mIZKRzk6VNwOBOQJSsIDf2jGbuEgI8EB4c3q1XykakCTvO3Ku3PJgZ9PO4qRw7QVvTkCbc91rT93/pD3/Ar8wqd4pNXtgbfbwJGviZ6kQIDAQAB-----END PUBLIC KEY-----r"
    },
    {
      "id": "did:com:14zk9u8894eg7fhgw0dsesnqzmlrx85ga9rvnjc#keys-2",
      "type": "Secp256k1VerificationKey2018",
      "controller": "did:com:14zk9u8894eg7fhgw0dsesnqzmlrx85ga9rvnjc ",
      "publicKeyHex": "02b97c30de767f084ce3080168ee293053ba33b235d7116a3263d29f1450936b71"
    }
  ],
  "authentication": "did:com:14zk9u8894eg7fhgw0dsesnqzmlrx85ga9rvnjc#keys-1",
  "service": [
    {
      "id": "did:com:14zk9u8894eg7fhgw0dsesnqzmlrx85ga9rvnjc#openid",
      "type": "OpenIdConnectVersion1.0Service",
      "serviceEndpoint": "https://openid.commercio.com/"
    },
    {
      "id": "did:com:14zk9u8894eg7fhgw0dsesnqzmlrx85ga9rvnjc#messageing",
      "type": "MessaginService",
      "serviceEndpoint": "http://chat.commercio.com/did:com:14zk9u8894eg7fhgw0dsesnqzmlrx85ga9rvnjc"
    }
  ],
  "proof": {
    "type": "LinkedDataSignature2015",
    "created": "2016-02-08T16:02:20Z",
    "creator": "did:com:14zk9u8894eg7fhgw0dsesnqzmlrx85ga9rvnjc#keys-1",
    "signatureValue": "QNB13Y7Q9...1tzjn4w=="
  }
}
```

### DID Operations (CRUD)

#### Create
In Commercio.network, a DID Document maybe associated to DID via the [setIdentity](https://docs.commercio.network/x/id/tx/associate-a-did-document.html) specific transacion
The transaction is validated when the transaction signature is verified to be coherent with the ID key in the DID document.
The DID document is saved on-chain as every successive modification to the did.
only the ID owner may set the DID Document.
only the ID owner may update the DID document.

#### Read/Verify
DID resolution is carried out by querying Commercio.network full node via restful API resource /identities, as specified [here](https://docs.commercio.network/x/id/query/read-identity.html)

#### Update
DID document may be updated by its ID owner, via the [setIdentity](https://docs.commercio.network/x/id/tx/associate-a-did-document.html) transaction.
The transaction is validated when the transaction signature is verified to be coherent with the ID key in the DID document.
The DID document is saved on-chain as every successive modification to the did.

#### Deactivate
Deactivation isn't currently supported.


### Privacy Consideration

Entities in commercio.network have the freedom of choice to act as public verifiable entities or pseudonym entities.
DID and DID Document are always stored on-chain.
DID resolution is provided by commercio.network full node APIs.


### Security Consideration

DID documents are stored and explicitly signed by the account private key it can be authenticated by relying parties. Any relying parties can resolve a DID without the need to trust the resolver.

Commercio.network support a eIDAS inspired trust framework and it is open to include other Self Sovereign Identity and eIDAS compliant  entities.

For instance a sender could use its own account private key to sign a message, whch inlude an external did (for instance uport did method) and its relatively encrypted content.
through DID method registry and  projects like universal resolver, the recipient would be able to validate the transaction using the did:com scheme, and validate the content using the did:ethr cheme after having resolved the external did.

The same approach may be used when a transaction would mix Commercio.internal identityes with eIDAS signature credentials, thanks to the availability of EUTSL, which can be referenced in the blockchain genesys block and updated via trusted oracles.

## Commercio.network Identity framework

### Public Pseudonym DID and DDO

### Verifiable Credentials schema

We distinguish between two possible DID subjects:

 1. Person
 2. Company

#### Person
credential schema:

 - Context
 - Id
 - Issuer:
	 - Id
	 - type
 - issuanceDate
 - Credential Subject:
	 - Name
	 - surname
	 - tin (tax payer identification number)
	 - Date of birth
	 - Email
	 - mobile number
	 - address
	 - city
	 - zipcode
	 - state
	 - country
 - credential status:
	 - id
	 - type
 - proof (embedded):
	 - type
	 - created
	 - proofPurpose (always “assertionMethod”)
	 - verification method
	 - jws (json web signature)

example:
```json
{
	"@context": "https://www.w3.org/2019/did/v1",
	"id": "http://exampletsp.com/credentials/14zk",
	"type": ["VerifiableCredential"],
	"issuer": {
		"id": "did:com:76e12ec712ebc6f1c221ebfeb1f",
		"name": "Example TSP"
	},
	"issuanceDate": "2019-03-04T17:34:383",
	"credentialSubject": {
		"id": " did:com:14zk9u8894eg7fhgw0dsesnqzmlrx85ga9rvnjc",
		"name": "Egidio",
		"surname": "Casati",
		"tin": "ccceee00c00e000c",
		"dateofbirth": "01011970",
		"email" : "egidio.casati@hotmail.com",
		"mobilenumber": "+390203020302",
		"address": "via Mario rossi 7",
		"zipcode": "20100",
		"city": "Milano",
		"state": "MI",
		"country": "IT"
	},
	"credentialStatus": {
		"id": "https://example.edu/status/24",
		"type": "CredentialStatusList2017"
	},
	"proof": {
		"type": "RsaSignature2018",
		"created": "2018-06-18T21:19:10Z",
		"proofPurpose": "assertionMethod",
		"verificationMethod": " http://exampletsp.com/tsp/keys/1",
		"jws": "eyJhbGciOiJQUzI1NiIsImI2NCI6ZmFsc2UsImNyaXQiOlsiYjY0Il19..DJBMvvFAIC00nSGB6Tn0XKbbF9XrsaJZREWvR2aONYTQQxnyXirtXnlewJMBBn2h9hfcGZrvnC1b6PgWmukzFJ1IiH1dWgnDIS81BH-IxXnPkbuYDeySorc4QU9MJxdVkY5EL4HYbcIfwKj6X4LBQ2_ZHZIu1jdqLcRZqHcsDF5KKylKc1THn5VRWy5WhYg_gBnyWny8E6Qkrze53MR7OuAmmNJ1m1nN8SxDrG6a08L78J0-Fbas5OjAQz3c17GY8mVuDPOBIOVjMEghBlgl3nOi1ysxbRGhHLEK4s0KKbeRogZdgt1DkQxDFxxn41QWDw_mmMCjs9qxg0zcZzqEJw"
	}
}
```
Note that the type tag could be used to add a specific commercio.network credential schema, for instance “personIdentityCredential”.

#### Company

 - Context
 - Id
 - Issuer:
	 - Id
	 - type
 - issuanceDate
 - Credential Subject
	 - Name
	 - Vat number
	 - Website
	 - Email
	 - mobile number
	 - address
	 - city
	 - zipcode
	 - state
	 - country
 - credential status:
	 - id
	 - type
 - proof (embedded):
	 - type
	 - created
	 - proofPurpose (always “assertionMethod”)
	 - verification method
	 - jws (json web signature)

example:

```json
{
	"@context": "https://www.w3.org/2019/did/v1",
	"id": "http://exampletsp.com/credentials/eedfk",
	"type": ["VerifiableCredential"],
	"issuer": {
		"id": "did:com:76e12ec712ebc6f1c221ebfeb1f",
		"name": "Example TSP"
	},
	"issuanceDate": "2019-03-04T17:34:383",
	"credentialSubject": {
		"id": " did:com:14zk9u8894eg7fhgw0dsesnqzmlrx85ga9rvnjc",
		"name": "cani&stracci Oil",
		"tin": "10201020102",
		"website": "https://caniestraccioil.com/",
		"email": "info@ caniestraccioil.com",
		"mobilenumber": "+390203020302",
		"address": "via Mario rossi 7",
		"zipcode": "20100",
		"city": "Milano",
		"state": "MI",
		"country": "IT"
	},
	"credentialStatus": {
		"id": "https://example.edu/status/234",
		"type": "CredentialStatusList2017"
	},
	"proof": {
		"type": "RsaSignature2018",
		"created": "2018-06-18T21:19:10Z",
		"proofPurpose": "assertionMethod",
		"verificationMethod": " http://exampletsp.com/tsp/keys/1",
		"jws": "eyJhbGciOiJQUzI1NiIsImI2NCI6ZmFsc2UsImNyaXQiOlsiYjY0Il19..DJBMvvFAIC00nSGB6Tn0XKbbF9XrsaJZREWvR2aONYTQQxnyXirtXnlewJMBBn2h9hfcGZrvnC1b6PgWmukzFJ1IiH1dWgnDIS81BHIxXnPkbuYDeySorc4QU9MJxdVkY5EL4HYbcIfwKj6X4LBQ2_ZHZIu1jdqLcRZqHcsDF5KKylKc1THn5VRWy5WhYg_gBnyWny8E6Qkrze53MR7OuAmmNJ1m1nN8SxDrG6a08L78J0Fbas5OjAQz3c17GY8mVuDPOBIOVjMEghBlgl3nOi1ysxbRGhHLEK4s0KKbeRogZdgt1DkQxDFxxn41QWDw_mmMCjs9qxg0zcZzqEJw"
	}
}
```

## References
[1]. COMMERCIO.NETWORK project portal, https://commercio.network/

[2]. COMMERCIO.NETWORK developers portal, https://docs.commercio.network/

[3]. COMMERCIO.NETWORK project github, https://github.com/commercionetwork

[4]. W3C Decentralized Identifiers (DIDs) v1.0, https://w3c-ccg.github.io/did-spec

[5]. W3C Verifiable Credential Data Model (VC) v1.0, https://www.w3.org/TR/vc-data-model/

[6]. A Primer for Decentralized Identifiers, https://w3c-ccg.github.io/did-primer/


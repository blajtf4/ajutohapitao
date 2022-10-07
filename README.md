# Switchboard VRF Flip

Utilize Switchboard's verifiable randomness to simulate a heads or tails coin toss.

## Setup

```
git clone https://github.com/switchboard-xyz/vrf-flip.git && cd vrf-flip
yarn install
yarn link
```

Setup program keypairs and client for your environment

```
yarn client:gen
```

Optionally, deploy to localnet

```
anchor build && anchor deploy
```

### Optional, Setup a Localnet Switchboard Environment

Run the following command to create a localnet switchboard environment

```
sbv2 localnet:env --keypair ../payer-keypair.json
```

This command will output:

- **start-local-validator.sh**: starts a local Solana validator with the Switchboard program, IDL, and our devnet environment pre-loaded
- **start-oracle.sh**: start a Switchboard oracle and start heartbeating on the localnet queue
- **docker-compose.yml**: docker file with the Switchboard oracle environment
- **switchboard.env**: contains your Switchboard accounts

In three separate shells, run the following commands in this order:

- `./.switchboard/start-local-validator.sh`
- `./.switchboard/start-oracle.sh`
- `anchor test --skip-local-validator`

The anchor test are configured to first fetch the account info for the Switchboard DAO controlled devnet permissionless queue. If the account info is not found, it assumes a localnet connection and looks for the `switchboard.env` with your Switchboard environment specific public keys. If a`.switchboard` directory or `switchboard.env` file is not found in the root project directory, it will look 2 levels higher until giving up.

## CLI

**_NOTE:_** If using localnet, make sure to pass `-c localnet` to the commands below.

Create a keypair for the house authority

```
 solana-keygen new --no-bip39-passphrase --outfile house-authority-keypair.json
```

Create the House account

```
sbv2-vrf-flip init house-authority-keypair.json F8ce7MsckeZAbAGmxjJNetxYXQa9mKr9nnrC3qKubyYy
# sbv2-vrf-flip init KEYPAIR QUEUEKEY
```

**_NOTE:_** The House must be initialized with a queue that has `unpermissioned_vrf_enabled` enabled.

Create a keypair for the user

```
 solana-keygen new --no-bip39-passphrase --outfile user-keypair.json
```

Create the User account

```
sbv2-vrf-flip create user-keypair.json
```

Request some FLIP tokens

```
sbv2-vrf-flip airdrop user-keypair.json
```

PLAY!

```
sbv2-vrf-flip play user-keypair.json --gameType coin-flip --guess 2
```

where,

- `gameType` can be `coin-flip`, `roll-dice`, `roll-20-sided-dice`.
- `guess` can be 1 through 2 for a `coin-flip`, 1 through 6 for `dice-roll`, and 1 through 20 for a `roll-20-sided-dice`
- `betAmount` is the number of tokens to wager

## Speed Run

```
solana-keygen new --no-bip39-passphrase --outfile house-authority-keypair.json
sbv2-vrf-flip init house-authority-keypair.json F8ce7MsckeZAbAGmxjJNetxYXQa9mKr9nnrC3qKubyYy
solana-keygen new --no-bip39-passphrase --outfile user-keypair.json
sbv2-vrf-flip create user-keypair.json
sbv2-vrf-flip airdrop user-keypair.json
sbv2-vrf-flip play user-keypair.json --gameType coin-flip --guess 2
```
------------------------------------------------------------
SVE KAJ SAM RADIO:
cd projects
git clone https://github.com/switchboard-xyz/vrf-flip.git
cd vrf-flip
yarn install(brda warninga)
yarn link(nakon yarn installa jako ljepo izgleda xD)

anchor build
solana-keygen pubkey target/deploy/switchboard_vrf_flip-keypair.json
:DD4D97uKgAWZyY3PbAniHMGJyX6nrCBoL5CkJjxnnq48(s ovim updateao anchor toml i lib.rs)
svb2 anchor test
svb2: command not found
npm install -g @switchboard-xyz/switchboardv2-cli(krenulo jebavat, zab sam da nemam npm jer sam
 snapshot uzeo kad sam proslo bacio u vjetar)

u rootu iz terminala vulgaris:
curl https://raw.githubusercontent.com/creationix/nvm/master/install.sh | bash
nvm install 16
nvm use 16
npm install -g @switchboard-xyz/switchboardv2-cli
sbv2 localnet env --keypair ~/.config/solana/id.json --outputDir .switchboard
:
OracleQueue     BWL9CkbX2BVdNT8bJsAs3cMSQbCUNrMAcsvtBbGG4ngx
OracleBuffer    C3UytH4JEtCbcvrG2Z9ozsR5VvVP1AqAMqsi1inr83Zo
CrankAccount    2YrTAuT6Sm1b1G2QR175JDReLfDwA19d6Wt19gwV9tv3
CrankBuffer     BXoQukDdw6L53yWSXmRJktUhcSHuA4YciaHVspgPx4hk
Oracle-1        Do7zfmEhj31wLzXS3Bri5KsTNeZMTrhfraJtsXL6QUd4
Permission-1    6SsW8nseKoo68DyVjwxPibcGCDBv5YghgA7UhJ7RCRiG
"payerKeypairPath": "/home/youngwarchief/.config/solana/id.json"(to iz maloprije generiranog switchboard.
jsona zakeljio u anchor toml: wallet = "/home/youngwarchief/.config/solana/id.json") 

switchboard.anchor.tomlu, switchboard json i envu sam promjenio program ID iz zadanog u 
onaj generiraran ranije: DD4D97uKgAWZyY3PbAniHMGJyX6nrCBoL5CkJjxnnq48(to je valjda ok?)


solana-keygen new --no-bip39-passphrase --outfile house-authority-keypair.json
:8exUBK7BwHjGpCZGte9pd2nJG9DiXnvqEPRgPMg77KHR
sbv2-vrf-flip init house-authority-keypair.json F8ce7MsckeZAbAGmxjJNetxYXQa9mKr9nnrC3qKubyYy
/usr/bin/env: ‘ts-node-esm’: No such file or directory
!!!tu zapinje
i po pitanju ovog nisam nista napravio:
NOTE: The House must be initialized with a queue that has unpermissioned_vrf_enabled enabled.

runo sam i : yarn client:gen
al mislim da je samo redundatno
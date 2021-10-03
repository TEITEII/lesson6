# Substrate Lesson6 Homework
## Build
cargo build --release
## Run
./target/release/node-template --dev
## Multi-Node Local Testnet
### purge chain (only required for new/modified dev chain spec)
./target/release/node-template purge-chain --base-path /tmp/node01 --chain local -y

### start node01
./target/release/node-template \
  --base-path /tmp/node01 \
  --chain ./customSpecRaw.json \
  --port 30333 \
  --ws-port 9945 \
  --rpc-port 9933 \
  --telemetry-url 'wss://telemetry.polkadot.io/submit/ 0' \
  --validator \
  --rpc-methods Unsafe \
  --name MyNode01
  ## Subsequent Participants Join
  ### purge chain (only required for new/modified dev chain spec)
  ./target/release/node-template purge-chain --base-path /tmp/node02 --chain local -y

  ### start node02
  ./target/release/node-template \
  --base-path /tmp/node02 \
  --chain ./customSpecRaw.json \
  --port 30334 \
  --ws-port 9946 \
  --rpc-port 9934 \
  --telemetry-url 'wss://telemetry.polkadot.io/submit/ 0' \
  --validator \
  --rpc-methods Unsafe \
  --name MyNode02 \
  --bootnodes /ip4/127.0.0.1/tcp/30333/p2p/12D3KooWAvdwXzjmRpkHpz8PzUTaX1o23SdpgAWVyTGMSQ68QXK6
  ### you MUST fill the correct info in the line above:
  ### --bootnodes /ip4/<IP Address>/tcp/<p2p Port>/p2p/<Peer ID>
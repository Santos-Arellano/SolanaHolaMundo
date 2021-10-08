## Dependencias

Tienen que tener instaladado [NodeJS](https://nodejs.org/es/), les recomiendo instalarlo vía [NVM](https://github.com/nvm-sh/nvm#installing-and-updating) si trabajan en Linux. Tambien [Yarn](https://classic.yarnpkg.com/lang/en/docs/install/#debian-stable) que les recomiendo instalar via NPM. Y finalmente [Rust](https://www.rust-lang.org/tools/install) y [Solana CLI](https://docs.solana.com/cli/install-solana-cli-tools).

```bash
# NodeJS
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.0/install.sh | bash
# ahora reinicia tus variables de entorno
nvm install 14
nvm alias default 14

# NodeJS
npm install --global yarn
# ahora reinicia tus variables de entorno

# Rust
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
# ahora reinicia tus variables de entorno

# Solana CLI
sh -c "$(curl -sSfL https://release.solana.com/v1.8.0/install)"
# ahora reinicia tus variables de entorno
```

## 1. Descargamos el proyecto de ejemplo

```bash
git clone https://github.com/FilosofiaCodigo/SolanaHolaMundo
cd SolanaHolaMundo
```

## 2. Nos preparamos para lanzar

Nos conectamos al devnet y conseguimos fondos desde el faucet.

```bash
solana config set --url https://api.devnet.solana.com
solana-keygen new --force
solana airdrop 5 
```

## 3. Lanzamos

```bash
cargo build-bpf --bpf-out-dir=dist/program
solana program deploy dist/program/helloworld.so
```

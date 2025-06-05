# Blueshift Anchor Vault

A simple Solana program built with Anchor framework that allows users to create personal vaults for depositing and withdrawing SOL.

## Overview

This program creates individual vaults for users using Program Derived Accounts (PDAs). Each user can deposit SOL into their vault and withdraw the full balance when needed.

## Features

- **Deposit**: Users can deposit SOL into their personal vault
- **Withdraw**: Users can withdraw their entire vault balance
- **PDA-based Vaults**: Each vault is uniquely derived from the user's public key
- **Safety Checks**: Prevents double initialization and ensures minimum balance requirements

## Program Functions

### `deposit(amount: u64)`
- Deposits the specified amount of SOL into the user's vault
- Requires the vault to be empty (prevents re-initialization)
- Enforces minimum balance requirements

### `withdraw()`
- Withdraws the entire balance from the user's vault
- Uses PDA signing to authorize the transfer

## Account Structure

The [`VaultAction`](programs/blueshift_anchor_vault/src/lib.rs) struct defines the required accounts:
- `signer`: The user's wallet (mutable)
- `vault`: PDA-derived vault account (mutable)
- `system_program`: Solana system program

## Development

### Prerequisites
- Rust
- Solana CLI
- Anchor CLI
- Node.js/Yarn

### Build
```bash
anchor build
# Vault Guardian Audit
- [What's Vault Guardian](#whats-vault-guardian)
- [User flow](#user-flow)
- [The DAO](#the-dao)
- [Summary](#summary)

# Audit Report 

[Audit-Report-HERE](audit-data/report.pdf)

## What's Vault Guardian

This protocol allows users to deposit certain ERC20s into an [ERC4626 vault](https://eips.ethereum.org/EIPS/eip-4626) managed by a `vaultGuardian`. The goal of a `vaultGuardian` is to manage the vault in a way that maximizes the value of the vault for the users who have despoited money into the vault.

You can think of a `vaultGuardian` as a fund manager.

To prevent a vault guardian from running off with the funds, the vault guardians are only allowed to deposit and withdraw the ERC20s into specific protocols. 

- [Aave v3](https://aave.com/) 
- [Uniswap v2](https://uniswap.org/) 
- None (just hold the funds) 

These 2 protocols (plus "none" makes 3) are known as the "investable universe".

The guardian can move funds in and out of these protocols as much as they like, but they cannot move funds to any other address.

The goal of a vault guardian, is to move funds in and out of these protocols to gain the most yield. Vault guardians charge a performance fee, the better the guardians do, the larger fee they will earn. 

Anyone can become a Vault Guardian by depositing a certain amount of the ERC20 into the vault. This is called the `guardian stake`. If a guardian wishes to stop being a guardian, they give out all user deposits and withdraw their guardian stake.

Users can then move their funds between vault managers as they see fit. 

The protocol is upgradeable so that if any of the platforms in the investable universe change, or we want to add more, we can do so.


## User flow

1. User deposits an ERC20 into a guardian's vault
2. The guardian automatically move the funds based on their strategy 
3. The guardian can update the settings of their strategy at any time and move the funds
4. To leave the pool, a user just calls `redeem` or `withdraw`

## The DAO

Guardians can earn DAO tokens by becoming guardians. The DAO is responsible for:
- Updating pricing parameters
- Getting a cut of all performance of all guardians

## Summary

Users can stake some ERC20s to become a vault guardian. Other users can allocate them funds in order to maximize yield. The guardians can move the funds between Uniswap, Aave, or just hold the funds. The guardians are incentivized to maximize yield, as they earn a performance fee.


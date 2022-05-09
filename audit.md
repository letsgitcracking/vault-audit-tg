- Reentrancy Attack on withdraw function - Use CEI pattern (Check, Effects and Interaction) to remove the exploit. This is because .call method has no gas limits.

- Reentrancy Attack on earn function - again this uses the .call method use reentrancy guard

- Keepers is not set in constructor, and there is currently no way to add additional keepers so earn function cannot be called

- No way to extract/withdraw funds if sent by accident

- Earn function assume only profit will be made, doesn't account for loss as this is a using uint

- Earning is averaged out and not given in proportion to investment - number_of_investors can be exploited by adding multiple small deposits which will enable attacker to get their earnings averaged out to their advantage

- Contract is initialised but the initial funds by contract creator is not added to the number of investors or investors array. Remove requirement for funds being non-zero or add parameters for details of investors who've given funds before contract deployment

- Floating pragma - you need to lock the pragma version
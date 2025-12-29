# Stacks Voting

Decentralized on-chain voting for DAOs and communities on Stacks blockchain.

## Features

- **Proposal Creation**: Create governance proposals with custom duration
- **Weighted Voting**: Support token-weighted voting
- **Vote Tracking**: Full transparency on who voted and when
- **Voter Stats**: Track participation and voting history
- **Execution**: Mark proposals as executed after voting ends

## Smart Contract Functions

### Proposals
```clarity
(create-proposal (title) (description) (duration))
(execute-proposal (proposal-id))
```

### Voting
```clarity
(vote (proposal-id) (option-id) (weight))
```

### Read-Only
```clarity
(get-proposal (proposal-id))
(get-vote-option (proposal-id) (option-id))
(get-vote (proposal-id) (voter))
(has-voted (proposal-id) (voter))
(is-voting-active (proposal-id))
(get-winning-option (proposal-id))
(get-voter-stats (voter))
```

## Usage

```clarity
;; Create a proposal (voting for ~7 days)
(contract-call? .voting create-proposal 
  u"Increase Treasury Allocation"
  u"Proposal to increase project treasury by 10%"
  u10080)

;; Vote Yes (option 0) with weight 100
(contract-call? .voting vote u0 u0 u100)

;; Execute after voting ends
(contract-call? .voting execute-proposal u0)
```

## License

MIT


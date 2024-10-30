# Commodities Trading Smart Contract

## About
A robust Clarity smart contract for managing commodities trading on the Stacks blockchain. This contract enables secure trading of commodities with features including escrow management, position tracking, and price oracle integration.

## Features
- Secure escrow system for fund management
- Real-time price oracle integration
- Position tracking and management
- Multi-commodity support
- Role-based access control
- Efficient trade execution
- Automated settlement process

## Contract Structure

### Core Components

1. **Administrator Functions**
   - Contract initialization
   - Price oracle management
   - Market status control
   - Commodity registration

2. **Trading Functions**
   - Execute trades
   - Close positions
   - View position details

3. **Escrow Management**
   - Deposit funds
   - Withdraw funds
   - Check balances

### Data Maps

1. **Available Commodities Inventory**
   ```clarity
   {
       commodity-identifier: uint,
       available-quantity: uint,
       current-market-price: uint,
       commodity-owner: principal
   }
   ```

2. **Active Trading Positions**
   ```clarity
   {
       trader-address: principal,
       trade-position-id: uint,
       commodity-identifier: uint,
       traded-quantity: uint,
       position-entry-price: uint,
       position-creation-timestamp: uint
   }
   ```

3. **Trader Escrow Accounts**
   ```clarity
   {
       trader-address: principal,
       escrow-balance: uint
   }
   ```

## Getting Started

### Prerequisites
- Stacks blockchain environment
- Clarity CLI tools
- STX tokens for deployment and trading

## Usage Guide

### For Traders

1. **Deposit Funds**
   ```clarity
   (deposit-funds-to-escrow deposit-amount)
   ```

2. **Execute Trade**
   ```clarity
   (execute-trade commodity-identifier trade-quantity trade-position-id)
   ```

3. **Close Position**
   ```clarity
   (close-trading-position trade-position-id)
   ```

4. **Withdraw Funds**
   ```clarity
   (withdraw-funds-from-escrow withdrawal-amount)
   ```

### For Administrators

1. **Toggle Market Status**
   ```clarity
   (toggle-market-trading-status)
   ```

2. **Update Oracle**
   ```clarity
   (update-price-oracle-address new-oracle-address)
   ```

3. **Add New Commodity**
   ```clarity
   (register-new-commodity commodity-identifier quantity price)
   ```

## Error Handling

The contract includes comprehensive error codes:
- `ERROR-UNAUTHORIZED-ACCESS` (u100): Unauthorized operation attempt
- `ERROR-INVALID-COMMODITY-PRICE` (u101): Invalid price input
- `ERROR-INSUFFICIENT-ESCROW-BALANCE` (u102): Insufficient funds
- `ERROR-TRADING-DISABLED` (u103): Market is closed
- `ERROR-INVALID-TRADE-QUANTITY` (u104): Invalid trade amount
- `ERROR-ESCROW-TRANSACTION-FAILED` (u105): Escrow operation failed

## Security Considerations

1. **Access Control**
   - Administrator-only functions are protected
   - Escrow system prevents unauthorized withdrawals

2. **Trade Validation**
   - Minimum trade quantity enforcement
   - Price validation
   - Balance verification before execution

3. **Fund Safety**
   - Escrow-based trading
   - Atomic settlements
   - Balance checks before operations

## Best Practices

1. **For Traders**
   - Always verify transaction parameters
   - Maintain sufficient escrow balance
   - Monitor position status regularly
   - Verify market status before trading

2. **For Administrators**
   - Regular oracle updates
   - Periodic market status review
   - Monitor trading volumes
   - Validate new commodity parameters

## Limitations and Known Issues

1. **Price Updates**
   - Relies on external oracle
   - Update frequency dependent on oracle

2. **Trade Execution**
   - Minimum trade quantity enforced
   - Maximum position size not implemented

3. **Market Hours**
   - No automatic market hour controls
   - Manual trading status toggle only

## Future Enhancements

1. **Planned Features**
   - Multi-oracle support
   - Advanced position types
   - Automated market makers
   - Position transfer capability
   - Advanced reporting features

2. **Under Consideration**
   - Margin trading
   - Stop-loss orders
   - Automated liquidation
   - Market maker incentives

## Contributing

We welcome contributions! Please follow these steps:
1. Fork the repository
2. Create a feature branch
3. Submit a pull request
4. Follow coding standards
5. Include tests for new features
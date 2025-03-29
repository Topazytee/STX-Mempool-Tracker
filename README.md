# STX-Mempool Real-Time Live Tracker

## Overview
The **Mempool Real-Time Live Tracker** is a smart contract designed for the **Stacks blockchain** to monitor and analyze mempool statistics in real time. This contract provides functionality to track transactions, update statuses, manage user watchlists, and maintain fee statistics and mempool metrics. Additionally, it includes administrative functions for setting minimum fee thresholds and transferring contract ownership.

## Features
- **Transaction Tracking**: Stores and updates transaction details including fee rate, size, priority, and confirmation status.
- **User Watchlist Management**: Enables users to track specific transactions and receive notifications based on alert thresholds.
- **Fee Statistics Management**: Records minimum, maximum, and recommended fees for different levels of urgency.
- **Mempool Metrics Monitoring**: Tracks mempool size, transaction count, average confirmation time, and congestion levels.
- **Administrative Controls**: Allows the contract owner to set fee thresholds and transfer ownership.

## Smart Contract Structure
### Error Codes
The contract defines several error codes for validation and authorization checks:
- `ERR-NOT-AUTHORIZED (1000)`: Unauthorized access.
- `ERR-INVALID-PARAMS (1001)`: Invalid input parameters.
- `ERR-NOT-FOUND (1002)`: Requested data not found.
- `ERR-ALREADY-EXISTS (1003)`: Attempt to add an existing entity.
- `ERR-INVALID-FEE (1004)`: Invalid fee rate provided.
- `ERR-INVALID-SIZE (1005)`: Invalid transaction size.
- `ERR-INVALID-THRESHOLD (1006)`: Invalid fee threshold value.
- `ERR-INVALID-STATS (1007)`: Invalid fee statistics data.
- `ERR-INVALID-METRICS (1008)`: Invalid mempool metrics.
- `ERR-INVALID-CATEGORY (1009)`: Invalid transaction category.
- `ERR-INVALID-TX-ID (1010)`: Invalid transaction ID format.
- `ERR-INVALID-USER (1011)`: Invalid user principal.
- `ERR-INVALID-HEIGHT (1012)`: Invalid block height.
- `ERR-INVALID-OWNER (1013)`: Ownership transfer validation failure.

### Data Structures
The contract maintains various data maps and variables:
- `tracked-transactions`: Stores transaction details such as fee rate, size, priority, timestamp, confirmation status, category, and estimated confirmation time.
- `user-watchlists`: Maintains user-specific transaction watchlists and alert preferences.
- `fee-stats`: Holds historical fee data based on block height.
- `mempool-metrics`: Records real-time mempool statistics.
- `contract-owner`: Stores the contract owner’s principal.
- `last-update`: Tracks the last update timestamp.
- `total-tracked-tx`: Counts the total transactions tracked.
- `min-fee-threshold`: Stores the minimum allowed fee threshold.

## Functions
### Public Functions
#### Transaction Management
- `track-transaction(tx-id, fee-rate, size, category)`: Adds a new transaction to the tracker.
- `update-transaction-status(tx-id, confirmed)`: Updates the confirmation status of a transaction.

#### Watchlist Management
- `add-to-watchlist(user, tx-id)`: Adds a transaction to a user’s watchlist.

#### Fee and Mempool Metrics
- `update-fee-statistics(height, stats)`: Updates fee-related statistics for a given block height.
- `update-mempool-metrics(metrics)`: Updates mempool size, transaction count, confirmation time, and congestion level.

#### Administrative Functions
- `set-min-fee-threshold(new-threshold)`: Updates the minimum required fee threshold.
- `transfer-ownership(new-owner)`: Transfers contract ownership to a new principal.

### Read-Only Functions
- `get-transaction-details(tx-id)`: Retrieves details of a specific transaction.
- `get-user-watchlist(user)`: Returns a user’s watchlist details.
- `get-fee-statistics(height)`: Fetches stored fee statistics for a specific block height.

## Validations
The contract includes several validation functions to ensure data integrity:
- `validate-fee-rate(fee-rate)`: Checks if the fee rate is within allowable limits.
- `validate-size(size)`: Ensures the transaction size is within the set limits.
- `validate-tx-id(tx-id)`: Validates transaction ID format.
- `validate-category(category)`: Ensures valid category names.
- `validate-stats(stats)`: Checks if fee statistics are structured correctly.
- `validate-metrics(metrics)`: Ensures mempool metric values fall within acceptable ranges.
- `validate-height(height)`: Validates block height.
- `validate-new-owner(new-owner)`: Ensures new owner differs from the current contract owner.

## Priority and Estimation Functions
- `calculate-priority(fee-rate, size)`: Determines transaction priority based on fee rate and size.
- `estimate-confirmation-time(fee-rate, congestion)`: Estimates confirmation time using fee rate and congestion level.

## Authorization
- `is-contract-owner()`: Ensures only the contract owner can perform administrative actions.

## Installation & Deployment
1. Install Clarity tools and Stacks blockchain dependencies.
2. Deploy the contract to the Stacks blockchain using the Clarity CLI or the Stacks Explorer.
3. Interact with the contract using Clarity scripts or API calls.

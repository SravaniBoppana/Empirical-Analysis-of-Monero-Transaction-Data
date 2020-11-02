# Empirical-Analysis-of-Monero-Transaction-Data

## Scope

Every field in a transaction falls into one of four buckets:
1. Signer-selected, expected to be non-uniform across transactions (e.g. unlock time)
2. Descriptive, expected to be non-uniform acrosss all transactions (e.g. transaction version)
3. Signer-selected, expected to be uniform across transactions (e.g. MLSAG/CLSAG scalars)
4. Function output, expected to be uniform across all transactions (e.g. public keys)


### Monero
Consider a random 1-in/2-out transaction: [https://xmrchain.net/tx/fd903232053a5ac6d8cf99ce494da2ec73488c94c33ee587523ae356b59b5579](https://xmrchain.net/tx/fd903232053a5ac6d8cf99ce494da2ec73488c94c33ee587523ae356b59b5579). The raw transaction data is below the table

Our expectations, labeled by the buckets described above, are:

| field_name   | field_type          | distro_expectation | num_vals | example_val                                                       |
|--------------|---------------------|--------------------|----------|-------------------------------------------------------------------|
| unlock_time  | [1] signer selected | non-uniform        | 1        | 0                                                                 |
| key_offsets  | [1] signer selected | non-uniform        | 11       | 19599438                                                          |
| extra        | [1] signer selected | non-uniform        | 44       | 2                                                                 |
| txnFee       | [1] signer selected | non-uniform        | 1        | 136770000                                                         |
| version      | [2] descriptive     | non-uniform        | 1        | 2                                                                 |
| amount (in)  | [2] descriptive     | non-uniform        | 1        | 0                                                                 |
| type         | [2] descriptive     | non-uniform        | 1        | 4                                                                 |
| nbp          | [2] descriptive     | non-uniform        | 1        | 1                                                                 |
| ss           | [3] signer selected | uniform            | 22       | 22f88f4f232a8e02f93dc17f8b250fcc449b0373819e2aa7b9bcc54f51b6e905 |
| k_image      | [4] crypto output   | uniform            | 1        | 1a01d8440f022d0b0760ba3fbc8afc4a12924135a33442730384672d7b83fc4e  |
| key          | [4] crypto output   | uniform            | 1        | 94125a4ac1171a57f908b532dda050bac0791adeee855e7ce4696835953ac45c  |
| amount (out) | [4] crypto output   | uniform            | 1        | 8cd29109454982ad                                                  |
| outPk        | [4] crypto output   | uniform            | 2        | 6a97cea40d6763f1cd68c966ec9ee827a7841faf70fa82e95491fe1b668d3e40  |
| pseudoOuts   | [4] crypto output   | uniform            | 1        | b289c2ebd5f5aff23c5c426fc7fefce0339fb1658dffe76648c37aa5fe743fd3] |
| R            | [4] crypto output   | uniform            | 7        | b5cdc4fba8caeae03da889404275c52507ac7707f60e59205134b6562eb82bbe  |
| cc           | [4] crypto output   | uniform            | 1        | fc2593c669652ec1a144a1bba8e5acd4990e7d552dd106cb32798096a48c0608  |
| A            | [4] crypto output   | uniform            | 1        | ee1a86b7d570628cbda5458623f5d300fc9e178cefc0fa6f8ba3772b2f85d63c  |
| S            | [4] crypto output   | uniform            | 1        | 517f04819c405ccf89309bf3c6c2d4ad86059fd877851c1d752593529265b50f  |
| T1           | [4] crypto output   | uniform            | 1        | a4466b683f4299cc88550a94d562ee2b6c8c4e77ce6fe17e51be88c0b0289927  |
| T2           | [4] crypto output   | uniform            | 1        | 7f7396420c64f5dfab1e82f06caa7bc408d4cec4cc4dd3249a2dc905aa12942f  |
| taux         | [4] crypto output   | uniform            | 1        | 7b886a9c8642ce258ab7eed4fd57aecd6ffe264e7b6fb0dd53e9395c7cf22902  |
| mu           | [4] crypto output   | uniform            | 1        | 6db7ec71b23d9b4141309848338f697f63bed31bf6e29d4eb00cfbae6838ba0b  |
| L            | [4] crypto output   | uniform            | 7        | aeee6d21c477b6420d42eaf0cbf79e925205d9bcff60e107da77004535227cdb  |
| a            | [4] crypto output   | uniform            | 1        | b44cefe5c19b485dfde10bc63280db5bedd39b53427b7f9abecfde70e78dc50f  |
| b            | [4] crypto output   | uniform            | 1        | 061bf7695eb15bae7b868369dfad1a11c8726aa653f819ebb33071fc04b3f706  |
| t            | [4] crypto output   | uniform            | 1        | f4386476bb24e1cf5c228643d3c97e526f155f5375c0a7b688c32ff40a2e7f01  |

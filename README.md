# DecentralizedLottery-smart-contract
## code description
Here's a breakdown of what each line in the DecentralizedLottery smart contract does:

1. `// SPDX-License-Identifier: MIT`: This line specifies the software license, MIT in this case, which is a permissive open-source license.
2. `pragma solidity ^0.8.7;`: This line specifies the Solidity compiler version the contract is compatible with, which is any version greater than or equal to 0.8.7 and less than 0.9.0.
3. `contract DecentralizedLottery {`: This line defines the start of the DecentralizedLottery contract.
4. `address payable[] public participants;`: This line declares a public array of payable address called `participants`, which will store the addresses of lottery participants.
5. `address public owner;`: This line declares a public address variable called `owner`, which represents the contract owner's address.
6. `uint public entryFee;`: This line declares a uint (unsigned integer) variable called `entryFee`, which represents the lottery entry fee in wei.
7. `uint public maxParticipants;`: This line declares a uint variable called `maxParticipants`, which represents the maximum number of participants allowed in the lottery.
8. `event LotteryEntered(address indexed participant);`: This line declares an event called `LotteryEntered`, which is emitted when a participant enters the lottery, and it includes the participant's address.
9. `event LotteryWon(address indexed winner, uint prize);`: This line declares an event called `LotteryWon`, which is emitted when a winner is selected, and it includes the winner's address and the prize amount.
10. `constructor(uint _entryFee, uint _maxParticipants) {`: This line defines the constructor function, which sets the `entryFee` and `maxParticipants` values when the contract is deployed.
11. `owner = msg.sender;`: This line sets the `owner` variable to the address that deployed the contract.
12. `entryFee = _entryFee;`: This line sets the `entryFee` variable to the specified `_entryFee` value passed to the constructor.
13. `maxParticipants = _maxParticipants;`: This line sets the `maxParticipants` variable to the specified `_maxParticipants` value passed to the constructor.
14. `}`: This line marks the end of the constructor function.
15. `function enterLottery() public payable {`: This line defines a public payable function called `enterLottery`, which allows users to enter the lottery by sending Ether to the contract.
16. `require(msg.value == entryFee, "Invalid entry fee.");`: This line checks if the sent Ether amount (`msg.value`) is equal to the required entry fee; if not, it throws an error.
17. `require(participants.length < maxParticipants, "Max participants reached.");`: This line checks if the number of participants is less than the maximum allowed; if not, it throws an error.
18. `require(!isParticipant(msg.sender), "Address already participating.");`: This line checks if the sender's address is already participating in the lottery; if it is, it throws an error.
19. `participants.push(payable(msg.sender));`: This line adds the sender's address to the `participants` array.
20. `emit LotteryEntered(msg.sender);`: This line emits the `LotteryEntered` event, including the participant's address.
21. `if (participants.length == maxParticipants) {`: This line checks if the number of participants has reached the maximum allowed.
22. `selectWinner();`: This line calls the `selectWinner()` function to select a winner and distribute the prize.
23. `}`: This line marks the end of the if statement

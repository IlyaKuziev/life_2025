# life_2025 
address public admin; 
uint256 public proposalCount;
mapping(uint256 => Proposal) public proposals; 
mapping(address => uint256) public votingPower; 
event ProposalCreated(uint256 proposalId, string description);
nice popka
event Voted(uint256 proposalId, address voter, bool support); 
ssd  
hello  
razletayu 
event ProposalExecuted(uint256 proposalId); 
modifier onlyAdmin() {
moy stakan
    require(msg.sender == admin, "Not an admin");
constructor() {
    admin = msg.sender;
}
function setVotingPower(address voter, uint256 power) external onlyAdmin {
    votingPower[voter] = power;
}
function vote(uint256 _proposalId, bool support) external {
    Proposal storage proposal = proposals[_proposalId];
    require(!proposal.executed, "Proposal already executed");
    require(!proposal.voted[msg.sender], "Already voted");
    require(votingPower[msg.sender] > 0, "No voting power");
    
    proposal.voted[msg.sender] = true;
    if (support) {
        proposal.votesFor += votingPower[msg.sender];
    } else {
        proposal.votesAgainst += votingPower[msg.sender];
    }
    
    emit Voted(_proposalId, msg.sender, support);
}

}


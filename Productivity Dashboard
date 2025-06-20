// SPDX-License-Identifier: MIT
pragma solidity ^0.8.17;

contract ProductivityDashboard {
    address public owner;
    uint256 public projectCount;

    struct Project {
        string title;
        string description;
        bool completed;
    }

    mapping(uint256 => Project) public projects;

    constructor() {
        owner = msg.sender;
        projectCount = 0;
    }

    modifier onlyOwner() {
        require(msg.sender == owner, "Only owner can call this function");
        _;
    }

    function addProject(string memory _title, string memory _description) public onlyOwner {
        projects[projectCount] = Project(_title, _description, false);
        projectCount++;
    }

    function toggleCompletion(uint256 _projectId) public onlyOwner {
        require(_projectId < projectCount, "Invalid project ID");
        projects[_projectId].completed = !projects[_projectId].completed;
    }

    function updateDescription(uint256 _projectId, string memory _newDescription) public onlyOwner {
        require(_projectId < projectCount, "Invalid project ID");
        projects[_projectId].description = _newDescription;
    }
}

js3
Simple overview of use/purpose.

Description
An in-depth paragraph about your project and overview of use.

Getting Started
Installing
*No Installation Needed

Executing program
How to run the program
Open In Remix
Compile
Deploy
Contract



pragma solidity ^0.5.0;

contract Sharer {
    function sendHalf(address payable addr) public payable returns (uint balance) {
        require(msg.value % 2 == 0, "Even value required."); 

        uint balanceBeforeTransfer = address(this).balance; 

        (bool success, ) = addr.call.value(msg.value / 2)(""); 
        require(success); // Ensure transfer succeeded

        // Assert that contract balance is reduced by exactly half of msg.value
        assert(address(this).balance == balanceBeforeTransfer - msg.value / 2);

        return address(this).balance; // Return current contract balance
    }
}


Help
Any advise for common problems or issues.

command to run if program contains helper info
Authors
Contributors names and contact info

ex.Dhairyaa ex.

License
This project is licensed under the [dhairyaa] License - see the LICENSE.md file for details

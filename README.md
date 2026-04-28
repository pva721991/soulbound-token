# Soulbound-Token
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.26;

contract SoulboundToken {
    string public name = "Base Soulbound";
    string public symbol = "BSBT";

    mapping(uint256 => address) public ownerOf;
    mapping(address => uint256) public balanceOf;

    uint256 public totalSupply;

    event SoulboundMinted(address indexed to, uint256 tokenId);

    function mint(address to, uint256 tokenId) public {
        require(ownerOf[tokenId] == address(0), "Already minted");
        ownerOf[tokenId] = to;
        balanceOf[to] += 1;
        totalSupply++;
        emit SoulboundMinted(to, tokenId);
    }

    // Transfer functions disabled (Soulbound)
    function transferFrom(address, address, uint256) public pure {
        revert("Soulbound: Transfers disabled");
    }
}

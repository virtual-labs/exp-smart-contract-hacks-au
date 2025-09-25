### Theory

<h4>Overflow and Underflow Attacks on Smart Contracts</h4> <p>Smart contracts often use integer variables to store balances, counters, or other numeric values. However, integers in Solidity have finite sizes, meaning they can only represent values within a specific range:</p> <ul> <li><b>uint8:</b> Unsigned integers from 0 to 255</li> <li><b>uint16:</b> Unsigned integers from 0 to 65,535</li> </ul> <p><b>Overflow:</b> An overflow occurs when a calculation exceeds the maximum value the data type can store. For example, adding 1 to a uint8 with value 255 wraps it back to 0. This happens due to arithmetic wrapping caused by the finite range of the integer type.</p> <p><b>Underflow:</b> Conversely, an underflow occurs when a calculation goes below the minimum value (0), wrapping around to the maximum value of the data type.</p> <p><b>Impact:</b> Overflow and underflow vulnerabilities can allow attackers to manipulate balances, bypass limits, or mint unlimited tokens. While modern Solidity versions have built-in overflow/underflow protection, understanding this vulnerability is crucial for analyzing legacy contracts.</p> <p><b>Hands-on Hint:</b> In this experiment, you will attempt to overflow a <b>uint8</b> balance to observe how arithmetic wrapping affects contract behavior.</p>

<h4>Re-entrancy</h4>
<p>The re-entrancy attack is one of the most destructive attacks in Solidity smart contracts. A re-entrancy attack occurs when a function makes an external call to another untrusted contract, and then the untrusted contract makes a recursive call back to the original function in an attempt to drain funds.</p>
<p>A re-entrancy attack involves two smart contracts: a vulnerable contract and an untrusted attacker’s contract.</p>
<div><img src="./images/reentrance.png" alt="re-entrance"></div>

<h4>Accessing Private Data</h4> <p>In Solidity, marking a variable <code>private</code> prevents direct access from other contracts but does <strong>not</strong> hide the value from the public. Because blockchains are transparent, any data stored on-chain can be read by anyone using blockchain explorer tools or by directly inspecting transaction/storage data.</p> <p><strong>Example:</strong></p> <pre><code>pragma solidity ^0.6.0;

contract PrivateData {
string private password = "mySecret123"; // still visible on the blockchain
}
</code></pre>

<p><strong>Exploit Impact:</strong> If sensitive information—such as passwords, private keys, API tokens, or secret salts—is stored on-chain, attackers can retrieve it directly from the blockchain even when the variable is declared <code>private</code>. This can lead to credential leaks, unauthorized access, and downstream compromises.</p> 
<div><img src="./images/reentrance.png" alt="re-entrance"></div>

<h4>Accessing Private Data</h4>
<p>When writing code for a blockchain-based application, you can define a variable as public or private. The purpose of defining a variable as private is to prevent other contracts from modifying it. However, blockchains are designed to be transparent, meaning that regardless of whether a variable is private or public, everyone can read it. Therefore, storing sensitive information like passwords is a very bad idea.</p>

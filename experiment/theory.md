### Theory

<h5>Overflow and Underflow Attacks on Smart Contracts</h5>
<p><b>Overflow:</b></p>
<p>An overflow occurs when a mathematical operation on integers attempts to produce a value exceeding the highest representable value for the chosen data type. This can be visualized as arithmetic wrapping around due to the finite range integers can hold within a specific data type.</p>
<p><b>Underflow:</b></p>
<p>The counterpart to overflow, underflow arises when an arithmetic operation on integers results in a value lower than the minimum representable value for the data type employed.</p>
<p><b>Uint8</b> and <b>Uint16</b> are data types commonly used in Solidity, a programming language specifically designed for creating smart contracts on the Ethereum blockchain.</p>

<p><b>Uint8:</b></p>
<li>Represents unsigned integers ranging from 0 to 255 (inclusive).</li>
<p><b>Uint16:</b></p>
<li>Represents unsigned integers ranging from 0 to 65,535 (inclusive).</li>

<h5>Re-entrancy</h5>
<p>The re-entrancy attack is one of the most destructive attacks in Solidity smart contracts. A re-entrancy attack occurs when a function makes an external call to another untrusted contract, and then the untrusted contract makes a recursive call back to the original function in an attempt to drain funds.</p>
<p>A re-entrancy attack involves two smart contracts: a vulnerable contract and an untrusted attacker’s contract.</p>
<div><img src="./images/reentrance.png" alt="re-entrance"></div>

<h5>Accessing Private Data</h5>
<p>When writing code for a blockchain-based application, you can define a variable as public or private. The purpose of defining a variable as private is to prevent other contracts from modifying it. However, blockchains are designed to be transparent, meaning that regardless of whether a variable is private or public, everyone can read it. Therefore, storing sensitive information like passwords is a very bad idea.</p>
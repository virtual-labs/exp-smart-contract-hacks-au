<!-- ### Procedure -->

<h5>Overflow & Underflow</h5>
<br>
<p>
  1. Open the Smart Contract Vulnerabilities page and choose either <b>Overflow</b> or <b>Underflow</b> from the right-side control panel by clicking on <b>Overflow &amp; Underflow</b>.
</p>

<div>
  <img src="./images/main.png" alt="overflow-underflow">
</div>
<br>
<p>
  2. Under <b>Select Vulnerability Type</b>, click <b>Overflow</b> and observe the initial balances where <b>Alice (Sender)</b> has 10 tokens and <b>Bob (Recipient)</b> has 255 tokens (maximum value of uint8).
</p>
<div><img src="./images/overflow1.png" alt="overflow-underflow"></div>
<br>
<p>
  3. In the <b>Tokens to Send</b> input field, enter <b>1</b>, click on <b>“Alice Sends Tokens to Bob”</b>, observe a popup showing <b>“Vulnerability Detected – Integer Overflow”</b>, and note that the calculation <b>(255 + 1 = 0)</b> causes Bob’s balance to wrap from <b>255 to 0 tokens</b>, which is confirmed in the <b>Transaction History</b> where the overflow vulnerability is highlighted.
</p>

<div><img src="./images/overflow2.png" alt="overflow-underflow"></div>
<br>
<p>
  4. From the right-side control panel under <b>Overflow &amp; Underflow</b>, click <b>Underflow</b> and observe that <b>Eve</b> has an initial balance of <b>0 tokens</b>.
</p>

<div><img src="./images/underflow1.png" alt="overflow-underflow"></div>

<p>
 5. In the <b>Tokens to Withdraw</b> input field, enter <b>1</b> and click on <b>“Eve Withdraws Tokens”</b>.
</p>

<div><img src="./images/underflow2.png" alt="overflow-underflow"></div>
<br>
<p>
  6. Observe a popup displaying <b>“Vulnerability Detected – Integer Underflow”</b>, where the calculation <b>(0 − 1 = 255)</b> causes Eve’s balance to wrap from <b>0 to 255 tokens</b>, which is confirmed in the <b>Transaction History</b> indicating the underflow vulnerability.
</p>

<div><img src="./images/underflow3.png" alt="overflow-underflow"></div>
<br>
<h5>Re-entrancy</h5>
<p>Click on the attack button and observe the changes happening carefully.</p>
<div><img src="./images/reentry.png" alt="re-entrancy"></div>
<p>Step 1: The attack() function deposits 1 ETH into the Bank contract.</p>
<div><img src="./images/step1.png" alt="re-entrancy"></div>
<p>Step 2: The attack() function deposits 1 ETH into the Bank contract.</p>
<div><img src="./images/step2.png" alt="re-entrancy"></div>
<p>Step 3: Since the balance of msg.sender (the Attack contract's address) is greater than 0, an external contract is called to send the value.</p>
<div><img src="./images/step3.png" alt="re-entrancy"></div>
<p>Step 4: When the Attack contract receives ETH from the Bank contract, the fallback() function is called. First, it checks the balance in the Bank contract, then it calls the withdraw() function in the Bank contract again.</p>
<div><img src="./images/step4.png" alt="re-entrancy"></div>
<p>Step 5: The line balances[msg.sender] = 0 is not reached because msg.sender.call has not finished yet. This continues until all the funds in the Bank contract are drained.</p>
<div><img src="./images/step5.png" alt="re-entrancy"></div>
<!-- <p>Step 6</p>
<div><img src="./images/step6.png" alt="re-entrancy"></div> -->

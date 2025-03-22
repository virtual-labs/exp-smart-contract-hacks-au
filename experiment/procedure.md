### Procedure
<h5>Overflow & Underflow</h5>
<p>Choose overflow and underflow from the following options.</p>
<div><img src="./images/mainpage.png" alt="overflow-underflow"></div>

<p>Enter the value for Uint8.</p>
<div><img src="./images/value.png" alt="overflow-underflow"></div>
<p>Enter a value greater than 255.</p>
<div><img src="./images/overflowed.png" alt="overflow-underflow"></div>
<p>Click on the help button to see the explanation.</p>
<div><img src="./images/help.png" alt="overflow-underflow"></div>
<p>Click on the underflow button.</p>
<div><img src="./images/underflow.png" alt="overflow-underflow"></div>
<p>Enter a value for Uint8.</p>
<div><img src="./images/valueunder.png" alt="overflow-underflow"></div>
<p>Enter a value less than 0.</p>
<div><img src="./images/errorunder.png" alt="overflow-underflow"></div>
<p>Click on the help button to see the explanation.</p>

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
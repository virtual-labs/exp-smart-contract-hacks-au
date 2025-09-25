### Procedure

<h5>Overflow & Underflow</h5>

<p>1. Choose <b>Overflow</b> or <b>Underflow</b> from the given options.</p>
<div><img src="./images/image1.png" alt="overflow-underflow"></div>

<p>2. Select the data type as <b>uint8</b>.</p>
<div><img src="./images/image2.png" alt="overflow-underflow"></div>

<p>3. Enter a value greater than 255.</p>
<div><img src="./images/image3.png" alt="overflow-underflow"></div>

<p>4. Click the <b>Help</b> button to see the explanation.</p>
<div><img src="./images/image4.png" alt="overflow-underflow"></div>

<p>5. Click the <b>Underflow</b> button and select a data type.</p>
<div><img src="./images/image5.png" alt="overflow-underflow"></div>

<p>6. Enter a value less than 0.</p>
<div><img src="./images/image6.png" alt="overflow-underflow"></div>

<p>7. Click the <b>Help</b> button to see the explanation.</p>
<div><img src="./images/image7.png" alt="overflow-underflow"></div>

<p>8. Click the <b>Show Example</b> button to view an example of overflow.</p>
<div><img src="./images/image8.png" alt="overflow-underflow"></div>

<p>9. Enter an amount greater than the sender’s balance.</p>
<div><img src="./images/image9.png" alt="overflow-underflow"></div>

<p>10. Click the <b>Transfer</b> button to see an overflow alert message.</p>
<div><img src="./images/image10.png" alt="overflow-underflow"></div>

<p>11. Enter a negative amount.</p>
<div><img src="./images/image13.png" alt="overflow-underflow"></div>

<p>12. Click the <b>Transfer</b> button.</p>

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

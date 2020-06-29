<script>
	export let name;
	import Numpad from './Numpad.svelte';
	let firstNumerator = '';
	let secondNumerator = '';
	let operator = '';
	$: result = calculate(firstNumerator, secondNumerator, operator);

	function handleButtonClick(event){
		const value = event.detail.value;
		if(isNaN(value)){ //First number filled. Is an operator
			handleOperators(value);
		}else{
			if(!operator) { // Operator NOT filled. Is first number
				firstNumerator = `${firstNumerator}${value}`;
			} if(operator){ // Operator filled. Is second number
				secondNumerator = `${secondNumerator}${value}`;
			}
		}
		
		result = calculate(firstNumerator, secondNumerator, operator);
	}

	function handleOperators(newOperator){
		switch(newOperator){
			case 'C':
				resetCalculator();
				break;
			default:
				operator = newOperator;
				break;
		}
	}

	function resetCalculator(){
		firstNumerator = '';
		secondNumerator = '';
		operator = '';
	}

	function calculate(firstNumerator, secondNumerator, operator){
		if(!firstNumerator || !secondNumerator){
			return null;
		}
		const firstNum = Number(firstNumerator);
		const secondNum = Number(secondNumerator);
		switch (operator) {
			case '+':
				return firstNum + secondNum;
			case '-':
				return firstNum - secondNum;
			case '*':
				return firstNum * secondNum;		
			default:
				return null;
		}
	}
</script>
<main>
	<h1>Special {name}!</h1>
	<h1>> {firstNumerator} {operator} {secondNumerator} </h1>
	<!-- {#if !isNaN(result) && result}
		<h1>= <strong>{result}</strong></h1>
	{/if} -->
		<h1>= <strong>{result ? result : '?'}</strong></h1>
	<Numpad on:btnValue={handleButtonClick}/>
</main>
<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}
	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}
	h1 > strong {
		color: green;
	}
	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>
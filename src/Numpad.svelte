<script>
    import Button from './Button.svelte';
	import { createEventDispatcher } from 'svelte';
    const dispatch = createEventDispatcher();
    const buttonsValues = [1, 2, 3, 4, 5, 6, 7, 8, 9, 'C', 0, '+', '*', '-'];
    const dispatchValue = (value)=>{
        dispatch('btnValue', {
            value: value
        });
    }
</script>

<div class='container'>
    {#each buttonsValues as value}
        <Button on:click={()=> dispatchValue(value)} {value}/>
    {/each}
</div>

<style>
    .container{
        display: grid;
        grid-gap: 0;
        grid-template-columns: repeat(3, 1fr);
        width: min-content;
        margin: auto;
    }
</style>
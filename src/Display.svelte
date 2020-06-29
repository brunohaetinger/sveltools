<script>
    export let firstNumerator, operator, secondNumerator;
</script>

<main>
    <h1>{firstNumerator} {operator} {secondNumerator} </h1>
</main>

<style>
    h1::before {
        content: "> ";
        text-decoration: blink;
        -webkit-animation-name: blinker;
        -webkit-animation-duration: 0.6s;
        -webkit-animation-iteration-count:infinite;
        -webkit-animation-timing-function:ease-in-out;
        -webkit-animation-direction: alternate;
    }
    @-webkit-keyframes blinker {
        from {opacity: 1.0;}
        to {opacity: 0.0;}
    }
</style>
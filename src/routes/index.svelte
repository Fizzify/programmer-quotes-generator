<script context="module">
  export async function load({ fetch }) {
    const res = await fetch('https://programming-quotes-api.herokuapp.com/quotes/random');
    const data = await res.json();
    if (res.ok) {
      return { 
	props: { quote: data }
      }
    } else {
      return {
	props: { quote: "Sadly, you have no internet." }
      }
    }
  }
</script>

<script>
  import ProgrammingQuotes from '../components/ProgrammingQuotes.svelte';
  export let quote;
</script>

<section>
  <ProgrammingQuotes {quote} />
</section>

<style>
  *,
  *::before,
  *::after {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }
  
  section {
    height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    text-align: center;
    font-family: Arial, sans-serif;
  }
</style>

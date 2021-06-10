<script>
  import { onMount } from "svelte";

  export let name;
  export let data = "no data";
  let GetData = async url => {
    let fh = await fetch(url);
    return await fh.json();
  };
  onMount(async () => {
    let d = await GetData("/data");
    data = d.data;
  });
</script>

<main>
  <h1>This is a Express-Svelte {name}!</h1>
  <p>
    Visit the <a href="https://svelte.dev/tutorial">Svelte tutorial</a> to learn
    how to build Svelte apps.
  </p>
  <p>{data}</p>
</main>

<style>
  main {
    text-align: center;
    padding: 1em;
    max-width:100vh;
    margin: 0 auto;
  }

  h1 {
    color: #ff3e00;
    text-transform:uppercase;
    font-size: 4em;
    font-weight: 100;
  }

</style>

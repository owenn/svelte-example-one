<script>
    import { onMount } from "svelte";
    import { apiData, shipNames } from './store.js';
    
    onMount(async () => {
      fetch("http://jane:5000/v1/ships")
      .then(response => response.json())
      .then(data => {
            console.log(data);     
        apiData.set(data);
      }).catch(error => {
        console.log(error);
        return [];
      });
    });
</script>
    
    <main>
        <h1>Ship names</h1>
        <ul>
        {#each $shipNames as shipName}
            <li>{shipName}</li>
        {/each}
        </ul>
    </main>
    
    <style>
    
    </style>
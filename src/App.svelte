<script>
  /* export let name; */

  import PokeCard from "./components/PokeCard.svelte";

  let endPoint = "https://pokeapi.co/api/v2/pokemon?limit=100";
  let pokemons = [];

  function getDataApi(endPoint) {
    fetch(endPoint)
      .then((res) => res.json())
      .then((data) => {
        data.results.forEach((r) => {
          fetch(r.url)
            .then((res) => res.json())
            .then((d) => {
              console.log();
              let test = {
                name: d.name,
                img: d.sprites.front_default,
                ability: d.abilities[0].ability.name,
                shiny: d.sprites.front_shiny,
              };
              pokemons = [...pokemons, test];
            });
        });
      });
  }

  getDataApi(endPoint);
</script>

<div class="wrapper">
  <h1>PokeApi List</h1>
  <div class="poke-list">
    {#each pokemons as { name, img, ability, shiny }}
      <PokeCard {name} {img} {ability} {shiny} />
    {/each}
  </div>
</div>

<style>
  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }
  .wrapper {
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  .poke-list {
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
    justify-content: center;
  }
</style>

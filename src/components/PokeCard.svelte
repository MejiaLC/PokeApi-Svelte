<script>
  export let name;
  export let ability;
  export let img;
  export let shiny;

  let imgType;
  let section;

  function changeImage() {
    imgType = section.querySelector(".img");

    if (imgType.dataset.shiny === "false") {
      console.log("No es shiny");
      imgType.src = img;
      imgType.dataset.shiny = "true";
    } else {
      console.log("Si es shiny");
      imgType.src = shiny;
      imgType.dataset.shiny = "false";
    }
  }
</script>

<div class="card" bind:this={section}>
  <p>{name}</p>
  <p>{ability}</p>
  <img src={img} alt={name} class="img" data-shiny="true" />
  <button bind:this={imgType} on:click={() => changeImage()}>Change Img</button>
</div>

<style>
  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }
  .card {
    display: flex;
    flex-direction: column;
    border: 1px solid #000;
    margin: 2.5rem;
    background-color: blueviolet;
  }

  .card p {
    text-align: center;
    background-color: red;
    padding: 10px 0;
    box-shadow: 0 10px 5px;
    text-transform: uppercase;
    cursor: pointer;
  }

  .card p:hover {
    background-color: silver;
  }

  .card img {
    object-fit: cover;
    background-color: skyblue;
    width: 250px;
  }

  button {
    padding: 10px;
    cursor: pointer;
  }
</style>

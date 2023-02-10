<script>

</script>

<template>
  <div class="container">
    <div>
      <img src="https://fontmeme.com/permalink/230210/1c172e1146ef8ed4174e7fc5db83540e.png" alt="Logo do aplicativo Pokelist">
    </div>

    <input type="text" placeholder="Busque o nome de um Pokémon" :aria-checked="'true'">
  </div>
</template>

<style scoped>
  .container{
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    height: 100vh;
    gap: 1.5rem;
  }
  
  .container > div {
    margin: 0 auto;
  }
  .container img {
    max-width: 18em;
  }
</style>

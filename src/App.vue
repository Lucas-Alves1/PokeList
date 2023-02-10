<script>

</script>

<template>
  <div class="container">
    <div>
      <img 
        src="https://fontmeme.com/permalink/230210/1c172e1146ef8ed4174e7fc5db83540e.png" 
        alt="Logo do aplicativo Pokelist"
      >
    </div>

    <div class="text-container">
      <p>Busque o nome de seu Pokémon favorito!</p>
    </div>

    <div>
      <input 
        type="text" 
        placeholder="Digite aqui:"
        :aria-checked="true"
      >
    </div>
  </div>
</template>

<style scoped>
  .container{
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    height: 100vh;
    gap: 1rem;
  }
  
  .container + div {
    margin: 0 auto;
  }

  .container input{
    height: 2rem;
    border-radius: 4px;
    border: transparent 1px solid;
    background-color: rgba(84, 84, 84, 0.65);
    padding: 0.5rem;
    font-size: 1rem;
    font-family: inherit;
    color: #f8f8f8;
  }

  .container input:focus{
    outline: 2px #356abc solid;
  }
  
  @media (max-width: 60em) {
    .container img {
      max-width: clamp(3rem, 80vw, 15rem);
      margin: 0;
    }

    .container .text-container {
      font-size: clamp(1rem, 2vw, 2.5rem);
      text-align: center;
      padding: 0 1rem 0 1rem;
    }

    .container input{
      max-width: clamp(5rem, 60vw, 40rem);
    }
  }
</style>

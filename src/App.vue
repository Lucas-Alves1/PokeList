<script>
import axios from "axios";

export default {
  name: 'app',
  components: {},
  data() {
    return {
      name: "",
      pokemons: []
    }
  },
  methods: {
    mostraTexto() {
      return this.name;
    },
    getId(pokemon) {
      return pokemon.url.split("/")[6]
    }
  },
  
  mounted() {
    axios.get(`https://pokeapi.co/api/v2/pokemon/${this.mostraTexto()}?limit=3`).then((response) => {
      this.pokemons = response.data.results;
    })
  },
}
</script>

<template>
  <div class="container">
    <div class="logo">
      <img 
        src="https://fontmeme.com/permalink/230210/1c172e1146ef8ed4174e7fc5db83540e.png" 
        alt="Logo do aplicativo Pokelist"
      >
    </div>

    <div class="text-container">
      <p>Busque o nome de seu Pokémon favorito!</p>
    </div>

    <div>
    <label>
        <input 
        type="text" 
        placeholder="Digite aqui:"
        aria-checked="true"
        v-model="name"
        >
    </label>
    </div>

    <div class="card-container">
      <div class="card">
        <div class="card-info" v-for="pokemon in pokemons" :key="pokemon.name">

          <img :src="`https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/${getId(pokemon)}.png`" :alt="{name}" />
          <h4>{{ pokemon.name }}</h4>
        </div>
      </div>
    </div>

  </div>

  

</template>

<style scoped>
  .container{
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
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
  .card-container {
    margin: 2em 0;
  }
  .card-container .card {
    background-color: #f8f8f8;
    min-width: clamp(10rem, 70vw, 32rem);
    border-radius: 4px;
    margin: 0 0.5rem 0 0.5rem;
    min-height: clamp(10rem, 20vh, 20rem);
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;
    place-items: center;
    text-align: center;
  }

  .card-container .card h4 {
    color: #181818;
    font-size: 1.25rem;
    font-weight: 700;
    margin: 0;
    padding-bottom: 0.5rem;
  }
  .card-container .card h4::first-letter {
    text-transform: uppercase;
  }
  .container .logo img {
    max-width: clamp(3rem, 80vw, 15rem);
    margin: 0;
    margin: 6rem 0 0 0;
    animation: floating infinite 5s ease-in-out;
  }
  
  @media (max-width: 60em) {

    .container .text-container {
      font-size: clamp(1.5rem, 2vw, 2.5rem);
      text-align: center;
      padding: 0 1rem 0 1rem;
    }

    .container input{
      max-width: clamp(5rem, 60vw, 40rem);
    }

    .card-container .card{
      display: flex;
      align-items: center;
      justify-content: center;
      flex-direction: column;
      text-align: center;
    }
    .card-container .card .card-info img{
      min-width: clamp(10em, 20vw, 20em);
    }
  }

  @keyframes floating {
    0% {
        transform: translatey(0px);
    }
    50% {
        transform: translatey(-20px);
    }
    100% {
        transform: translatey(0px);
    }
}
</style>

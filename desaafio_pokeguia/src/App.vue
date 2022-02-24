<template>
  <div class="container">
  <div>
    <img src="https://upload.wikimedia.org/wikipedia/commons/9/98/International_Pok%C3%A9mon_logo.svg" alt="">
    <h1>PokeGuía</h1>
    <br>
    <label> Nombre: </label>
    <input type="text" v-model="pokemon.name" />
    <button @click="buscar">Buscar</button>
    <br>
    <img :src="pokeFoto" />
  </div>
  <div>
    <h3>Movimientos</h3>
    <ol>
      <li v-for="(movimiento, index) in movimientos" :key="index"
      v-text="movimiento.move.name"></li>
    </ol>
  </div>
    <div>
    <h3>Habilidades</h3>
    <ol>
      <li v-for="(habilidad, index) in habilidades" :key="index"
      v-text="habilidad.ability.name"></li>
    </ol>
  </div>
  </div>
</template>
<script>
export default {
  data () {
    return {
      pokemon: {
        name: 'pikachu',
        sprite: {
          front_default: ''
        },
        moves: [],
        abilities: []
      },
      actualizacion: ''
    }
  },
  created(){
    this.buscar()
  },
  methods: {
    buscar() {
      fetch(`https://pokeapi.co/api/v2/pokemon/${this.pokemon.name}`)
      .then(response => response.json())
      .then(json => this.pokemon = json)
    }
  },
  computed: {
    pokeFoto(){
      return this.pokemon.sprites.front_default
    },
    movimientos(){
       return this.pokemon.moves
    },
    habilidades(){
       return this.pokemon.abilities
    }
  }
}
</script>

<style>
.container{
  text-align: center;
}
ol{
 text-decoration: none;
 list-style: none;
}
label,h3{
  font-size: 20px;
  font-weight: bold
}
</style>
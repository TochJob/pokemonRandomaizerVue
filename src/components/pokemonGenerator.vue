<template>
    <div>
        <button @click="getPokemon()">generatePokemon</button>
        <div class="pokemonCard">
            <div class="pokemon__warapper">
                <div class="header">
                    <h1 class="pokemon__header">{{pokemon.name}}</h1>
                    <p class="pokemon__hp"><sub class="hp__desc">HP</sub> {{pokemonStat}}</p>
                </div>
                <img class="pokemon__image" :src="pokemonImage" alt="">
                <div class="pokemon__description">
                    <p>{{pokemonAbility}}</p>
                </div>
            </div>
        </div>

        <!-- <p>{{pokemon}}</p> -->
        
    </div>
</template>

<script>


export default {
   name:'pokemonGenerator',
   data() {
    return {
        pokemonAPI: 'https://pokeapi.co/api/v2/pokemon/',
        currentPokemon:1,
        currentPokemonId:'',
        pokemon:{},
        pokemonImage:'',
        pokemonAbility:'',
        pokemonStat:'',

    }
   },
   methods: {
    getPokemon(){
        this.currentPokemon = Math.floor(Math.random()*(700-1)+1)

        this.currentPokemonId = `${this.pokemonAPI}${this.currentPokemon}`
        fetch(this.currentPokemonId)
        .then(response => response.json())
        .then(data => this.pokemon = data)

        fetch('https://pokeapi.co/api/v2/stat/1/')
        .then(response => response.json())
        .then(data => console.log(data))

    }
   },

   updated(){
    this.pokemonImage = this.pokemon.sprites.front_default
    this.pokemonAbility = this.pokemon.abilities[0].ability.name
    this.pokemonStat = this.pokemon.stats[0].base_stat
    console.log();
    console.log(this.pokemon);

   }
   
}
</script>


<style scoped>
    *{
        margin: 0;
        padding: 0;
    }
    .header{
        background: linear-gradient(90deg, #5CD224 -1.29%, #4349CF 100%);
        display: flex;
        justify-content: space-around;
        border-radius: 15px 15px 0 0;
        padding: 15px 0;
    }
    .pokemonCard{
        width: 335px;
        /* height: 450px; */
        background: rgb(143, 101, 101);
        padding: 15px;
        
    }
    .pokemon__warapper{
        border: 10px solid #000;
        height: 100%;
        display: flex;
        flex-direction: column;
        justify-content: space-between;
        border-radius: 30px;
        box-sizing: border-box;
    }
    .pokemon__header{
        color: #000;
        text-align: left;
        font-size: 20px;
    }
    .pokemon__hp{
        color:#fff;
        font-weight: 700;
        font-size: 20px;
    }
    .pokemon__hp sub{
        font-size: 10px;
    }

    .pokemon__image{
        width: 100%;
    }

    .pokemon__description{
        background: linear-gradient(360deg, rgba(136, 6, 216, 0.65) 0%, rgba(252, 247, 255, 0) 100.5%);
        padding: 0px 0 70px;
        z-index: 0;
        position: relative;
        border-radius: 20px;
        font-weight: 700;
        font-size: 20px;
        text-shadow: rgb(255, 255, 255) 0px 0 3px;
    } 
</style>
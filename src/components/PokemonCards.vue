<template>
  <div class="cards">
 <cards v-for="pokemon in pokemons"
 :key="pokemon.id"
 :pokemons="pokemons"
 @click="click(pokemon)"
 :class="{opace: selectedId && pokemon.id !== selectedId }"
 class="card">
 <template v-slot:title>
  {{pokemon.name}} #{{ pokemon.id }}
  </template>
 <template v-slot:content>
  <img :src="pokemon.sprite" alt="pokemon sprite">
  </template>
   <template v-slot:description>
  <div v-for="type in pokemon.types" :key="type">
      {{ type }}
      </div>
  </template>
 </cards>
  </div>
</template>

<script>
import Cards from './Cards.vue'
export default {
 components : {
    Cards,
      },
props: {
    pokemons:{
        type:Array,
        default: []
    },
    selectedId :{
        type:Number,
        
    }
},
methods : {
    click(pokemon){
        this.$emit('chosen', pokemon)
    }
}

}
</script>

<style scoped>

.opace {
  opacity: 0.5;
}
.cards {
  display: flex;
  justify-content: center;
}
.card:hover {
  opacity: 1;
}
img {
  width:100%;
}
</style>
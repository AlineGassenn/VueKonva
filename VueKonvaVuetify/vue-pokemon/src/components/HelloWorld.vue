<template>
  <v-container>
    <center>
      <v-img max-height="12%" max-width="12%" :src="url"></v-img>
      <h1>{{ item.name }}</h1>
      <br />

      <ul id="habilidades">
        <li v-if="item.abilities">
          <b>Habilidades = {{ item.abilities.length }}</b>
        </li>
        <li
          v-for="itemAbility in item.abilities"
          :key="itemAbility.ability.name"
        >
          <b>{{ itemAbility.ability.name }}</b>
        </li>
      </ul>
      <br />
      <v-col class="row justify-around full-width" cols="12" sm="6">
        <v-text-field
          v-on:keyup.enter="getPokemon"
          outlined
          label="Informe o nome ou o id de um Pokémon"
          v-model="pokemon"
        ></v-text-field>
        <!-- <v-btn v-on:click="getPokemon" color="blue" dark x-large>
            Pesquisar
          </v-btn> -->
      </v-col>
    </center>
  </v-container>
</template>

<script>
import api from "../services/api";

export default {
  name: "HelloWorld",

  data() {
    return {
      url: "",
      pokemon: "pikachu",
      item: {},
    };
  },

  async beforeMount() {
    await this.getPokemon();
  },

  methods: {
    getPokemon() {
      api
        .get(`/pokemon/${this.pokemon}/`)
        .then((response) => {
          console.log(response);
          this.item = response.data;
          this.url = response.data.sprites.other.dream_world.front_default;
        })
        .catch((error) => {
          console.log(error);
        })
        .then(() => {});
    },
  },
};
</script>

<style>
#habilidades li {
  list-style: none;
}
</style>
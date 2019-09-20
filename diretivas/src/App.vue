<template>
  <div id="app">
    <input type="text" v-model="novaFruta" />
    <!-- <button v-on:click="inserirFruta">Inserir</button> -->
    <button @click="inserirFruta">Inserir</button>

    <p>Lista de frutas</p>
    <ul>
      <li v-for="fruta in frutas" :key="fruta.index">{{fruta}}</li>
    </ul>

    <p>Total: <b>{{totalFrutas}}</b></p>
  </div>
</template>

<script>
export default {
  name: "app",
  data() {
    return {
      frutas: [],
      novaFruta: "",
      totalFrutas: 0
    };
  },
  methods: {
    inserirFruta() {
      this.frutas.push(this.novaFruta)
      this.novaFruta = ''
      this.totalFrutas = this.frutas.length
    }
  }
};
</script>

<style>
</style>

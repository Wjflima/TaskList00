<template>
  <div id="app">
    <img width="25%" src="./assets/logo.png">
    <h1>Lista de Tarefas Simples</h1>
    <div>
      <input v-model="novaTarefa" placeholder="Adicionar uma nova tarefa">
      <button v-on:click="adicionar()">adicionar</button>
    </div>
    <div>
      <ul>
        <li v-for="({tarefa}, i) in lista" :key="tarefa" @click="remove(i)">{{tarefa}}</li>
        <button v-on:click="remove()">Apagar</button>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      lista: [{}],
      novaTarefa: ""
    };
  },
  methods: {
    adicionar() {
      this.lista.push({
        tarefa: this.novaTarefa
      });
      this.novaTarefa = "";
    },
    remove(i) {
      this.lista.splice(i, 1);
    }
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

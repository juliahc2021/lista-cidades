<template>
  <div class="container">
    <h2>{{ titulo }}</h2>
    <div class="input-group">
      <input @keyup.enter="adicionarCidade" v-model="novaCidade" type="text">
      <span class="input-group-btn">
        <button @click="adicionarCidade" class="btn btn-primary">Adicionar Cidade</button>
      </span>
    </div>
    <ul>
      <li 
        v-for="(cidade, index) in cidades" 
        :key="index" 
        :class="{ removed: cidade.checked }">

        <input type="checkbox" v-model="cidade.checked" />
        <label>{{ cidade.titulo }}</label>
      </li>
    </ul>
    <footer>
      <em>Altere aqui o título da sua lista de cidades</em>
      <input v-model="titulo" type="text">
    </footer>  
  </div>
</template>

<script>

export default {
  name: 'App',
  data() {
    return {
      titulo: "Lista de cidades",
      novaCidade: "",
      cidades: [
        { titulo: "Joinville", checked: false},
        { titulo: "Rio de Janeiro", checked: true},

      ]
    }

  },
  methods: {
    adicionarCidade() {
      this.cidades.push({
        titulo: this.novaCidade,
        checked: false,
      })
      this.novaCidade = "";
    }
  }
}
</script>

<style>
.container {
  width: 40%;
  margin: 20px auto 0px auto;
}

ul li {
  list-style: none;
}

.removed {
  color: gray;
}

.removed label {
  text-decoration: line-through;
}

</style>

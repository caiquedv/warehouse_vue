<template>
  <div>
    <h1>Cadastrar Galpão</h1>

    <div class="container">
      <div>{{ msg }}</div>

      <form v-on:submit.prevent>
        <div class="form">
          <label>Código: </label>
          <input type="text" placeholder="Código do galpão" v-model="form.code" />
        </div>

        <div class="form">
          <label>Nome: </label>
          <input type="text" placeholder="Nome do galpão" v-model="form.name" />
        </div>

        <div class="form">
          <label>Endereço: </label>
          <input
            type="text"
            placeholder="Endereço do galpão"
            v-model="form.address"
          />
        </div>

        <div class="form">
          <label>Cidade: </label>
          <input type="text" placeholder="Cidade" v-model="form.city" />
        </div>

        <div class="form">
          <label>Cep: </label>
          <input type="text" placeholder="Ceps" v-model="form.cep" />
        </div>

        <div class="form">
          <label>Área m²: </label>
          <input type="number" v-model="form.area" />
        </div>

        <div class="form">
          <label>Descrição: </label>
          <textarea cols="30" rows="5" v-model="form.description"></textarea>
        </div>

        <div class="form">
          <button v-on:click="postWarehouse">Cadastrar</button>
        </div>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  name: "WarehouseNew",

  data() {
    return {
      msg: null,
      form: {
        name: null,
        code: null,
        city: null,
        address: null,
        cep: null,
        area: null,
        description: null,
      },
    };
    this;
  },
  methods: {
    async postWarehouse() {
      try {
        await this.$http.post("http://localhost:2000/api/v1/warehouses", {        
          name: this.form.name,
          code: this.form.code,
          city: this.form.city,
          address: this.form.address,
          cep: this.form.cep,
          area: this.form.area,
          description: this.form.description,
        });
        this.msg = "Cadastrado com sucesso!";
      } catch (error) {
        this.msg = "Ops, tente novamente!";
        console.log(error);
      }
    },
  }
};
</script>

<style>
.form {
  margin-bottom: 15px;
}

.form input {
  margin: 5px;
}
</style>

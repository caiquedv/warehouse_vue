<template>
  <div>
    <h1>Galpões Cadastrados</h1>

    <input
      class="form"
      type="text"
      placeholder="Buscar galpão"
      v-model="term"
    />

    <div v-for="w in filterWarehouse" :key="w.id">
      <WareHouse
        :id="w.id"
        :name="w.name"
        :code="w.code"
        :address="w.address"
        :city="w.city"
        :area="w.area"
      />
    </div>
  </div>
</template>

<script>
import WareHouse from "../components/Warehouse.vue";

export default {
  name: "WarehouseList",
  components: {
    WareHouse,
  },
  data() {
    return {
      warehouses: [],
      term: "",
    };
  },
  mounted() {
    this.getWareHouses();
  },
  methods: {
    async getWareHouses() {
      const response = await this.$http.get(
        "http://127.0.0.1:2000/api/v1/warehouses"
      );

      const result = await response.json();

      console.log(result);

      this.warehouses = result;
      return this.warehouses;
    },
  },
  computed: {
    filterWarehouse() {
      return this.warehouses.filter((warehouse) => {
        return warehouse.name.toLowerCase().includes(this.term.toLowerCase());
      });
    },
  }
};
</script>

<style>
.form {
  margin-bottom: 20px;
}
</style>

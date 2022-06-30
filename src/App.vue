<template>
  <div>
    <ProductAdd @add:product="addProduct" />
    <ProductList
      @update:product="updateProduct"
      @delete:product="deleteProduct"
      :products="products"
    />
  </div>
</template>

<script>
import ProductList from "./components/ProductList.vue";
import ProductAdd from "./components/ProductAdd.vue";

export default {
  name: "App",
  components: {
    //componentler burda tanımlanır
    ProductList,
    ProductAdd,
  },
  data() {
    return {
      products: [],
    };
  },
  mounted() {
    this.getProducts();
  },
  methods: {
    async getProducts() {
      const result = await fetch("http://localhost:3000/products");
      const data = await result.json();
      this.products = data;
    },
    async deleteProduct(product) {
      await fetch("http://localhost:3000/products/" + product.id, {
        method: "DELETE",
      });
      this.getProducts()
    },
    async updateProduct(product) {
       await fetch(
        "http://localhost:3000/products/" + product.id,
        {
          method: "PUT",
          body: JSON.stringify(product),
          headers: { "Content-Type": "application/json" },
        }
      );
      this.getProducts()

    },
    async addProduct(product) {
       await fetch("http://localhost:3000/products", {
        method: "POST",
        body: JSON.stringify(product),
        headers: { "Content-Type": "application/json" },
      });

      this.getProducts()
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

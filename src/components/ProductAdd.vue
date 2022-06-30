<template>
  <div id="addForm">
    <form @submit.prevent="handleAdd" class="form-inline">
      <div class="form-group listxx">
        <label for="id">Id</label>
        <input v-model="product.id" type="text" class="form-control" id="id"/>
      </div>
      <div class="form-group listxx">
        <label for="productName">Ürün Adı</label>
        <input v-model="product.productName" type="text" class="form-control" id="productName"/>
      </div>
      <div class="form-group listxx">
        <label for="categoryId">Kategori</label>
        <input v-model="product.categoryId" type="text" class="form-control" id="categoryId"/>
      </div>
      <div class="form-group listxx">
        <label for="quantityPerUnit">Açıklama</label>
        <input v-model="product.quantityPerUnit" type="text" class="form-control" id="quantityPerUnit"/>
      </div>
      <div class="form-group listxx">
        <label for="unitPrice">Fiyat</label>
        <input v-model="product.unitPrice" type="text" class="form-control" id="unitPrice"/>
      </div>
      <div class="form-group listxx">
        <label for="unitsInStock">Stok Adedi</label>
        <input v-model="product.unitsInStock" type="text" class="form-control" id="unitsInStock"/>
      </div>
      <button type="submit" class="btn btn-sm btn-success">Ekle</button>
    </form>
  </div>
</template>
<script>
export default {
  name: "product-add",
  data() {
    return {
      product: {
        id: "",
        categoryId: "",
        productName: "",
        quantityPerUnit: "",
        unitPrice: "",
        unitsInStock: "",
      },
    };
  },
  methods:{
    handleAdd(){
        this.$emit("add:product",this.product)
    }
  }
};
</script>
<style scoped>
.form-inline {  
  display: flex;
  flex-flow: row wrap;
  align-items: center;
}
.form-inline label {
  margin: 5px 10px 5px 0;
}
.form-inline input {
  vertical-align: middle;
  margin: 5px 10px 5px 0;
  padding: 10px;
  background-color: #fff;
  border: 1px solid #ddd;
}
.form-inline button {
  padding: 10px 20px;
  background-color: dodgerblue;
  border: 1px solid #ddd;
  color: white;
  cursor: pointer;
}
@media (max-width: 800px) {
  .form-inline input {
    margin: 10px 0;
  }
  
  .form-inline {
    flex-direction: column;
    align-items: stretch;
  }
}

</style>
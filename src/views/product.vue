<template>
    <div>
        <h1>Product List</h1>
     
        <b-table striped hover :items="products" :fields="fields" :per-page="pageSize" :current-page="pageIndex"></b-table>
        <b-pagination align="center" size="md" :total-rows="products.length" :per-page="pageSize" v-model="pageIndex"></b-pagination>
       
    </div>
</template>


<script>
import axios from "axios";

export default {
  name: "productss",
  data() {
    return {
      message: "Retrieved ALL products",
      products: [],
      pageSize: 10,
      pageIndex: 1,
      fields: [
        {
          key: "product_id",
          sortable: true
          
        },
        {
          key: "product_name",
          sortable: true
        },
        {
          key: "units_in_stock",
          sortable: true
        },
        {
          key: "unit_price",
          sortable: true
        }
      ]
    };
  },
  mounted() {
    var instance = this;
    axios
      .get("https://gentle-island-33488.herokuapp.com/api/products/")
      .then(function(response) {
        console.log(response.data);
        instance.products = response.data.data;
      });
  }
};
</script>
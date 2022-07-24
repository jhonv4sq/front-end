<template>
  <div v-if="products.length" class="w-full flex justify-center flex-wrap ">
      <div class="w-5/6 flex flex-wrap justify-center gap-7 ">
        <div v-for="(product, i) in products" :key="i">
          <Card :id='product.id'/>
        </div>
      </div>
  </div>
  <div v-if="!products.length" class="w-full flex justify-center flex-wrap ">
      <Spinner />
  </div>
</template>

<script>
import axios from 'axios';
import Card from '../components/ProductCard.vue'
import Spinner from '../components/Spinner.vue'

export default {
  components:{
    Card,
    Spinner
  },
  data() {
    return {
      products: [],
    };
  },
  async created(){
    await axios.get('http://localhost:8000/api/products').then((result) => {
      this.products = result.data;
    });
  },
}
</script>


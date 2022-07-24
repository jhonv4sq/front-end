<template>
  <div>
    <div v-if="product.length" class="max-w-xs rounded-md overflow-hidden shadow-lg hover:scale-105 transition duration-500 cursor-pointer">
      <div class="w-80 h-44 bg-cover bg-center bg-no-repeat" :style="{backgroundImage:`url(${this.product[0].image})`}">
      </div>
      <div class="py-4 px-4 bg-white flex  flex-col gap-4">
        <h3 class="text-md font-semibold text-gray-600 text-center">{{ this.product[0].name }}</h3>

        <div class="w-full flex justify-between mt-8 font-normal  ">
          <p class="text-lg">€ {{ this.product[0].price }}</p>
          <p class="text-lg">Stock: {{ this.product[0].stock }}</p>
        </div>

        <button type="button" class="w-full bg-yellow-400 hover:bg-yellow-500 py-1 rounded font-semibold text-gray-800" @click.prevent="buy()">
            Buy Product
        </button>

        <button type="button" class="w-full bg-yellow-400 hover:bg-yellow-500 py-1 rounded font-semibold text-gray-800" @click.prevent="refund()">
            Refund Product
        </button>

      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  props:{
    id: Number,
  },
  data(){
    return {
      product:[],
    }
  },
  methods:{
    async show(){
      await axios.get(`http://localhost:8000/api/products/${this.id}`)
      .then((result) => {
          this.product[0] = result.data;
      })
    },

    async refund(){
      await axios.get(`http://localhost:8000/api/products/${this.id}/refund`)
      this.show();
    },

    async buy(){
      await axios.get(`http://localhost:8000/api/products/${this.id}/buy`);
      this.show();
    },
  },
  mounted(){
    this.show()
  }

}
</script>
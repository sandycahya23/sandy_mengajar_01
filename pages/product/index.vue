<template>
  <div>
    <h1>Product</h1>
    <hr>
    <ProductCard
      v-for="product in listProduct"
      :key="product.id"
      :data-product="product"
      @clickProductAmount="addProductAmount"
    />
    <div :class="subtotalClass">Subtotal: {{subtotal}}</div>
    <p>
      subtotal &lt; 5000 -> pink<br/>
      subtotal > 5000 -> red<br/>
      subtotal > 7000 -> green<br/>
      subtotal > 8000 -> blue
    </p>
    <div v-if="subtotal > 10000">hemat dong!!!</div>
    <div v-show="subtotal > 15000">Ayo hemat dong!!!</div>
  </div>
</template>
<script>
export default {
  name: 'PageProductA',
  data() {
    return {
      listProduct: [{
          id: 1,
          name: 'Product ABC',
          amount: 1,
          price: 1000,
        },{
          id: 2,
          name: 'Product ASD',
          amount: 1,
          price: 500,
        },
      ]
    };
  },
  computed: {
    subtotal() {
      let subtotal = 0;
      // for (let i = 0; i < this.listProduct.length; i+= 1) {
      //   subtotal += this.listProduct[i].amount * this.listProduct[i].price;
      // }
      // map -> return 
      /*
        [1,2,3] => [2,4,6]
        list.map(data => data * 2)
      */
      // forEach -> loop
      this.listProduct.forEach((product) => {
        subtotal += product.amount * product.price;
      });
      return subtotal;
    },
    subtotalClass() {
      // return {
      //   'bg-red-800': this.subtotal > 5000,
      //   'bg-green-800': this.subtotal > 7000,
      //   'bg-blue-800': this.subtotal > 8000,
      // };
      let bgClass = '';
      if (this.subtotal > 8000) {
        bgClass = 'bg-blue-800';
      } else if (this.subtotal > 7000) {
        bgClass = 'bg-green-800';
      } else if (this.subtotal > 5000) {
        bgClass = 'bg-red-800';
      } else {
        bgClass = 'bg-pink-300';
      }
      return bgClass;
    }
  },
  methods: {
    addProductAmount(id) {
      const product = this.listProduct.find(product => product.id ===id);
      product.amount += 1;
    },
  }
}
</script>

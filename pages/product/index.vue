<template>
  <div>
    <h1>Product</h1>
    <hr>
    <ProductCard
      v-for="product in listProduct"
      :key="product.id"
      :data-product="product"
    />
    <div>Subtotal: {{subtotal}}</div>
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
    }
  }
}
</script>

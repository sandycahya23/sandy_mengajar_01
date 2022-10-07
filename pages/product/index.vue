<template>
  <div>
    <h1>Product</h1>
    <hr>
    <ProductCard :data-product="product"/>
  </div>
</template>
<script>
export default {
  name: 'PageProductA',
  data() {
    return {
      product: {
          id: 1,
          name: 'Product ABC',
          amount: 1,
          price: 1000,
        },
    };
  },
}
</script>

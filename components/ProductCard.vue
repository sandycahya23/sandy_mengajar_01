<template>
  <div>
    <div>Nama: {{ dataProduct.name }}</div>
    <div>Jumlah: {{ dataProduct.amount }}</div>
    <div>Price: {{ dataProduct.price }}</div>
    <button @click="addAmount">Tambah Jumlah 1</button>
    <div>Total: {{ total }}</div>
    <!-- <div>Total + PPN {{ totalAfterPPn }}</div> -->
  </div>
</template>
<script>
export default {
  name: 'ProductCard',
  props: {
    dataProduct: {
      type: Object,
      default() {
        return {}
      },
    }
  },
  computed: {
    total() {
      return this.dataProduct.amount * this.dataProduct.price;
    },
    // PPN 10%
    // totalAfterPPn() {
    //   return Math.round(this.total * 1.1);
    // },
  },
  methods: {
    addAmount() {
      // eslint-disable-next-line vue/no-mutating-props
      this.dataProduct.amount += 1;
    }
  }
}
</script>

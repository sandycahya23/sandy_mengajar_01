<template>
  <div>
    <div>Nama: {{ dataProduct.title }}</div>
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
      this.$emit('clickProductAmount', this.dataProduct.id);
    }
  }
}
</script>

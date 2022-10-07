<template>
  <div>
    <div>Nama: {{ name }}</div>
    <div>Jumlah: {{ amount }}</div>
    <div>Price: {{ price }}</div>
    <button @click="addAmount">Tambah Jumlah 1</button>
    <div>Total: {{ total }}</div>
    <div>Total + PPN {{ totalAfterPPn }}</div>
  </div>
</template>
<script>
export default {
  name: 'ProductCard',
  data() {
    return {
      name: 'Product A',
      amount: 1,
      price: 1000,
    }
  },
  computed: {
    total() {
      return this.amount * this.price;
    },
    // PPN 10%
    totalAfterPPn() {
      return Math.round(this.total * 1.1);
    },
  },
  methods: {
    addAmount() {
      this.amount += 1;
    }
  }
}
</script>

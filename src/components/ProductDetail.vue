<template>
  <div class="product-details-wrapper">
    <div @click="closeModal">X</div>
    <img class="thumbnail" :src="photoName + '?w=170&&crop=10,10,-10,-10'" />
    <div class="item-details">
      <div class="item-name">{{ itemName }}</div>
      <div>ID: {{ itemId }}</div>
      <div>{{ formatPrice }}</div>
      <div>{{ description }}</div>
      <div>{{ dimensions }}</div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ProductDetail',
  props: {
    itemId: String,
    photoName: String,
    itemName: String,
    description: String,
    dimensions: String,
    basePrice: Number,
  },

  computed: {
    formatPrice() {
      return '$' + this.basePrice.toFixed(2);
    }
  },

  methods: {
    closeModal() {
      this.$emit('closeModal');
    }
  },
}
</script>

<style scoped>
.product-details-wrapper {
  position: fixed;
  width: 90vw;
  height: 90vh;
  top: 2rem;
  left: 3rem;
  background: white;
  border: 1px solid black;
  border-radius: 15px;
  transition: all .5s;
}
</style>

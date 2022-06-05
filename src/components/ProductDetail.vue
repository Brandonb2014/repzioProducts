<template>
  <div class="product-details-wrapper">
    <div class="close" @click="closeModal">X</div>
    <img class="thumbnail" :src="photoName + '?crop=10,10,-10,-10'" />
    <div class="item-details">
      <div class="item-name">{{ itemName }}</div>
      <div>ID: {{ itemId }}</div>
      <div>{{ formatPrice }}</div>
      <div>{{ description }}</div>
      <div>Dimensions: {{ dimensions }}</div>
      <img class="logo" alt="Logo" :src="logo" />
      <RepContact
        :salesRep="salesRep"
        :itemId="itemId"
      ></RepContact>
    </div>
  </div>
</template>

<script>
import RepContact from './/RepContact.vue';

export default {
  name: 'ProductDetail',
  components: {
    RepContact,
  },
  props: {
    itemId: String,
    photoName: String,
    itemName: String,
    description: String,
    dimensions: String,
    basePrice: Number,
    salesRep: Object,
    logo: String,
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

<style lang="scss">
@import "../mixins/variables.scss";
.product-details-wrapper {
  position: fixed;
  top: 0;
  bottom: 0;
  left: 0.313rem;
  right: 0.313rem;
  background: white;
  border: 1px solid black;
  border-radius: 0.938rem;
  transition: all .5s;
  display: flex;
  flex-direction: column;
  padding-top: 0.938rem;

  @media (min-width: $screen-xs) {
    flex-direction: row;
  }

  .thumbnail {
    width: 5rem;
    height: 5rem;

    @media (min-width: $screen-xs) {
      width: 10rem;
      height: 10rem;
    }

    @media (min-width: $screen-sm) {
      width: 16.25rem;
      height: 16.25rem;
    }

    @media (min-width: $screen-md) {
      width: 22.5rem;
      height: 22.5rem;
    }
  }

  .logo {
    width: 5rem;
    height: 5rem;
  }

  .close {
    position: absolute;
    right: 0.625rem;
    top: 0.625rem;
    font-size: 0.8331rem;
    cursor: pointer;

    &:hover {
      font-weight: bold;
    }
  }

  .item-details {
    display: flex;
    flex-direction: column;

    .item-name {
      font-weight: bold;
    }
  }
}
</style>

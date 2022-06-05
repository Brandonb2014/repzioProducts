<template>
  <div class="item-wrapper" @click="showDetail = !showDetail">
    <img class="thumbnail" :src="photoName + '?crop=10,10,-10,-10'" />
  </div>

  <ProductDetail
    v-show="showDetail"
    v-on:closeModal="closeModal()"
    :itemId="itemId"
    :photoName="photoName"
    :itemName="itemName"
    :description="description"
    :dimensions="dimensions"
    :basePrice="basePrice"
    :salesRep="salesRep"
    :logo="logo">
  </ProductDetail>
</template>

<script>
import ProductDetail from './ProductDetail.vue';

export default {
  name: 'ProductListItem',
  components: {
    ProductDetail
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

  data() {
    return {
      showDetail: false,
    }
  },

  methods: {
    closeModal() {
      this.showDetail = false;
    }
  },
}
</script>

<style lang="scss">
@import "../mixins/variables.scss";

.item-wrapper {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
  max-width: 90%;
  height: 13.625rem;
  margin: 0.313rem;
  padding: 0.313rem;
  cursor: pointer;
  border: 0.063rem solid transparent;
  border-radius: 0.938rem;
  transition: all .5s;
      
  @media (min-width: $screen-xs) {
    max-width: 40%;
  }
      
  @media (min-width: $screen-md) {
    max-width: 30%;
  }
      
  @media (min-width: $screen-lg) {
    max-width: 15%;
  }

  &:hover {
    border: 0.063rem solid black;
  }

  .thumbnail {
    max-height: 100%;
    max-width: 100%;
  }
}



</style>

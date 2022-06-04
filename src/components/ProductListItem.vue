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
    :basePrice="basePrice">
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
.item-wrapper {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
  height: 100%;
  margin: 15px 0;
  cursor: pointer;
  border: 1px solid transparent;
  border-radius: 15px;
  transition: all .5s;

  &:hover {
    border: 1px solid black;
  }
}
.thumbnail {
  width: 80px;
  max-height: 200px;
}



@media (min-width: 525px) {
  .thumbnail {
    max-width: 210px;
  }
}
</style>

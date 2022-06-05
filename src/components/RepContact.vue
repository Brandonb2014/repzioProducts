<template>
  <div id="rep-contact" v-if="salesRep">
    <span v-if="salesRep && SalesRepName && message && !itemId" class="rep-message-wrapper">
      <span v-html="message" class="message"></span>
      <div class="signature">-{{ SalesRepName }}</div>
    </span>
    <div v-else-if="salesRep && SalesRepName && !itemId">
      <div><span class="bold">Your Sales Rep:</span> {{ SalesRepName }}</div>
    </div>
    <div v-else-if="salesRep && itemId">
      <span>Do you want this product?<br />Contact me to get this ordered</span>
    </div>
    <div v-if="salesRep && salesRep.EmailAddress">
      <i class="fa-solid fa-envelope"></i>
      &nbsp;<a :href="'mailto:' + salesRep.EmailAddress">{{ salesRep.EmailAddress }}</a>
    </div>
    <div v-if="salesRep && salesRep.Phone">
      <i class="fa-solid fa-mobile-screen-button"></i>
      &nbsp;<a :href="'tel:' + salesRep.Phone">{{ salesRep.Phone }}</a>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ProductDetail',
  props: {
    salesRep: Object,
    message: String,
    itemId: String,
  },

  computed: {
    SalesRepName() {
      if (this.salesRep && this.salesRep.FirstName && this.salesRep.LastName) {
        return this.salesRep.FirstName + ' ' + this.salesRep.LastName;
      }
      return '';
    }
  },
}
</script>

<style  lang="scss">
@import "../mixins/variables.scss";

#rep-contact {
  background: white;
  margin: 0.188rem;
  padding: 0.313rem;
  border-radius: 0.563rem;

  .rep-message-wrapper {
    display: flex;
    flex-direction: column;

    .message {
      color: $secondary-font-color;
      font-family: "Comic Sans MS";

      p {
        margin: 0;
      }
    }
    .signature {
      align-self: flex-end;
    }
  }
}
</style>

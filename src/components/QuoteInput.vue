<template>
  <div class="col-lg-8">
    <h2 class="text-white">Quote</h2>
    <textarea class="form-control" rows="6" v-model="quote"> </textarea>
    <button
      class="btn btn-primary btn-lg btn-block submit-btn"
      @click="addQuote"
    >
      Add Quote
    </button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      quote: ""
    };
  },
  methods: {
    addQuote() {
      this.$emit("addToQuoteList", this.quote);
      this.quote = "";
    }
  }
};
</script>

<style scoped>
.submit-btn {
  margin-top: 10px;
}
</style>

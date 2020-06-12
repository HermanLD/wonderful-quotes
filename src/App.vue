<template>
  <div class="container">
    <div class="row">
      <div class="col-sm-12">
        <h1 class="text-white text-center pb-5">WONDERFUL QUOTES</h1>
      </div>
    </div>
    <div class="row">
      <progress-bar :quoteStorage="quoteCount"> </progress-bar>
    </div>
    <hr />
    <div class="row justify-content-md-center">
      <quote-input @addToQuoteList="toList($event)"> </quote-input>
    </div>
    <div
      class="row row-cols-xs-1 row-cols-sm-2 row-cols-md-4 justify-content-md-center py-5"
    >
      <quote-display
        v-for="(quote, index) in quoteList"
        :key="index"
        :index="index"
        @removedQuote="fromList($event)"
      >
        <div class="card-body">{{ quote.txt }}</div>
      </quote-display>
    </div>
    <footer class="alert alert-info" role="alert">
      CLICK ON QUOTE TO DELETE
    </footer>
  </div>
</template>

<script>
import Progress from "./components/ProgressBar.vue";
import Input from "./components/QuoteInput.vue";
import Quote from "./components/Quote.vue";

export default {
  data() {
    return {
      quoteList: []
    };
  },
  methods: {
    toList(quoteTxt) {
      if (this.quoteCount < 10) {
        this.quoteList.push({ txt: quoteTxt });
      } else {
        alert("Storage full. Delete some Quotes");
        console.log(this.quoteCount);
      }
    },
    fromList(selectedQuote) {
      this.quoteList.splice(selectedQuote, 1);
    }
  },
  computed: {
    quoteCount() {
      return this.quoteList.length;
    }
  },
  components: {
    ProgressBar: Progress,
    QuoteInput: Input,
    QuoteDisplay: Quote
  }
};
</script>

<style>
body {
  padding-top: 80px;
  background-color: #330033;
  background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='264' height='264' viewBox='0 0 800 800'%3E%3Cg fill='none' stroke='%23404' stroke-width='3.1'%3E%3Cpath d='M769 229L1037 260.9M927 880L731 737 520 660 309 538 40 599 295 764 126.5 879.5 40 599-197 493 102 382-31 229 126.5 79.5-69-63'/%3E%3Cpath d='M-31 229L237 261 390 382 603 493 308.5 537.5 101.5 381.5M370 905L295 764'/%3E%3Cpath d='M520 660L578 842 731 737 840 599 603 493 520 660 295 764 309 538 390 382 539 269 769 229 577.5 41.5 370 105 295 -36 126.5 79.5 237 261 102 382 40 599 -69 737 127 880'/%3E%3Cpath d='M520-140L578.5 42.5 731-63M603 493L539 269 237 261 370 105M902 382L539 269M390 382L102 382'/%3E%3Cpath d='M-222 42L126.5 79.5 370 105 539 269 577.5 41.5 927 80 769 229 902 382 603 493 731 737M295-36L577.5 41.5M578 842L295 764M40-201L127 80M102 382L-261 269'/%3E%3C/g%3E%3Cg fill='%23505'%3E%3Ccircle cx='769' cy='229' r='10'/%3E%3Ccircle cx='539' cy='269' r='10'/%3E%3Ccircle cx='603' cy='493' r='10'/%3E%3Ccircle cx='731' cy='737' r='10'/%3E%3Ccircle cx='520' cy='660' r='10'/%3E%3Ccircle cx='309' cy='538' r='10'/%3E%3Ccircle cx='295' cy='764' r='10'/%3E%3Ccircle cx='40' cy='599' r='10'/%3E%3Ccircle cx='102' cy='382' r='10'/%3E%3Ccircle cx='127' cy='80' r='10'/%3E%3Ccircle cx='370' cy='105' r='10'/%3E%3Ccircle cx='578' cy='42' r='10'/%3E%3Ccircle cx='237' cy='261' r='10'/%3E%3Ccircle cx='390' cy='382' r='10'/%3E%3C/g%3E%3C/svg%3E");
}
</style>

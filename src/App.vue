<template>
  <div class="container">
    <app-header :quoteCount="quoteCounter" :maxQuotes="maxQuotes"></app-header>
    <app-new-quote @quoteAdded="newQuote"></app-new-quote>
    <app-quote-grid :quotes="quotes" @quoteDeleted="deleteQuote"></app-quote-grid>
    <div class="row">
      <div class="col-sm-12 text-center">
        <div class="alert alert-info">Info: Click on a Quote to delete it!</div>
      </div>
    </div>
  </div>
</template>

<script>
import QuoteGrid from './components/QuoteGrid';
import NewQuote from './components/NewQuote';
import Header from './components/Header';

export default {
  data() {
    return {
      maxQuotes: 10,
      quotes: ["Just a Quote to see something"]
    };
  },
  components: {
    'appQuoteGrid': QuoteGrid,
    'appNewQuote': NewQuote,
    'appHeader': Header
  },
  computed: {
    quoteCounter() {
      return this.quotes.length;
    }
  },
  methods: {
    newQuote(quote) {
      if (this.quotes.length == this.maxQuotes) {
        alert('Please Delete Quotes first!');
      } else {
        this.quotes.push(quote);
      }
    },
    deleteQuote(index) {
      this.quotes.splice(index, 1);
    }
  },
};
</script>

<style>
</style>

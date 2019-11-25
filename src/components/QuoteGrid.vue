<template>
    <div class="row">
        <app-quote v-for="(quote, index) in quotes" :key="quote" @click.native="deleteQuote(index)">
            <p slot="quote">{{ quote }}</p>
        </app-quote>
    </div>
</template>

<script>
import Quote from './Quote';
export default {
    props: ['quotes'],
    components: {
        'appQuote': Quote
    },
    methods: {
        deleteQuote(index) {
            this.$emit('quoteDeleted', index);
        }
    },
}
</script>
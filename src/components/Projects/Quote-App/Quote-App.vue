<template>
    <div class="component-container">
      <section>
        <app-header :quoteCount="quotes.length" :maxQuotes="maxQuotes"></app-header>

        <app-new-quote @quoteAdded="newQuote"></app-new-quote>

        <app-quote-grid :quotes="quotes" @quoteDeleted="deleteQuote"></app-quote-grid>

        <div class="row">
            <div class="col-sm-12 text-center">
                <div class="alert alert-info">Info: Click on a Quote to delete it!</div>
            </div>
        </div>
      </section>
    </div>
</template>

<script>
    import QuoteGrid from './QuoteGrid.vue';
    import NewQuote from './NewQuote.vue';
    import Header from './Header.vue';

    export default {
        data: function () {
            return {
                quotes: [
                    'Just a Quote to see something'
                ],
                maxQuotes: 10
            }
        },
        methods: {
            newQuote(quote) {
                if (this.quotes.length >= this.maxQuotes) {
                    return alert('Please delete Quotes first!');
                }
                this.quotes.push(quote);
            },
            deleteQuote(index) {
                this.quotes.splice(index, 1);
            }
        },
        components: {
            appQuoteGrid: QuoteGrid,
            appNewQuote: NewQuote,
            appHeader: Header
        }
    }
</script>

<style>
</style>

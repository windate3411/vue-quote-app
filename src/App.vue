<template>
  <v-app>
    <v-content>
      <v-container>
        <NewQuote @addQuote="updateQuotes" />
        <v-divider></v-divider>
        <v-row>
          <Quote v-for="(item,index) in quotes" :key="index">
            <p class="quote">{{item}}</p>
          </Quote>
        </v-row>
        <v-divider></v-divider>
      </v-container>
    </v-content>
  </v-app>
</template>

<script>
import Quote from './components/Quote.vue';
import NewQuote from './components/NewQuote.vue';

export default {
  name: 'App',

  components: {
    Quote, NewQuote
  },

  data: () => ({
    quotes: ['This is A quote', 'This is Another quote'],
    maxQuotes: 10
  }),
  methods: {
    updateQuotes(quote) {
      this.quotes.push(quote)
    }
  },
};
</script>

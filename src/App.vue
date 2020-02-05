<template>
  <v-app>
    <v-content>
      <v-snackbar v-model="snackbar" top timeout="3000">
        {{ text }}
        <v-btn color="pink" text @click="snackbar = false">Close</v-btn>
      </v-snackbar>
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
    maxQuotes: 10,
    snackbar: false,
    text: 'You have added a new quote',
  }),
  methods: {
    updateQuotes(quote) {
      this.quotes.push(quote)
      this.snackbar = true
    }
  },
};
</script>

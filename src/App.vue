<template>
  <v-app>
    <v-content>
      <!-- add header -->
      <Header></Header>
      <!-- add a progress bar -->
      <v-progress-linear :value="progress" color="red"></v-progress-linear>
      <!-- snackbar for message shown -->
      <v-snackbar v-model="snackbar" top timeout="3000">
        {{ text }}
        <v-btn color="pink" text @click="snackbar = false">Close</v-btn>
      </v-snackbar>
      <!-- quote container -->
      <v-container>
        <NewQuote @addQuote="updateQuotes" />
        <v-divider></v-divider>
        <v-row>
          <Quote v-for="(item,index) in quotes" :key="index" @click.native="deleteQuote(index)">
            <p class="quote">{{item}}</p>
          </Quote>
        </v-row>
        <v-divider></v-divider>
        <!-- add use hint -->
        <v-alert type="info">Click on a quote to delete it. You can have up to 10 quotes</v-alert>
      </v-container>
    </v-content>
  </v-app>
</template>

<script>
import Quote from './components/Quote.vue';
import NewQuote from './components/NewQuote.vue';
import Header from './components/Header.vue';

export default {
  name: 'App',

  components: {
    Quote, NewQuote, Header
  },

  data: () => ({
    quotes: ['This is A quote', 'This is Another quote'],
    maxQuotes: 10,
    snackbar: false,
    text: ''
  }),
  computed: {
    progress() {
      return (this.quotes.length * 10).toString()
    }
  },
  methods: {
    updateQuotes(quote) {
      this.snackbar = true
      // check if user reach 10 quotes
      if (this.quotes.length === this.maxQuotes) {
        this.text = 'You can\'t have any more quotes'
      } else {
        this.quotes.push(quote)
        this.text = 'You have added a new quote'
        this.progress = parseInt(this.progress) + 10
      }
    },
    deleteQuote(index) {
      this.quotes.splice(index, 1)
      this.text = 'You have deleted a quote'
      this.progress = parseInt(this.progress) - 10
    }
  },
};
</script>

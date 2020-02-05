<template>
  <v-row>
    <v-col cols="12" sm="8" offset-sm="2" md="6" offset-md="3">
      <v-form class="text-center" ref="form">
        <v-textarea label="Quote" hint="Enter your quote" v-model="quote" :rules="quoteRules"></v-textarea>
        <v-btn
          small
          rounded
          @click.prevent="creatNew"
          color="orange accent-2"
          class="font-italic font-weight-bold"
        >
          <v-icon left>mdi-plus</v-icon>
          <span>Add quote</span>
        </v-btn>
      </v-form>
    </v-col>
  </v-row>
</template>


<script>
export default {
  data() {
    return {
      quote: '',
      quoteRules: [
        v => !!v || 'Quote is required',
        v => (v && v.length >= 10) || 'Quote must be greater than 10 characters',
      ],
    }
  },
  methods: {
    creatNew() {
      if (this.$refs.form.validate()) {
        this.$emit('addQuote', this.quote)
        this.quote = ''
        this.$refs.form.resetValidation()
      }
    }
  },
}
</script>
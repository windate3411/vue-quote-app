<template>
  <v-row>
    <v-col cols="12" sm="8" offset-sm="2" md="6" offset-md="3">
      <v-form class="text-center">
        <v-textarea label="Quote" hint="Enter your quote" v-model="quote"></v-textarea>
        <v-btn small @click.prevent="creatNew">
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
      quote: ''
    }
  },
  methods: {
    creatNew() {

    }
  },
}
</script>
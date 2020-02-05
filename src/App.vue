<template>
  <v-app>
    <v-content>
      <Quote />
    </v-content>
  </v-app>
</template>

<script>
import Quote from './components/Quote.vue';

export default {
  name: 'App',

  components: {
    Quote,
  },

  data: () => ({
    //
  }),
};
</script>

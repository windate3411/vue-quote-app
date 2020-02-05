<template>
  <v-col cols="12" sm="6" md="3">
    <v-card height="100%" class="text-center">
      <v-card-text>
        <slot></slot>
      </v-card-text>
    </v-card>
  </v-col>
</template>

<script>
export default {
  props: ['quotes']
}
</script>

<style lang="scss">
@import url("https://fonts.googleapis.com/css?family=Arizonia&display=swap");

.quote {
  font-family: "Arizonia", sans-serif;
  font-size: 24px;
  color: #6e6e6e;
  &:hover {
    cursor: pointer;
    transform: scale(1.1);
  }
  margin-top: 10px;
}
</style>
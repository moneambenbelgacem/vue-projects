<template lang="">
  <div>
    <v-app-bar
      color="amber darken-1
 accent-4"
      dense
      dark
      fixed
    >
      <v-toolbar-title>Bright Coding</v-toolbar-title>

      <v-spacer></v-spacer>

      <v-toolbar-items class="hidden-sm-and-down">
        <v-btn text v-for="item in menu" dark>{{ item.title }}</v-btn>
      </v-toolbar-items>
    </v-app-bar>
  </div>
</template>
<script>
export default {
  data() {
    return {
      menu: [
        { id: 1, title: 'Admin' },
        { id: 2, title: 'Cours' },
        { id: 3, title: 'F&Q' },
      ],
    };
  },
  methods: {},
};
</script>
<style lang=""></style>

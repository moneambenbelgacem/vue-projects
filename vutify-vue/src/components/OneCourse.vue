<template lang="">
  <v-card class="mx-auto " max-width="250">
    <v-img :src="course.image" height="150px"></v-img>

    <v-card-title>
      {{ course.title }}
    </v-card-title>

    <v-card-text>
      Lorem ipsum dolor sit amet consectetur.
    </v-card-text>
    <v-card-actions>
      <v-btn @click="deleteone(course.id)" color="red darken-1" text>
        Delete
      </v-btn>
      <v-btn color="grey darken-1" text>
        {{ course.categorie }}
      </v-btn>
    </v-card-actions>
    <hr />
    <v-chip
      class="ma-2"
      color="red"
      text-color="white"
      x-small
      v-for="tag in course.tags"
    >
      {{ tag }}
    </v-chip>
  </v-card>
</template>
<script>
export default {
  props: ['course'],
  methods: {
    deleteone(id) {
      this.$emit('deleteOneCourse', id);
    },
  },
};
</script>
<style lang=""></style>

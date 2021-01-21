<template>
  <div>
    <template>
      <v-form ref="form" v-model="valid" lazy-validation>
        <v-text-field
          v-model="title"
          :counter="10"
          :rules="titleRules"
          label="title"
          required
        ></v-text-field>

        <v-text-field
          v-model="image"
          :rules="imageRules"
          label="ImageUrl"
          required
        ></v-text-field>

        <v-select
          v-model="select"
          :rules="[(v) => !!v || 'Item is required']"
          label="Your categorie"
          :items="categories"
          required
        ></v-select>

        <v-radio-group v-model="row" row>
          <v-radio label="Free" value="Free"></v-radio>
          <v-radio label="Payant" value="Payant"></v-radio>
        </v-radio-group>
        <h5>Tags</h5>
        <div class="form-check" v-for="tag in tags">
          <input
            class="form-check-input"
            type="checkbox"
            :value="tag"
            v-model="myTags"
          />
          <label class="form-check-label"> {{ tag }} </label>
        </div>

        <v-btn color="success" class="mr-4" @click="add">
          Add Course
        </v-btn>
      </v-form>
    </template>
  </div>
</template>
<script>
export default {
  data: () => ({
    valid: true,
    title: '',
    titleRules: [(v) => !!v || 'title is required'],
    image: '',
    imageRules: [(v) => !!v || 'Image is required'],
    select: '',
    myTags: [],

    row: '',
    tags: ['Front-end', 'Back-end', 'Full-stack', 'Mobile'],
    categories: ['Front-end', 'Back-end', 'Full-stack', 'Mobile'],
  }),

  methods: {
    add() {
      let title = this.title;
      let image = this.image;
      let id = Math.random(100);

      const course = {
        id,
        title,
        image,
        categorie: this.select,
        tags: this.myTags,
      };
      this.$emit('addcourse', course);
      this.$refs.form.reset();
    },
  },
};
</script>
<style lang=""></style>

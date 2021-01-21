<template>
  <div>
    <v-row v-if="verif">
      <v-col md="6" class="mx-auto">
        <AddCourse @addcourse="addOneCourse($event)" />
      </v-col>
    </v-row>

    <v-row>
      <v-flex md="4">
        <h1>Liste Of Courses</h1>
      </v-flex>
      <v-flex class="md-8" align-self="end" v-if="deleted">
        <v-alert border="top" color="red lighten-2" class="text-center" dark>
          Course is deleted !!!
        </v-alert>
      </v-flex>
      <v-flex class="md-8" align-self="end" v-if="added">
        <v-alert border="top" color="green" class="text-center" dark>
          Course is Added !!!
        </v-alert>
      </v-flex>
    </v-row>
    <v-row>
      <v-col md="10">
        <v-breadcrumbs :items="items" divider="-"></v-breadcrumbs>
      </v-col>
      <v-col md="2">
        <v-btn
          @click="newCourse"
          class="my-3 small"
          rounded
          :class="{ success: !verif, 'orange darken-4': verif }"
        >
          {{ verif ? 'Close' : 'New' }}
        </v-btn>
      </v-col>
    </v-row>
    <v-row>
      <div v-for="course in courses" :key="course.id" class="ma-1 ml-6">
        <OneCourse :course="course" @deleteOneCourse="deleteOne($event)" />
      </div>
    </v-row>
  </div>
</template>
<script>
import OneCourse from './OneCourse.vue';
import AddCourse from './AddCourse';
export default {
  methods: {
    deleteOne(id) {
      this.courses = this.courses.filter((course) => course.id != id);
      this.deleted = true;
      setTimeout(() => {
        this.deleted = false;
      }, 3000);
    },
    addOneCourse(course) {
      this.courses = [course, ...this.courses];
      this.verif = !this.verif;
      this.added = true;
      setTimeout(() => {
        this.added = false;
      }, 3000);
    },
    newCourse() {
      this.verif = !this.verif;
    },
  },
  components: {
    OneCourse,
    AddCourse,
  },
  data: () => ({
    courses: [
      {
        id: 1,
        title: 'learn vue 3',
        image:
          'https://process.fs.teachablecdn.com/ADNupMnWyR7kCWRvm76Laz/resize=width:705/https://www.filepicker.io/api/file/k7Fltx5ITbu9LI6VtgTS',
        categorie: 'FrameworkOne',
        tags: [],
      },
      {
        id: 2,
        title: 'learn ReactJs ',
        image:
          'https://process.fs.teachablecdn.com/ADNupMnWyR7kCWRvm76Laz/resize=width:705/https://www.filepicker.io/api/file/C2oT8I1eTXGg69ytJ69f',
        categorie: 'Framework',
        tags: [],
      },
      {
        id: 3,
        title: 'learn Symfony',
        image:
          'https://process.fs.teachablecdn.com/ADNupMnWyR7kCWRvm76Laz/resize=width:705/https://www.filepicker.io/api/file/DH3y1mfjS6qLVQp1uOtO',
        categorie: 'Framework',
        tags: [],
      },
      {
        id: 4,
        title: 'learn GitHub',
        image:
          'https://process.fs.teachablecdn.com/ADNupMnWyR7kCWRvm76Laz/resize=width:705/https://www.filepicker.io/api/file/evNSVH9RSjW0um2vBYW9',
        categorie: 'Framework',
        tags: [],
      },
      {
        id: 5,
        title: 'learn JavaScript',
        image:
          'https://process.fs.teachablecdn.com/ADNupMnWyR7kCWRvm76Laz/resize=width:705/https://www.filepicker.io/api/file/H9QyEOsSLG05qNb2kC0V',
        categorie: 'Framework',
        tags: [],
      },
      {
        id: 6,
        title: 'learn Spring Boot',
        image:
          'https://process.fs.teachablecdn.com/ADNupMnWyR7kCWRvm76Laz/resize=width:705/https://www.filepicker.io/api/file/5miGPBu8RbCSc4hCzN39',
        categorie: 'Framework',
        tags: [],
      },
    ],
    items: [
      {
        text: 'Dashboard',
        disabled: false,
        href: 'breadcrumbs_dashboard',
      },
      {
        text: 'Listes Courses',
        disabled: false,
        href: 'breadcrumbs_link_1',
      },
    ],
    verif: false,
    deleted: false,
    added: false,
  }),
};
</script>
<style lang=""></style>

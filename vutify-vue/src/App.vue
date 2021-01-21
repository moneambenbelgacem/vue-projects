<template>
  <v-app>
    <Header />
    <v-container class="cont">
      <v-col class=" mx-auto  " md="9">
        <Courses />
      </v-col>
    </v-container>
    <Footer />
  </v-app>
</template>

<script>
import Header from './components/Header.vue';
import Courses from './components/Courses.vue';
import Footer from './components/Footer.vue';
export default {
  components: {
    Header,
    Courses,
    Footer,
  },
  name: 'App',

  data: () => ({
    message: 'hello mon3em',
  }),
};
</script>
<style>
.cont {
  margin-top: 60px;
}
</style>

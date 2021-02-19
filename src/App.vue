<template>
  <v-app>
    <v-app-bar
      app
    >
   <a href="https://github.com/paul-asvb/vuetify-form-example">go to code</a>
    </v-app-bar>

    <v-main>
      <HelloWorld/>
    </v-main>
  </v-app>
</template>

<script>
import HelloWorld from './components/HelloWorld';

export default {
  name: 'App',

  components: {
    HelloWorld,
  },

  data: () => ({
    //
  }),
};
</script>

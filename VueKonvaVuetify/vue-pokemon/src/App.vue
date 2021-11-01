<template>
  <v-app>
     <v-img
      :src="require('./assets/logo.png')"
      class="my-3"
      contain
      height="180"
    />
      
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

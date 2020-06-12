<template>
  <v-app>
    <v-content>
      <router-view/>
    </v-content>
  </v-app>
</template>

<script>
import {mapState} from 'vuex'

export default {

  name: 'App',

  components: {
  },

  data: () => ({
    //
  }),
  computed: {

  }
};
</script>

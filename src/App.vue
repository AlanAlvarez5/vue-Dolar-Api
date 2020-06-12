<template>
  <v-app>
    <v-content>
      <router-view/>
      <v-dialog
        v-mode="loading.estado"
        hide-overlay
        persistent
        width="300"
      >
        <v-card
          color="primary"
          dark
        >
          <v-card-text>
            {{loading.titulo}}
            <v-progress-linear
              indeterminate
              color="white"
              class="mb-0"
            >
            </v-progress-linear>
          </v-card-text>
        </v-card>
      
      </v-dialog>
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
    ...mapState(['loading']),
  }
};
</script>

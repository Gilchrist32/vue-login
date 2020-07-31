<template>
  <div :class="mode ? 'welcome': 'darkness'">
    <v-card>
      <v-app-bar
       absolute 
      :color="mode ? ' success white--text' : ''"
      elevate-on-scroll
      :dark="mode ? false : true"
      >
      <v-toolbar-title>
        MeetUp
      </v-toolbar-title>

      <v-spacer></v-spacer>

      <v-tooltip bottom>
        <template v-slot:activator="{ on }">
          <v-btn class="white--text mr-2"
          depressed
          :color="mode ? 'success white--text' : ''"
          v-on="on"
          to="/">
          <v-icon left class="white--text">mdi-home</v-icon>
          Home
          </v-btn>
          </template>
      </v-tooltip>

          <v-btn
          class="white--text"
          depressed
          :color="mode ? 'success white--text' : ''"
          to="/login">
          <v-icon left>mdi-login</v-icon>
          Login
          </v-btn>
      </v-app-bar>
    </v-card>
  </div>
</template>
<script>
import { mapState } from 'vuex'
export default {

  computed: {
        ...mapState(['mode'])
    },
}
</script>

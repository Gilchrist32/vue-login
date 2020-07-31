<template>
  <v-app>
     <v-app-bar
       absolute 
      :color="mode ? 'success white--text' : ''"
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
    <v-content>
      <v-container class="fill-height" fluid>
        <v-row align="center" justify="center">
          <v-col cols="12" sm="8" md="8">
            <v-card class="elevation-12">
              <v-window v-model="step">
                 <v-window-item :value="2" class="mt-16">
                  <v-row class="fill-height">
                    <v-col cols="12" md="4" class="success">
                      <v-card-text class="white--text">
                        <h1 class="text-center display-1">Welcome Back !</h1>
                        <h5 class="text-center">To Keep connected with us please login with your personnel info</h5>
                      </v-card-text>
                      <div class="text-center">
                        <v-btn v-for="link in event" :key="link.title" router :to="link.route" 
                        rounded outlined dark @click="step--">
                        <v-icon left>{{ link.icons }}</v-icon><span>{{ link.title }}</span>
                        </v-btn>
                      </div>
                    </v-col>
                    <v-col cols="12" md="8">
                      <v-card-text class="mt-10">
                        <h1 class="text-center display-2 teal--text text--accent-3">Create Account</h1>
                        <div class="text-center mt-4">
                           <v-btn class="mx-2" fab color="black" outlined>
                            <v-icon>fab fa-facebook-f</v-icon>
                          </v-btn>
                          <v-btn class="mx-2" fab color="black" outlined>
                            <v-icon>fab fa-instagram</v-icon>
                          </v-btn>
                          <v-btn class="mx-2" fab color="black" outlined>
                            <v-icon>fab fa-github</v-icon>
                          </v-btn>
                          <v-btn class="mx-2" fab color="black" outlined>
                            <v-icon>fab fa-google-plus-g</v-icon>
                          </v-btn>  
                        </div>
                        <h4 class="text-center mt-4">Ensure your email for registation</h4>
                        <v-form>
                          <v-text-field 
                            label="Firstname"
                            name="firstname"
                            prepend-icon="person"
                            type="text"
                            color="teal accent-3"
                          />
                          <v-text-field 
                            label="Lastname"
                            name="lastname"
                            prepend-icon="person"
                            type="text"
                            color="teal accent-3"
                          />
                          <v-text-field 
                            label="Email"
                            name="Email"
                            :rules="[required('Email'), emailRules('Email')]"
                            v-model="email"
                            autocomplete="off"
                            prepend-icon="email"
                            type="text"
                            color="teal accent-3"
                          />
                          <v-text-field
                            id="password"
                            label="Password"
                            name="Password"
                            v-model="password"
                            :rules="[required('Password')]"
                            autocomplete="off"
                            prepend-icon="lock"
                            type="password"
                            color="teal accent-3"
                           />
                        </v-form>
                      </v-card-text>
                      <div class="text-center mt-n5">
                        <v-btn rounded color="teal accent-3" dark>SIGN UP</v-btn>
                        <v-btn rounded color="teal accent-3" dark>CANCEL</v-btn>
                      </div>
                    </v-col>
                  </v-row>
                </v-window-item>
              </v-window>
            </v-card>
          </v-col>
        </v-row>
      </v-container>
    </v-content>
  </v-app>
</template>
<script>
import { mapState } from 'vuex' 
import { required, emailRules } from '@/utils/validationRules'

export default {
  name: 'Create',
  
  data: () => ({
    step: 1,
    firstname: '',
    lastname: '',
    email: '',
    password: '',
    loading: false,
      event: [
        { icons: 'accessibility', title: 'SIGN IN', route: '/login'}
      ],
          valid: true,
          required(propertyType) { 
          return required(propertyType)
      },
      emailRules(propertyType) {
          return emailRules(propertyType)
      },
  }),
  props: {
    source: String
  },

  computed: {
    ...mapState(['mode'])
  },
}
</script>
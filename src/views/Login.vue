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
                <v-window-item :value="1">
                  <v-row>
                    <v-col cols="12" md="8">
                      <v-card-text class="mt-12">
                        <h1 class="text-center display-2 teal--text text--accent-3">Sign in</h1>
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
                        <h4 class="text-center mt-4">Ensure your email for registration</h4>
                        <v-form>
                          <v-text-field
                            label="Email Address"
                            name="Email"
                            prepend-icon="email"
                            type="text"
                            color="teal accent-3"
                           />
                           <v-text-field
                            id="password"
                            label="Password"
                            name="Password"
                            prepend-icon="lock"
                            type="password"
                            color="teal accent-3"
                            />
                        </v-form>
                        <h3 class="text-center mt-3">Forgot your password</h3>
                      </v-card-text>
                      <div class="text-center mt-3">
                        <v-btn rounded color="success" dark>SIGN IN</v-btn>
                      </div>
                    </v-col>
                    <v-col cols="12" md="4" class="success">
                      <v-card-text class="white--text mt-12">
                        <h1 class="text-center display-1">!Hello, Friends !</h1>
                        <h5 class="text-center">Enter your personnel details and start journey with us</h5>
                      </v-card-text>
                      <div class="text-center">
                        <v-btn rounded outlined dark @click="step++">CREAtE ACCOUNT</v-btn>
                      </div>
                    </v-col>
                  </v-row>
                </v-window-item>
                <v-window-item :value="2" class="mt-12">
                  <v-row class="fill-height">
                    <v-col cols="12" md="4" class="success">
                      <v-card-text class="white--text mt-12">
                        <h1 class="text-center display-1">Welcome Back !</h1>
                        <h5 class="text-center">To Keep connected with us please login with your personnel info</h5>
                      </v-card-text>
                      <div class="text-center">
                        <v-btn rounded outlined dark @click="step--">SIGN IN</v-btn>
                      </div>
                    </v-col>
                    <v-col cols="12" md="8">
                      <v-card-text class="mt-12">
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
                            name="Firstname"
                            prepend-icon="person"
                            type="text"
                            color="teal accent-3"
                          />
                          <v-text-field 
                            label="Lastname"
                            name="Lastname"
                            prepend-icon="person"
                            type="text"
                            color="teal accent-3"
                          />
                          <v-text-field 
                            label="Email"
                            name="Email"
                            prepend-icon="email"
                            type="text"
                            color="teal accent-3"
                          />
                          <v-text-field
                            id="password"
                            label="Password"
                            name="Password"
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
export default {
  name: 'Login',
  
  data: () => ({
    step: 1
  }),
  props: {
    source: String
  },

  computed: {
    ...mapState(['mode'])
  },
}
</script>
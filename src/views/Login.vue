<template>
  <div>
    <Signin />
  </div>
</template>
<script>
import Signin from '../components/user/Signin'
import { mapState } from 'vuex' 
import { required, emailRules } from '../utils/validationRules'
export default {
  name: 'Login',
  components: {
    Signin,
  },
  
  data: () => ({
    step: 1,
    firstname: '',
    lastname: '',
    email: '',
    password: '',
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
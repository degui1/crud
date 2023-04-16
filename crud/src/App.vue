<template>
  <v-app>
    <v-app-bar
      app
      dark
    >
      <div class="d-flex align-center">
        <span class="text-h5">CRUD</span>
      </div>

      <v-spacer></v-spacer>

      <v-btn
        text
        @click="() => {
          link('table');
        }"
      >
        <span class="mr-2" v-if="login===true">tabela de users</span>
      </v-btn>

      <v-btn
        text
        @click="() => {
          link('login')
        }"
      >
        <span class="mr-2" v-if="login===true">Logout</span>
        <span class="mr-2" v-if="login===false">Login</span>
        
      </v-btn>
    </v-app-bar>

    <v-main>
      <router-view/>
    </v-main>
  </v-app>
</template>

<script>
export default {
  name: 'App',

  data() {
    return {
      login: true,
    }
  },

  methods: {
    link(parm){
      if (parm === 'login') {
        switch (this.login) {
        case true:
          this.login = false
          this.$router.push('/')
          break;
        case false:
          this.login = true 
          this.$router.push('/login')
          break;
      }
      } else if (parm === 'table') {
        this.$router.push('/table')
      }
    }
  }
};
</script>

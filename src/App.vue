<template>
  <v-app>
    <v-toolbar app>
      <v-spacer></v-spacer>
      <v-toolbar-title>
        <span class="font-weight-light">Asiacommerce</span>
      </v-toolbar-title>
    </v-toolbar>
    <v-content>
      <HelloWorld/>
    </v-content>
  </v-app>
</template>

<script>
import HelloWorld from './components/HelloWorld';

export default {
  name: 'App',
  components: {
    HelloWorld
  },
  data () {
    return {
      //
    }
  }
}
</script>

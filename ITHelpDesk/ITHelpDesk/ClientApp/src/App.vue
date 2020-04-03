<template>
  <v-app>
    <v-app-bar app color="primary" dark extension="true" >
      <div class="d-flex align-center">
        <v-img
          alt="Vuetify Logo"
          class="shrink mr-2"
          contain
          :src="require('./assets/template.png')"
          transition="scale-transition"
          width="100"
        />
      </div>
      <v-spacer>{{ date }}</v-spacer>
      <v-btn
        href="https://github.com/vuetifyjs/vuetify/releases/latest"
        target="_blank"
        text
      >
        <span class="mr-2">Latest Release</span>
        <v-icon>mdi-open-in-new</v-icon>
      </v-btn>

      <template v-slot:extension>
        <v-tabs
          centered
          slider-color="secondary"
        >
          <v-tab
            v-for="i in 3"
            :key="i"
            :href="`#tab-${i}`"
          >
            Item {{ i }}
          </v-tab>
        </v-tabs>
      </template>
          

    </v-app-bar>

    <v-content >
      <HelloWorld />
    </v-content>
  </v-app>
  
</template>

<script lang="ts">
import Vue from "vue";
import HelloWorld from "./components/HelloWorld.vue";
import moment from 'moment';
import 'moment/locale/zh-tw';

export default Vue.extend({
  name: "App",

  components: {
    HelloWorld
  },

  data: function () {
    return {
      date: ''
    }
  },
  
  methods: {
    time: function () {
      this.date = moment().format('MMMM Do YYYY, h:mm:ss a');
    }
  },

  mounted(){
    this.time();
    setInterval(this.time,1000);
  }
});

</script>

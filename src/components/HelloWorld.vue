<template>
  <v-app id="inspire">
    <v-navigation-drawer
    :mini-variant.sync="mini"
    v-model="drawer"
    hide-overlay
    stateless
    fixed
    dark
    pa-1
  >
    <v-toolbar flat class="transparent">
      <v-list class="pa-0">
        <v-list-tile avatar>
          <v-list-tile-avatar>
            <img src="../assets/logoasia.png">
          </v-list-tile-avatar>

          <v-list-tile-content>
            <v-list-tile-title></v-list-tile-title>
          </v-list-tile-content>

          <v-list-tile-action>
            <v-btn
              icon
              @click.stop="mini = !mini"
            >
              <v-icon>chevron_left</v-icon>
            </v-btn>
          </v-list-tile-action>
        </v-list-tile>
      </v-list>
    </v-toolbar>

    <v-list class="pt-0" dense>
      

      <v-list-tile
        v-for="item in items"
        :key="item.title"
        click=""
      >
        <v-list-tile-action>
          <v-icon>{{ item.icon }}</v-icon>
        </v-list-tile-action>

        <v-list-tile-content>
          <v-list-tile-title>{{ item.title }}</v-list-tile-title>
        </v-list-tile-content>
      </v-list-tile>
    </v-list>
  </v-navigation-drawer>
      <v-container>
        <v-layout v-for="prod in products" :key="prod.title">
          <v-flex  sm3, pa-1>
            <v-card>
              <v-img
              :src="prod.attachment"
              aspect-ratio="2.75"
              ></v-img>
                <v-card-title primary-title>
                  <div>
                    <h3 class="headline mb-0">{{ prod.title.rendered }}</h3>
                      <div>Located two hours south of Sydney in the <br>Southern Highlands of New South Wales, ...</div>
                  </div>
                </v-card-title>
                <v-card-actions>
                  <v-btn flat color="orange">Share</v-btn>
                  <v-btn flat color="orange">Explore</v-btn>
                </v-card-actions>
            </v-card>
          </v-flex>
        </v-layout> 
      </v-container>
  </v-app>
  
</template>

<script>
  export default {
    data () {
      return {
        drawer: true,
        items: [
          { title: 'Home', icon: 'dashboard' },
          { title: 'About', icon: 'question_answer' }
        ],
        mini: true,
        right: null,
        products: []
      }
    },
        created: function(){
          this.$http.get('https://asiacommerce.net/wp-json/wp/v2/product/').then(response => 
            {
            for (const product in response.data){
              this.products.push(response.data[product]);
             }
            },error => {
              alert(error);
            });
          
          }
  }
</script>
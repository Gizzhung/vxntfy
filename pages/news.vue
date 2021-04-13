<template>
  <section class="container">
    <div >
          <H1 width="100%" height="auto"  style="margin-bottom=10px">熱門排行</H1>
    </div>
    <v-row justify="center"
      no-gutters>
      
      
      
          <v-card

            class="pa-3"
            tile
            outlined
            max-width="430px"
            v-for="article in articles" :key="article.id"
            style="border-bottom:2px solid "
          >
          <div target="_blank" v-for="(item,idx) in article.media" :key="idx">        
              <v-img
                class="white--text align-end"
                height="100px"
                width="100px"
                style="margin:15px "
                :src="item['media-metadata'][0].url"
              >
              </v-img>
          </div>
          
              <v-card-title style="font-weight:bold">{{ article.title }}</v-card-title>
            

            <v-card-subtitle class="pb-0">
              {{article.published_date }}
            </v-card-subtitle>

            <v-card-text class="text--primary" style="margin-top:15px" >
              {{article.abstract }}
            </v-card-text>

            <v-card-actions>
              <v-btn
                color="orange"
                text
                :href="article.url"
                target="_blank"
              >
                GO LooK
              </v-btn>

              
            </v-card-actions>
          </v-card>
     
    </v-row>
    
    
    <!-- <div v-for="article in articles" :key="article.id">
      <p>{{ article.title }}</p>     
      <div  target="_blank" v-for="(item,idx) in article.media" :key="idx">        
        <img :src="item['media-metadata'][0].url" alt />
      </div>
    </div> -->
  </section>
   
</template>
<script>
import axios from 'axios'
export default {

  data() {
    return {
      articles: [],
      mediaart: [],
    };
  },
  // Axios({
  //     url : url,
  //     articles : data,
  // }).then(res => {
  //     resolve(res.data)
  // }).catch( error => {

  // }),
  mounted() {
   this.fetchSomething();
  
  },
  methods: {
     async fetchSomething() {
        const data = await this.$axios.$get('https://api.nytimes.com/svc/mostpopular/v2/viewed/7.json?api-key=d4QSQpGoGKHoRUaYpiIxDuq4AxBDn0Ms')
        console.log(data)
        this.articles = data.results;

        console.log(this.articles)
        
        // this.mediaart = data.results.media.media-metadata
        // console.log(Object.keys(this.articles).length)
        // this.artlengths =this.articles.size()
        
    },
 
    // size(Object){
    //   Object.size = function(obj) {
    //     var size = 0,
    //       key;
    //     for (key in obj) {
    //       if (obj.hasOwnProperty(key)) size++;
    //     }
    //     return size;
    //   };
    // }



  },


};
</script>
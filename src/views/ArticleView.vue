<script>
import axios from 'axios';

export default {
  name: 'ArticleView',
  data() {
    return {
      todos_list: [],
    };
  },
  mounted() {
    this.get_article();
  },
  methods: {
    get_article() {
      const apiKey = import.meta.env.VITE_APP_API_KEY
      const headers = {
        "Content-Type": "application/json",
        "X-MICROCMS-API-KEY": apiKey
      }
      const url = 'https://em3vfr548v.microcms.io/api/v1/blog'
      axios.get(url, { headers: headers}).then(response => {
        if (response.status === 200) {
          console.log(response.data)
        }
      }).catch(error => {
        console.log(error)
      });

    }
  }
};


</script>

<template>
  <div class="about">
    <h2>
      #Article
    </h2>
    <div class="content-box">
      <div class="article-box">
        <v-card
            class="mx-auto my-4"
            title="心理的安全性を高めるための実践"
            subtitle="投稿日 : 2023年12月1日"
            text="心理的安全性とは..."
            variant="tonal"
            link>
        </v-card>
      </div>
      <div class="article-box">
        <v-card
            class="mx-auto my-4"
            title="心理的安全性を高めるための実践"
            subtitle="投稿日 : 2023年12月1日"
            text="心理的安全性とは..."
            variant="tonal"
            link>
        </v-card>
      </div>
    </div>
  </div>
</template>


<style>
@media (min-width: 1024px) {
  .about {
    width: 800px;
    margin: 0 auto;
    padding-top: 20px;
    padding-right: 10px;
    padding-left: 10px;
  }


}
</style>

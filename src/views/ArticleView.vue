<script>
import axios from 'axios';
import dayjs from "dayjs";

export default {
  name: 'ArticleView',
  data() {
    return {
      articleList: [],
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
      axios.get(url, {headers: headers}).then(response => {
        if (response.status === 200) {
          console.log(response.data)
          this.articleList = response.data.contents
          console.log(this.articleList)
        }
      }).catch(error => {
        console.log(error)
      });
    },
    formatDate(dateString) {
      return dayjs(dateString).format('YYYY-MM-DD');
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
        <ul>
          <li v-for="(value) in articleList" :key="value.id">
            <v-card
                class="mx-auto my-4"
                :title="value.title"
                :subtitle="formatDate(value.publishedAt)"
                :text="value.description"
                variant="tonal"
                link>
            </v-card>
          </li>
        </ul>
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

  li {
    list-style: none;
  }


}
</style>

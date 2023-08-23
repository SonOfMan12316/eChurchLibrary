<template>
  <div class="events">
    <div class="events-content p-6 sm:p-8 lg:p-16 xl:p-20 bg-white">
      <div class="features-head flex flex-row justify-between">
        <div>
          <h2
            class="text-red-700 text-xl lg:text-2xl xl:text-3xl font-semibold mb-1 font-serif"
          >
            Upcoming Events
          </h2>
          <div class="line"></div>
        </div>
        <!-- <div class="jo flex flex-row justify-end items-center -mt-1">
                    <h1 class="font-serif font-normal text-tiny sm:text-base lg:text-xl">View All</h1>
                    <Arrow/>
                </div> -->
      </div>
      <div>
        <!-- <Search
                class="mt-2"
                v-on:newsChanged="getNews"
                /> -->
      </div>
      <EventsContent
        v-for="newsArticle in filteredItems"
        :key="newsArticle.index"
        :data="newsArticle"
      />
    </div>
  </div>
</template>

<script>
import Arrow from "../components/Arrow.vue";
import EventsContent from "../components/EventsContent.vue";
import SecSearchButton from "../components/SecSearchButton.vue";
import axios from "axios";
// import Search from '../components/Search.vue'

export default {
  components: {
    Arrow,
    EventsContent,
    SecSearchButton,
    // Search
  },
  data() {
    return {
      articles: [],
    };
  },
  methods: {
    // getNews(query) {
    //     var that = this
    //     var url = 'https://newsapi.org/v2/everything?' +
    //     'q=' + query + '&' +
    //     'apiKey=03e626f76f9b41428758fc7202e3a169';
    //     var req = new Request(url);
    //     fetch(req)
    //     .then(function(response) {
    //         return response.json();
    //     })
    //     .then(function(data) {
    //         that.articles = data.articles;
    //         console.log(data)
    //     })
    // }
    async fetchData() {
      let res = await axios
        .get(
          "https://newsapi.org/v2/everything?q=bitcoin&apiKey=03e626f76f9b41428758fc7202e3a169"
        )
        .then((res) => {
          console.log(res.data.articles);
          this.articles = res.data.articles;
        })
        .catch((error) => {
          console.error(error.message);
        });
    },
  },
  computed: {
    filteredItems() {
      return this.articles.filter((article) => {
        return article.description.length > 200;
      });
    },
  },
  created() {
    // this.getNews();
    this.fetchData();
    // console.log('created')
    // console.log(this.searchQ, 'created2');
  },
  // mounted() {
  //     this.getNews(this.searchQ);
  //     console.log(this.searchQ, 'mounted');
  // }
};
</script>

<style scoped>
.line {
  content: "";
  display: block;
  width: 40px;
  height: 4px;
  border: 1px solid #ca0609;
  background-color: #ca0609;
  border-radius: 10px;
}

h1 {
  letter-spacing: -0.02em;
  color: rgba(0, 0, 0, 0.56);
}

@media (min-width: 768px) {
  .jo {
    width: 15%;
  }
}

@media (min-width: 1024px) {
  .jo {
    width: 30%;
  }

  .features-head {
    width: 98%;
  }
}

@media (min-width: 1200px) {
  .features-head {
    width: 98%;
  }
}
</style>

<template>
  <div class="event-content mt-8">
    <div class="flex flex-col sm:flex-row gap-y-4 sm:gap-x-4 sm">
      <div class="jo sm:mt-2" @click="reloadPage">
        <img :src="data.urlToImage" loading="lazy" />
      </div>
      <div class="content flex flex-col">
        <a :href="data.url">
          <div class="content1 flex flex-row justify-between">
            <div>
              <h2
                class="text-lg sm:text-xl lg:text-2xl font-bold font-serif text-black"
              >
                {{ data.title }}
              </h2>
            </div>
            <div class="flex flex-row items-center mt-1">
              <p class="para font-serif text-tiny sm:text-base">
                {{ data.published_at }}
              </p>
            </div>
          </div>
          <h1 class="font-serif font-medium text-base xl:mb-1">
            {{ data.author }} || {{ data.source.name }}
          </h1>
          <h1 class="font-serif font-medium text-base xl:mb-1">
            {{ data.description }}
          </h1>
        </a>
      </div>
    </div>
  </div>
</template>

<script>
// import { DateFilter } from '../Filters/date'
import formatUnix from "../DateFormat";
export default {
  props: ["data"],
  data() {
    return {};
  },
  setup() {
    return {
      formatUnix,
    };
  },
  methods: {
    reloadPage() {
      window.location.reload();
    },
  },
  // computed: {
  //     reduceParagraph() {
  //         if(this.data.description.length > 10) {
  //             return this.data.description.slice(0, 9)
  //         }
  //         return this.data.description
  //     }
  // }
};
</script>

<style scoped>
h2,
h1,
p {
  letter-spacing: -0.02em;
}

h1 {
  color: rgba(0, 0, 0, 0.53);
}

p {
  color: rgba(0, 0, 0, 0.5);
}

.jo {
  cursor: pointer;
}

@media (min-width: 640px) {
  .para {
    width: 100%;
  }

  .jo {
    width: 45%;
  }

  .jo img {
    width: 100%;
    height: 10rem;
  }

  .content {
    width: 100%;
  }
}

@media (min-width: 1024px) {
  .jo img {
    height: 9.5rem;
  }

  .content1 {
    width: 98%;
  }
}

@media (min-width: 1200px) {
  .jo {
    width: 25%;
  }

  .last-para {
    width: 100%;
  }
}
</style>

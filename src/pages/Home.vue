<template>
  <div class="home-page">
    <div class="banner">
      <div class="container">
        <h1 class="logo-font">
          conduit
        </h1>
        <p>A place to share your knowledge.</p>
      </div>
    </div>

    <div class="container page">
      <div class="row">
        <div class="col-md-9">
          <Suspense>
            <template #default>
              <ArticlesList
                use-global-feed
                use-my-feed
                use-tag-feed
              />
            </template>
            <template #fallback>
              Articles are downloading...
            </template>
          </Suspense>
        </div>

        <div class="col-md-3">
          <div class="sidebar">
            <Suspense>
              <template #default>
                <PopularTags />
              </template>
              <template #fallback>
                Popular tags are downloading...
              </template>
            </Suspense>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

import ArticlesList from '../components/ArticlesList.vue'
import PopularTags from '../components/PopularTags.vue'

export default defineComponent({
  name: 'HomePage',
  components: {
    ArticlesList,
    PopularTags,
  },
})
</script>

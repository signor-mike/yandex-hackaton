<template>
  <v-main>
    <div class="cats text-center">
      <div class="d-flex">
        <v-icon class="mx-2" large color="header" @click="$router.go(-1)"
          >mdi-arrow-left
        </v-icon>
        <h3>
          {{ types.description }}
        </h3>
      </div>
      <iframe
        :title="types.description"
        allowfullscreen="true"
        :src="types.link"
        width="100%"
        height="600px"
      ></iframe>
      <v-btn color="button"
        ><a :href="types.link" target="_blank"
          >Открыть в новой вкладке</a
        ></v-btn
      >
    </div>
  </v-main>
</template>

<script>
export default {
  async asyncData({ $content, route }) {
    const categories = await $content(
      route.path.substr(-1) === '/'
        ? route.path.slice(1, -1)
        : route.path.substring(1)
    ).fetch()
    const types = await categories[0]
    return {
      types,
    }
  },
  computed: {
    randomId() {
      return Math.floor(Math.random() * 100)
    },
  },
  mounted() {
    //
  },
}
</script>

<style></style>

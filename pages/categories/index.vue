<template>
  <v-main>
    <div class="cats">
      <h1>Категории</h1>
      <v-row>
        <v-col v-for="cat in cats" :key="cat.id" cols="3">
          <Item :item="cat" width="auto" height="250" description="" />
        </v-col>
      </v-row>
    </div>
  </v-main>
</template>

<script>
import Item from '~/components/Item.vue'
export default {
  components: { Item },
  async asyncData({ $content, route }) {
    const categories = await $content(
      route.path.substr(-1) === '/'
        ? route.path.slice(1, -1)
        : route.path.substring(1)
    ).fetch()
    const cats = categories[0].categories
    return {
      cats,
    }
  },
  computed: {
    link() {
      return this.$route.path.substr(-1) === '/'
        ? this.$route.path.slice(1, -1)
        : this.$route.path.substring(1)
    },
  },
  beforeMount() {
    // console.log(this.$route.path)
    // console.log(this.$route.path.substring(1))
    // console.log(this.$route.path.substring(0, 2))
    // console.log(this.link)
  },
  methods: {
    // {
  },
}
</script>

<style scoped></style>

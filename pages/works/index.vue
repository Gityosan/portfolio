<template>
  <v-card flat class="d-flex flex-column layout">
    <v-card class="ma-5 pa-0" color="transparent" flat width="100%">
      <v-card-title class="font-weight-bold text-h3">Works</v-card-title>
    </v-card>
    <v-row class="mx-9 pa-0">
      <v-card
        v-for="item in works"
        :key="item.title"
        class="mr-5 mb-5"
        outlined
        :to="item.url"
      >
        <v-card-title class="font-weight-bold text-h6">
          {{ item.title }}
        </v-card-title>
      </v-card>
    </v-row>
  </v-card>
</template>
<script>
export default {
  data: () => ({
    works: [
      {
        title: '簡易タイピングゲーム',
        url: '/works/typing-game'
      },
      {
        title: 'Lit+GrapesJsの簡易HTMLビルダーアプリ',
        url: 'https://main.d2xvgc55woftez.amplifyapp.com/'
      },
      {
        title: 'go-webassemblyの電卓アプリ',
        url: 'https://main.d3usnbgonskc6w.amplifyapp.com/'
      },
      {
        title: 'LitとViteを使ったストップウォッチアプリ',
        url: 'https://stopwatch.d1k5vwj8k5chym.amplifyapp.com/'
      }
    ]
  })
}
</script>
<style lang="scss" scoped>
.layout {
  width: 100vw;
  max-width: 1024px;
  margin: 0 auto;
}
</style>

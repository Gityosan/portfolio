<template>
  <v-card flat class="d-flex flex-column mx-10 mt-5">
    <v-card class="ma-5 pa-0" color="transparent" flat width="100%">
      <v-card-title class="font-weight-bold text-h3">
        Typing Game
        <v-spacer></v-spacer>
        <v-btn icon to="/works" height="40" width="40" depressed>
          <v-icon size="28">mdi-arrow-left</v-icon>
        </v-btn>
      </v-card-title>
    </v-card>
    <v-row class="mx-9 my-5 pa-0">
      <v-btn class="mr-2" outlined @click="reset()">before</v-btn>
      <v-btn class="mr-2" outlined @click="start(60)">palying</v-btn>
      <v-btn outlined @click="status = 'afterPlay'">after</v-btn>
    </v-row>
    <v-card
      v-if="status === 'beforePlay'"
      flat
      outlined
      class="mx-9 my-5 pa-0 d-flex flex-column"
    >
      <v-card-title>コース選択</v-card-title>
      <v-btn class="mx-5 my-2" outlined @click="start(60)">初級(1分)</v-btn>
      <v-btn class="mx-5 my-2" outlined @click="start(120)">中級(2分)</v-btn>
      <v-btn class="mx-5 my-2" outlined @click="start(180)">上級(3分)</v-btn>
    </v-card>

    <v-card
      v-else-if="status === 'playing'"
      flat
      outlined
      class="mx-9 my-5 pa-0 d-flex flex-column"
    >
      <v-row class="mx-5 my-0">
        <v-card-title>残り{{ limit - timer }}秒</v-card-title>
        <v-spacer></v-spacer>
        <v-card-title>正解数：{{ correct }}</v-card-title>
      </v-row>
      <v-card-title class="text-h3 text-bold mx-auto my-5">
        {{ answer || 'ここに問題文が入ります' }}
      </v-card-title>
      <v-text-field
        v-model.trim="input"
        outlined
        class="mx-5"
        @change="check()"
      ></v-text-field>
    </v-card>

    <v-card v-else flat outlined class="mx-9 my-5 pa-0 d-flex flex-column">
      <v-card-title>{{ correct }}問正解しました！</v-card-title>
      <v-btn class="mx-5 my-2" outlined @click="reset()">はじめに戻る</v-btn>
    </v-card>
  </v-card>
</template>
<script>
export default {
  data: () => ({
    // status = ['beforePlay','playing','afterPlay']
    status: 'beforePlay',
    correct: 0,
    input: null,
    answer: null,
    questions: [
      'タイピングゲーム作成会',
      'トラボルタカスタム',
      '穏やかじゃないですね',
      '楽園放浪',
      '夜の自販機',
      'アヤカシライダー',
      'バケモノバッター',
      'ドーナツホール',
      '九龍レトロ',
      'カラフルボンバーズ',
      '全てあなたのせいです',
      'パンダヒーロー',
      'アプリコット',
      'レセプション',
      'どんぐりず'
    ],
    limit: 0,
    timer: 0,
    interval: null
  }),
  methods: {
    setQuestion() {
      // 入力欄を空にする
      this.input = ''
      // 次の問題をセットする
      const index = Math.floor(Math.random() * this.questions.length)
      this.answer = this.questions[index]
      console.log(index, this.questions[index])
      // 1行で書くと、こう
      // this.answer =
      // this.questions[Math.floor(Math.random() * this.questions.length)]
    },
    start(time = null) {
      this.setQuestion()
      this.status = 'playing'
      if (time) {
        this.limit = time
        const startTime = new Date()
        this.interval = setInterval(
          function () {
            if (time - 1 <= this.timer) {
              clearInterval(this.interval)
              this.status = 'afterPlay'
            }
            this.timer = Math.floor((new Date() - startTime) / 1000)
          }.bind(this),
          1000
        )
      }
    },
    check() {
      console.log('s')
      if (this.answer === this.input) {
        // 正解数を１プラスする
        this.correct += 1
        this.setQuestion()
      }
    },
    reset() {
      this.status = 'beforePlay'
      this.correct = 0
      this.input = null
      this.answer = null
      this.limit = 0
      this.timer = 0
      if (this.interval) {
        clearInterval(this.interval)
        this.interval = null
      }
    }
  }
}
</script>

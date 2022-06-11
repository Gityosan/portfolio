<template>
  <v-card flat>
    <v-card class="ma-5 pa-0" color="transparent" flat width="100%">
      <v-card-title class="font-weight-bold text-h3">
        IIHARA HODAKA.com
      </v-card-title>
    </v-card>
    <v-card class="ma-5 pa-0" color="transparent" flat width="100%">
      <v-card-title class="font-weight-bold text-h4">
        About<v-icon class="ml-2" color="black">mdi-arrow-right</v-icon>
      </v-card-title>
      <nuxt-link to="/works" class="text-decoration-none">
        <v-card-title class="font-weight-bold text-h4">
          Works<v-icon class="ml-2" color="black">mdi-arrow-right</v-icon>
        </v-card-title>
      </nuxt-link>

      <v-card-title class="font-weight-bold text-h4">
        Study<v-icon class="ml-2" color="black">mdi-arrow-right</v-icon>
      </v-card-title>
    </v-card>
    <!-- <v-row class="ma-5 justify-center">
      <span class="word">I</span>
      <button
        :class="[{ pressed: pressed, unpressed: !pressed }]"
        @click="pressed = !pressed"
      >
        <v-icon size="30">mdi-plus</v-icon>
      </button>
      <span class="word mr-2">You</span>
      <v-icon size="30" color="black">mdi-equal</v-icon>
      <div class="word mr-2">You</div>
    </v-row> -->
  </v-card>
</template>
<script>
export default {
  data: () => ({
    pressed: false
  })
}
</script>
<style lang="scss" scoped>
.word {
  font-size: 50px;
}

.pressed {
  width: 40px;
  height: 40px;
  padding: 5px;
  margin: 17.5px 10px 17.5px 17.5px;
  background-color: red;
  border-radius: 50%;

  & > i {
    color: white;
  }
}

.unpressed {
  width: 40px;
  height: 40px;
  padding: 5px;
  margin: 17.5px 10px 17.5px 17.5px;
  background-color: transparent;
  border-radius: 50%;

  & > i {
    color: white;
  }

  &:hover {
    background-color: #ccc;

    & > i {
      color: #ccc;
    }
  }
}
</style>

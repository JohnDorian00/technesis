<template>
  <v-app>
    <v-main>
      <div class="main">
        <!--        На весь экран с выравниванием по левому краю-->
        <div class="main__row">
          <TagList :tags="tags" :align="'left'"></TagList>
        </div>
        <!--        На весь экран с выравниванием по ширине-->
        <div class="main__row">
          <TagList :tags="tags" :align="'width'"></TagList>
        </div>
        <!--        На половину экрана с выравниванием по левому краю-->
        <div class="main__row main__row_is-half">
          <TagList :tags="tags" :align="'left'"></TagList>
        </div>
        <!--        На половину экрана с выравниванием по ширине-->
        <div class="main__row main__row_is-half">
          <TagList :tags="tags" :align="'width'"></TagList>
        </div>
      </div>
    </v-main>
  </v-app>
</template>

<script>
import TagList from "@/components/TagList.vue";

export default {
  name: "App",
  components: {
    TagList,
  },
  data() {
    return {
      tags: [],
      icons: [
        "airplane",
        "antenna",
        "baby-face",
        "basketball",
        "bus-clock",
        "duck",
        "drupal",
        "halloween",
        "power-sleep",
      ],
    };
  },
  beforeMount() {
    // 7 записей со случайным появлением иконок
    for (let i = 1; i < 8; i++) {
      let tag = { text: "Текст" + i };

      if (Math.floor(Math.random() * 2) === 0) {
        tag.icon = this.icons[Math.floor(Math.random() * this.icons.length)];
      }

      this.tags.push(tag);
    }
  },
};
</script>

<style lang="scss">
html {
  overflow: hidden !important;
}

#app {
  height: 100%;
  padding: 0;
  margin: 0;
}

.main {
  @extend #app;
  display: flex;
  flex-direction: column;
  justify-content: space-evenly;
  align-items: flex-start;
}

$margin: 50px;

.main__row {
  width: calc(100% - (2 * #{$margin}));
  margin-left: $margin;
  margin-right: $margin;
  height: 50px;
}

.main__row_is-half {
  width: 50%;
}
</style>

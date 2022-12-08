<template>
  <v-container fluid>
    <v-row no-gutters class="main-row">
      <v-row
        no-gutters
        class="tag-row"
        :class="{
          'tag-row_is-left': align === 'left',
          'tag-row_no-grow': index === 0,
        }"
        v-for="(tag, index) in tags"
        :key="index"
      >
        <v-col v-if="index !== 0">
          <v-icon class="tag-row__separator">mdi-circle-small</v-icon>
        </v-col>
        <v-col class="tag-row__col_no-grow" v-if="tag.icon">
          <v-icon size="21" class="tag-row__icon">{{
            "mdi-" + tag.icon
          }}</v-icon>
        </v-col>
        <v-col class="tag-row__col_no-grow">{{ tag.text }}</v-col>
      </v-row>
    </v-row>
  </v-container>
</template>

<script>
export default {
  name: "TagList",
  props: ["tags", "align"],
};
</script>

<style scoped lang="scss">
.container {
  height: 100%;
  border: 1px solid black;
  padding-left: 25px;
  padding-right: 25px;
}

.main-row {
  overflow: hidden;
  height: 25px;
}

.tag-row {
  text-align: center;
}

.tag-row_no-grow {
  flex-grow: 0;
}

.tag-row_is-left {
  flex-grow: 0 !important;
  flex-shrink: 1 !important;
}

.tag-row__col_no-grow {
  flex-grow: 0;
}

.tag-row__separator {
  margin: 0 10px;
}

.tag-row__icon {
  margin-right: 5px;
}

.icon {
  margin: 0;
}
</style>

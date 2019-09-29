<template>
  <div :class="{unactiveItem: !switcherValue}" class="test-app-main_wrap__orgitem_wrap">
    <v-layout style="margin: 0">
      <span>{{data.org_title}}</span>
      <span class="nrm-w" style="color: rgb(187, 188, 196);">{{data.hint}}</span>
      <v-spacer />
      <v-menu bottom left>
        <template v-slot:activator="{ on }">
          <v-btn icon v-on="on">
            <v-icon>mdi-dots-vertical</v-icon>
          </v-btn>
        </template>
        <v-list>
          <v-list-item>
            <v-list-item-title
              @click="() => this.switcherValue = false"
              v-if="switcherValue"
            >Выключить</v-list-item-title>
            <v-list-item-title @click="() => this.switcherValue = true" v-else>Включить</v-list-item-title>
          </v-list-item>
        </v-list>
      </v-menu>
    </v-layout>
    <v-layout v-if="hasChips" style="margin: 9px 0 20px 0">
      <div v-for="(chip ,i) in data.chips" :key="i">
        <view-chip :data="chip" />
      </div>
    </v-layout>
    <v-layout style="margin: 0">
      <div style="color: #ffaa30" v-if="!!data.rate">
        <v-icon style="color: #ffaa30">mdi-star</v-icon>
        <span>{{data.rate}} из 5</span>
      </div>
      <div v-else class="nrm-w" style="color: rgb(187, 188, 196);">
        <v-icon style="color: rgb(187, 188, 196);">mdi-star</v-icon>
        <span>Портал без рейтинга</span>
      </div>
      <span
        v-if="!!data.review"
        class="ml-2 nrm-w"
      >• {{data.review.all}} отзывов, {{data.review.not_answered}} неотвеченных</span>
      <v-spacer />
      <view-chip :data="data.need_action" v-if="data.need_action" />
      <div class="nrm-w" v-else>2 обновления</div>
    </v-layout>
  </div>
</template>

<script>
import ViewChip from "./ViewChip";
export default {
  data() {
    return {
      switcherValue: true
    };
  },
  props: ["data"],
  components: {
    ViewChip
  },
  methods: {},
  computed: {
    switcher() {
      if (this.switcherValue) {
        return "Выключить";
      }
      return "Включить";
    },
    hasChips() {
      return !!this.data.chips || null;
    }
  }
};
</script>

<style lang="scss">
.test-app-main_wrap__orgitem_wrap {
  position: relative;
  background: rgb(255, 255, 255);
  border-radius: 4px;
  border: 1px solid rgb(230, 236, 242);
  margin-bottom: 10px;
  padding: 15px 18px 15px 29px;
}
.test-app-main_wrap__orgitem_wrap::before {
  content: "";
  position: absolute;
  background: rgb(90, 57, 167);
  border-radius: 4px 0px 0px 4px;
  height: 100%;
  width: 4px;
  top: 0;
  left: 0;
}
.unactiveItem::before {
  content: "";
  position: absolute;
  background: rgb(206, 218, 230);
  border-radius: 4px 0px 0px 4px;
  height: 100%;
  width: 4px;
  top: 0;
  left: 0;
}
</style>
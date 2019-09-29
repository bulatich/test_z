<template>
  <v-content class="test-app-main_wrap">
    <v-container grid-list-lg fluid>
      <v-layout row style="margin-bottom: 35px">
        <v-flex
          style="margin-bottom: 19px"
          v-for="item in infoItems"
          :key="'infokey_' + item.key"
          xs3
        >
          <info-item :data="item" />
        </v-flex>
        <v-flex v-for="item in orgItems" :key="item.key" xs12>
          <org-item :data="item" />
        </v-flex>
      </v-layout>
    </v-container>
  </v-content>
</template>

<script>
import InfoItem from "./InfoItem";
import OrgItem from "./OrgItem";
export default {
  data() {
    return {
      infoItems: [
        { count: "165", title: "отзывов", key: 1, icon: "mdi-comment" },
        {
          count: "21",
          title: "неотвеченный отзыв",
          key: 2,
          icon: "mdi-comment"
        },
        { count: "50", title: "обновлений", key: 3, icon: "mdi-sync" },
        { count: "4,5", title: "средний рейтинг", key: 4, icon: "mdi-star" }
      ],
      orgItems: [
        {
          key: 1,
          org_title: "Google",
          hint: " •  все 30 заведений настроены",
          rate: "4,5",
          review: { all: 198, not_answered: 15 },
          chips: [
            { type: "sync", value: true },
            { type: "chip", value: "Инфа" },
            { type: "chip", value: "Прайс" },
            { type: "chip", value: "Акции" },
            { type: "chip", value: "Фото" }
          ]
        },
        {
          key: 2,
          org_title: "Flado",
          hint: " •  30 заведений  •  4 настроено  •  20 в поиске",
          rate: null,
          review: null,
          need_action: true,
          chips: [
            { type: "sync", value: false, message: "Создаём 3 страницы" },
            { type: "chip", value: "Инфа" },
            { type: "chip", value: "Прайс" },
            { type: "chip", value: "Акции" },
            { type: "chip", value: "Фото" }
          ]
        },
        {
          key: 3,
          org_title: "2Gis",
          hint: "",
          rate: null,
          review: null,
          need_action: true,
          chips: [{ type: "sync", value: false, message: "Создаём 3 страницы" }]
        },
        { key: 4, org_title: "Yell", hint: "", rate: null, review: null }
      ]
    };
  },
  components: {
    InfoItem,
    OrgItem
  }
};
</script>

<style lang="scss">
.test-app-main_wrap {
  .v-content__wrap {
    padding: 43px 80px 77px 80px;
  }
  .theme--light.v-icon {
    color: rgb(88, 50, 158);
  }
  .nrm-w {
    font-size: 13px;
    font-weight: normal;
    letter-spacing: 0px;
    line-height: 20px;
  }
  .bld-w {
    font-size: 25px;
    font-weight: bold;
    letter-spacing: 0px;
    line-height: 35px;
  }
}
</style>
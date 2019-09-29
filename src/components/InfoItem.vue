<template>
  <div class="test-app-main_wrap__infoitem_wrap">
    <div>
      <div class="bld-w">{{data.count}}</div>
      <div class="nrm-w">{{data.title}}</div>
    </div>
    <v-spacer />
    <v-icon style="font-size: 3em;">{{ data.icon }}</v-icon>
  </div>
</template>

<script>
export default {
  data() {
    return {};
  },
  props: ["data"]
};
</script>

<style lang="scss">
.test-app-main_wrap__infoitem_wrap {
  display: flex;
  background: rgb(74, 5, 148);
  border-radius: 4px;
  height: 85px;
  padding: 14px 15px 19px;
  margin: 0;
  color: #fff;
}
</style>
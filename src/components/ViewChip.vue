<template>
  <div v-if="data.type === 'chip'" class="view-chip_item nrm-w">
    <v-icon>mdi-check</v-icon>
    <span>{{data.value}}</span>
  </div>
  <div v-else-if="data.type === 'sync' && !data.value" class="view-chip_item nrm-w">
    <v-icon>mdi-sync</v-icon>
    <span>{{data.message}}</span>
  </div>
  <div
    style="background: rgb(90, 57, 167); color: #fff"
    v-else-if="data.type === 'sync' && data.value"
    class="view-chip_item nrm-w"
  >
    <v-icon style="color: #fff">mdi-check</v-icon>
    <span>Синхронизировано</span>
  </div>
  <div style="background: rgb(255, 170, 48); color: #fff" v-else class="view-chip_item nrm-w">
    <v-icon style="color: #fff">mdi-bell-outline</v-icon>
    <span>Требуется действие</span>
  </div>
</template>

<script>
export default {
  props: ["data"]
};
</script>

<style lang="scss">
.view-chip_item {
  border-radius: 4px;
  border: 1px solid rgb(230, 236, 242);
  padding: 5px 10px 3px 10px;
  margin-right: 10px;
}
</style>
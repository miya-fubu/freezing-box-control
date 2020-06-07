<template>
  <div class="item">
    <div class="flex-area">
      <p>{{ option.name }}</p>
      <p>{{ option.limit }}</p>
    </div>
    <div>
      <button @click=""></button>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from "vue-property-decorator";
import { itemOptionType } from "@/types/itemOprionType";

@Component
export default class FreezingItem extends Vue {
  @Prop()
  private option!: itemOptionType;

  
}
</script>

<style scoped>
.item {
  margin-top: 12px;
  background-color: #fff;
  border: 1px solid #dadce0;
  border-radius: 8px;
  margin-bottom: 12px;
  padding: 24px;
  padding-top: 22px;
  display: flex;
  justify-content: space-between;
}

.flex-area{
  display: flex;
  flex-direction:  row;

}
</style>

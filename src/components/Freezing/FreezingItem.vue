<template>
  <v-toolbar>
    <v-toolbar-title>{{ item.name }}</v-toolbar-title>
    <v-spacer></v-spacer>
    <v-toolbar-text>{{ item.limit }}</v-toolbar-text>
    <v-btn @click="close">close</v-btn>
  </v-toolbar>
</template>

<script lang="ts">
import { Component, Prop, Vue, Emit } from "vue-property-decorator";
import { ItemOptionType } from "@/types/ItemOprionType";

@Component
export default class FreezingItem extends Vue {
  @Prop({ default: null })
  item!: ItemOptionType;


  @Emit("close")
  close() {
    console.log(this.item.id);
    return this.item;
  }
}
</script>

<style scoped>
.flex-area {
  display: flex;
  flex-direction: row;
}
</style>

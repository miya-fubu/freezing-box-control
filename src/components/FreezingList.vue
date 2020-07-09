<template>
  <div class="list">
    <FreezingItem
      v-for="item in items"
      :key="item.id"
      :item="item"
      @close="close"
    ></FreezingItem>
    <button @click="getTable">getTest</button>
    <button @click="setTask">setTest</button>
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from "vue-property-decorator";
import { ItemOptionType } from "@/types/ItemOprionType";
import FreezingItem from "@/components/Freezing/FreezingItem.vue";
import Dexie from "dexie";
const db = new Dexie("freezingBoxControlDB");

@Component({
  components: {
    FreezingItem,
  },
})
export default class FreezingList extends Vue {
  items: ItemOptionType[] = [];
  mounted(): void {
    db.version(1).stores({
      items: `id, name, limit`,
    });
    db.table("items").put({
      id: 2,
      name: "肉",
      limit: new Date(),
    });
    db.table("items")
      .toArray()
      .then((items) => {
        this.items.splice(0);
        items.map((item) => {
          this.items.push(item);
        });
      });
  }
  getTable() {
    try {
      db.table("items")
        .toArray()
        .then((items) => {
          this.items.splice(0);
          items.map((item) => {
            this.items.push(item);
          });
        });
    } catch {
      db.version(1).stores({
        items: `id, name, limit`,
      });
      db.table("items").put({
        id: 2,
        name: "商品名",
        limit: new Date(),
      });
      this.getTable();
    }
    console.log(this.items);
  }

  setTask() {
    db.table("items").put({
      id: 2,
      name: "商品名",
      limit: new Date(),
    });
  }

  close(closeItem: ItemOptionType) {
    const serch = (item: ItemOptionType) => {
      return item.id == closeItem.id;
    };
    const removeIndex = this.items.findIndex(serch);
    db.table("items").delete(closeItem.id);
    if (removeIndex + 1) {
      this.items.splice(removeIndex, 1);
    } else {
      alert("アイテムの削除に失敗しました");
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>

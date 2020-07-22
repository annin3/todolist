<template>
  <div>
    <div>未完了のタスク</div>
    <div v-for="item in items" :key="item.name">
      <div v-if="item.condition === true">
        <span class="name">タスク名 : {{ item.name }}</span>
        <span class="name"> 期日 : {{ item.month }}月</span>
        <span class="name">{{ item.day }}日
        <button @click="finItem(item)">finish</button></span>
      </div>
    </div>
    <div>完了済みタスク</div>
    <div v-for="item in items" :key="item.name">
      <div v-if="item.condition === false">
        <span class="name">タスク名 : {{ item.name }}</span>
        <span class="name"> 期日 : {{ item.month }}月</span>
        <span class="name">{{ item.day }}日</span>
      </div>
    </div>
      <label>
        タスク名
        <input type="text" v-model="newItemName">
        期日
        <input type="number" v-model="newItemMonth">
        月
        <input type="number" v-model="newItemDay">
        日
      </label>
      <button @click="addItem">add</button>
  </div>
</template>

<script>
export default {
  name: "ItemList",
  data() {
    return {
      items: [{name: 'てすと', condition: true, month:0, day:0}],
      newItemName: "",
      newItemMonth:null,
      newItemDay:null
    };
  },
  methods: {
    addItem() {
      this.items.push({ name: this.newItemName, month: this.newItemMonth, day: this.newItemDay, condition: true})
    },
    finItem(item) {
      item.condition = false;
    }
  }
};
</script>

<style>
.table {
  margin: auto;
}
</style>
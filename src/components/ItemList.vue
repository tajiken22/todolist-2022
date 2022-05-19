<script setup>
import { ref } from "vue";

const items = ref([
  { name: "たまご", price: 100, done: false },
  { name: "りんご", price: 160, done: false },
]);
const newItemName = ref("");
const newItemPrice = ref(0);

const addItem = () => {
  items.value.push({
    name: newItemName.value,
    price: newItemPrice.value,
    done: false,
  });
};
</script>

<template>
  <div>
    <div>ItemList</div>
    <div v-for="item in items" :key="item.name">
      <div
        v-if="item.done === false"
        class="item"
        :class="{ over500: item.price >= 500 }"
      >
        <div class="name">名前： {{ item.name }}</div>
        <div class="price">{{ item.price }} 円</div>
        <div v-if="item.price >= 10000">高額商品</div>
        <a href="#" @click="item.done = true">完了</a>
      </div>
    </div>
    <div>
      <label>
        名前
        <input v-model="newItemName" type="text" />
      </label>
      <label>
        価格
        <input v-model="newItemPrice" type="number" />
      </label>
      <button @click="addItem">add</button>
    </div>
  </div>
</template>

<style>
.over500 {
  color: red;
}
</style>

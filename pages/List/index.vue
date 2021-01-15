<template>
  <div>
    <div class="input-group" :key="item" v-for="item in itemList">
      <span class="input-group-addon" id="basic-addon1">
        <input type="checkbox" :checked="item.status == 'clear'" />
      </span>
      <input type="text" class="form-control" :value="item.content" />
      <span class="input-group-btn">
        <button
          class="btn btn-defalut"
          type="button"
          @click="removeItem(Item.id)"
        >
          X
        </button>
      </span>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator'

interface ItemList {
  id: number
  content: string
  date: number
  status: string
}

@Component
export default class List extends Vue {
  itemList: ItemList[] = []

  created() {
    this.itemList = this.$store.state.itemList
  }

  removeItem(id: number) {
    this.$store.commit('removeItem, id')
  }
}
</script>

<style scoped></style>

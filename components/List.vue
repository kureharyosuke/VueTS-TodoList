<template>
  <div>
    <div v-for="item in itemList" :key="item" class="input-group">
      <span id="basic-addon1" class="input-group-addon">
        <input type="checkbox" :checked="item.status == 'clear'" />
      </span>
      <input type="text" class="form-control" :value="item.content" />
      <span class="input-group-btn">
        <button
          class="btn btn-defalut"
          type="button"
          @click="removeItem(item.id)"
        >
          X
        </button>
      </span>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Vue, Prop } from 'nuxt-property-decorator'
import { ListType } from '~/types'

@Component
export default class List extends Vue {
  @Prop({ type: Array, required: true })
  itemList: ListType.ItemList[] = []

  created() {
    this.itemList = this.$store.state.itemList
  }

  removeItem(id: number) {
    this.$store.commit('removeItem', id)
  }
}
</script>

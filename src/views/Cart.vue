<template>
  <v-container fill-height fluid class="pa-0">
    <v-btn icon fixed class="hidden-md-and-up" color="grey--text" style="top: 0.7em; right: 1em; z-index:111;"><v-icon>attach_money</v-icon></v-btn>
    <v-layout column>
      <v-layout row style="max-height: 110px;"  class="hidden-sm-and-down">
        <h1 class="my-4 ml-2" style="padding-top: 0.2em;">| Total: $ {{ this.total }}</h1>
        <v-spacer></v-spacer>
        <h1 class="my-3" style="position: absolute; right: 3em; top: 0;">Checkout</h1>
        <Hex class="ma-4" style="position: absolute; right: 0; top: 0;" icon="attach_money" color="teal"/>
      </v-layout>
      <v-layout row wrap align-content-start>
        <Item class="zoom one-by-one" v-for="item in items" :key="item.name" :item="item" />
      </v-layout>
    </v-layout>
  </v-container>
</template>

<script>
import Hex from '@/components/Hex.vue'
import Item from '@/components/Item.vue'

export default {
  name: 'Home',
  components: {
    Hex,
    Item
  },
  data () {
    return {
      men: false,
      women: false,
      category: false,
      type: false,
      total: 88.88 * 9,
      items: [
        { name: 'item-shirt', price: 88.88, sale: true, stock: 10, pics: ['', ''] },
        { name: 'item-hoodie', price: 88.88, sale: false, stock: 10, pics: ['', ''] },
        { name: 'item-a', price: 88.88, sale: true, stock: 10, pics: ['', ''] },
        { name: 'item-e', price: 88.88, sale: false, stock: 10, pics: ['', ''] }
      ]
    }
  }
}
</script>

<style lang="css" scoped></style>

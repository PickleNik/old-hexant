<template lang="html">
  <v-flex xs6 xl4 class="item">
    <v-layout column class="dark3 corner-cut hidden-lg-and-up" style="margin: 1.4em 0.25em;">
      <v-layout row class="px-2">
        <p style="height: 3em; width: calc(100% - 70px)" >{{ item.name }}</p>
        <v-layout column class="text-xs-right">
          <b class="px-1" style="max-height: 22px;" :class="item.sale ? 'pink dark3--text': ''">$ {{ item.price }}</b>
          <s class="px-1" v-if="item.sale">$ {{ item.price + 11 }}</s>
        </v-layout>
      </v-layout>
      <v-img aspect-ratio="0.78" contain src="http://static1.squarespace.com/static/52a4c2f7e4b05fd98a136ff4/59ffac944192021a54418de6/5a5a3c42e4966bd4a51b24a2/1515863151528/?format=1500w" alt="error"/>
      <v-layout row wrap class="px-2">
        <v-flex xs6 class="pr-1"><v-select color="grey" :items="sizes" v-model="size" :placeholder="size" label="Size"></v-select></v-flex>
        <v-flex xs6 class="pl-1"><v-select color="grey" :items="colors" v-model="color" :placeholder="color" label="Color"></v-select></v-flex>
        <v-layout row style="margin-bottom: -0.5em;z-index:1;">
          <v-btn v-if="inCart && qty==1" icon color="pink mx-auto dark3--text" @click="inCart = false, qty = 0"><v-icon size="18">remove_shopping_cart</v-icon></v-btn>
          <v-btn v-if="inCart && qty>1" icon color="pink mx-auto dark3--text" @click="qty--"><v-icon>remove</v-icon></v-btn><span class="mx-2 pt-3" v-if="inCart">{{ qty }}</span><v-btn v-if="inCart" icon color="green mx-auto dark3--text" @click="qty++"><v-icon>add</v-icon></v-btn>
          <v-btn v-else block round color="green dark3--text" @click="inCart = true, qty++">Add to Cart<v-icon right size="18">add_shopping_cart</v-icon></v-btn>
        </v-layout>
      </v-layout>
    </v-layout>

    <v-layout row class="dark3 corner-cut pl-3 hidden-md-and-down mx-2 my-4">
      <v-flex xs4>
        <v-img aspect-ratio="0.78" style="max-height: 200px;" contain src="http://static1.squarespace.com/static/52a4c2f7e4b05fd98a136ff4/59ffac944192021a54418de6/5a5a3c42e4966bd4a51b24a2/1515863151528/?format=1500w" alt="error"/>
      </v-flex>
      <v-flex xs8 class="px-3">
        <v-layout column style="height: 75%;">
          <v-layout row>
            <p style="width: calc(100% - 80px); max-height: 2em;" class="pr-2">{{ item.name }}</p>
            <v-layout column>
              <b class="px-1" style="height: 22px;" :class="item.sale ? 'pink dark3--text': ''">$ {{ item.price }}</b>
              <s class="px-1" v-if="item.sale">$ {{ item.price + 11 }}</s>
            </v-layout>
          </v-layout>
          <v-layout row>
            <v-flex xs6 class="pr-1"><v-select color="grey" :items="sizes" v-model="size" :placeholder="size" label="Size"></v-select></v-flex>
            <v-flex xs6 class="pl-1"><v-select color="grey" :items="colors" v-model="color" :placeholder="color" label="Color"></v-select></v-flex>
          </v-layout>
        </v-layout>
          <v-layout row>
            <v-spacer></v-spacer>
            <v-btn v-if="inCart && qty==1" icon color="pink dark3--text" @click="inCart = false, qty = 0"><v-icon size="18">remove_shopping_cart</v-icon></v-btn>
            <v-btn v-if="inCart && qty>1" icon color="pink dark3--text" @click="qty--"><v-icon>remove</v-icon></v-btn><span class="mt-2 pt-2 mx-2" v-if="inCart">{{ qty }}</span><v-btn v-if="inCart" icon color="green dark3--text" @click="qty++"><v-icon>add</v-icon></v-btn>
            <v-btn v-else round color="green dark3--text" @click="inCart = true, qty++">Add to Cart<v-icon right size="18">add_shopping_cart</v-icon></v-btn>
          </v-layout>
      </v-flex>
    </v-layout>
  </v-flex>
</template>

<script>
export default {
  props: ['item'],
  data () {
    return {
      sizes: ['XL', 'L', 'M'],
      size: 'XL',
      colors: ['Red', 'Green', 'Blue', 'Grey', 'White', 'Black'],
      color: 'Black',
      inCart: false,
      qty: 0
    }
  }
}
</script>

<style lang="css" scoped>
/* .item {
  transition-duration: 5s;
  transition-timing-function: ease-in-out;
  transition-property: all;
}
.item:hover {
  z-index: 10;
  transform: scale(1.2);
} */
</style>

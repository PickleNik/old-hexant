<template>
  <v-container fill-height fluid class="pa-0">
    <v-btn icon fixed class="hidden-md-and-up" color="grey--text" style="top: 0.8em; right: 1em; z-index:111;"><v-icon>search</v-icon></v-btn>
    <v-layout column>
      <v-layout row style="max-height: 110px;" class="hidden-sm-and-down">
        <v-menu v-if="men || women"><h1 class="ml-2" style="margin-top: 1.2em; margin-bottom: 1.2em;" slot="activator">{{ men ? '| Men' : women ? '| Women' : '' }}</h1>
          <v-list>
            <v-list-tile @click="men = true, women = false">
              <v-list-tile-title>Men</v-list-tile-title>
            </v-list-tile>
            <v-list-tile @click="women = true, men = false">
              <v-list-tile-title>Women</v-list-tile-title>
            </v-list-tile>
          </v-list>
        </v-menu>
        <v-menu v-if="category"><h1 class="ml-2" style="margin-top: 1.2em; margin-bottom: 1.2em;" slot="activator">{{ category ? '> ' + category : '' }}</h1>
          <v-list>
            <v-list-tile @click="category='All'">
              <v-list-tile-title>View All</v-list-tile-title>
            </v-list-tile>
            <v-list-tile @click="category='Sale'">
              <v-list-tile-title>Sale</v-list-tile-title>
            </v-list-tile>
            <v-list-tile @click="category='Sol'">
              <v-list-tile-title>Sol</v-list-tile-title>
            </v-list-tile>
          </v-list>
        </v-menu>
        <v-menu v-if="type"><h1 class="ml-2" style="margin-top: 1.2em; margin-bottom: 1.2em;" slot="activator">{{ type ? '> ' + type : '' }}</h1>
          <v-list>
            <v-list-tile @click="type='T-Shirts'">
              <v-list-tile-title>T-Shirts</v-list-tile-title>
            </v-list-tile>
            <v-list-tile @click="type='Hoodies'">
              <v-list-tile-title>Hoodies</v-list-tile-title>
            </v-list-tile>
            <v-list-tile @click="type='Sweaters'">
              <v-list-tile-title>Sweaters</v-list-tile-title>
            </v-list-tile>
          </v-list>
        </v-menu>
        <v-spacer></v-spacer>
        <Hex class="ma-4" style="position: absolute; right: 0.2em; top: 1em;" icon="search" color="deep-orange"/>
        <Hex class="ma-4" style="position: absolute; right: 4em; top: 65em;" icon="attach_money" color="orange"/>
      </v-layout>

      <v-layout column v-if="!men && !women" class="mx-auto" style="margin-top: 50vh;transform: translateY(-50%);">
        <v-layout row>
          <v-flex class="mx-2 zoom-rotate one-by-one">
            <HexBig class="hidden-md-and-down" @click.native="men = true" text="Men" image="https://thenypost.files.wordpress.com/2018/06/men-shopping-masculine.jpg?quality=90&strip=all&w=618&h=410&crop=1"/>
            <HexMedium class="hidden-lg-and-up hidden-xs-only" @click.native="men = true" text="Men" image="https://thenypost.files.wordpress.com/2018/06/men-shopping-masculine.jpg?quality=90&strip=all&w=618&h=410&crop=1"/>
            <HexSmall class="hidden-sm-and-up" @click.native="men = true" text="Men" image="https://thenypost.files.wordpress.com/2018/06/men-shopping-masculine.jpg?quality=90&strip=all&w=618&h=410&crop=1"/>
          </v-flex>
          <v-flex class="mx-2 zoom-rotate one-by-one">
            <HexBig class="hidden-md-and-down" @click.native="women = true" text="Women" image="https://cdn.images.express.co.uk/img/dynamic/130/590x/women-shopping-825605.jpg"/>
            <HexMedium class="hidden-lg-and-up hidden-xs-only" @click.native="women = true" text="Women" image="https://cdn.images.express.co.uk/img/dynamic/130/590x/women-shopping-825605.jpg"/>
            <HexSmall class="hidden-sm-and-up" @click.native="women = true" text="Women" image="https://cdn.images.express.co.uk/img/dynamic/130/590x/women-shopping-825605.jpg"/>
          </v-flex>
        </v-layout>
      </v-layout>

      <v-layout column v-if="(men || women) && !category && !type" class="mx-auto" style="margin-top: 50vh;transform: translateY(-50%);">
        <v-layout row style="margin-top: -5.2em;">
          <v-flex class="mx-2 zoom-rotate delay-3">
            <HexBig class="hidden-md-and-down" @click.native="category='Sale'" text="Sale" image="https://us.123rf.com/450wm/geckly/geckly0908/geckly090800036/5415350-sale-background-in-red-tints.jpg?ver=6"/>
            <HexMedium class="hidden-lg-and-up hidden-xs-only" @click.native="category='Sale'" text="Sale" image="https://us.123rf.com/450wm/geckly/geckly0908/geckly090800036/5415350-sale-background-in-red-tints.jpg?ver=6"/>
          </v-flex>
          <v-flex class="mx-2 zoom-rotate delay-4">
            <HexBig class="hidden-md-and-down" @click.native="category='All'" text="View All" image="https://ak4.picdn.net/shutterstock/videos/12199724/thumb/1.jpg"/>
            <HexMedium class="hidden-lg-and-up hidden-xs-only" @click.native="category='All'" text="View All" image="https://ak4.picdn.net/shutterstock/videos/12199724/thumb/1.jpg"/>
          </v-flex>
          <v-flex class="mx-2 zoom-rotate delay-5">
            <HexBig class="hidden-md-and-down" @click.native="category='Sol'" text="Sol" image="https://cdn.clipart.email/a113be22cf5af56baec8abab15acdac2_28-collection-of-universe-clipart-images-high-quality-free-_612-471.jpeg" />
            <HexMedium class="hidden-lg-and-up hidden-xs-only" @click.native="category='Sol'" text="Sol" image="https://cdn.clipart.email/a113be22cf5af56baec8abab15acdac2_28-collection-of-universe-clipart-images-high-quality-free-_612-471.jpeg" />
          </v-flex>
        </v-layout>
        <v-layout row class="hidden-sm-and-up">
          <v-flex class="mx-2 zoom-rotate delay-3">
            <HexSmall @click.native="category='Sale'" text="Sale" image="https://us.123rf.com/450wm/geckly/geckly0908/geckly090800036/5415350-sale-background-in-red-tints.jpg?ver=6"/>
          </v-flex>
          <v-flex class="mx-2 zoom-rotate delay-4">
            <HexSmall @click.native="category='All'" text="View All" image="https://ak4.picdn.net/shutterstock/videos/12199724/thumb/1.jpg"/>
          </v-flex>
        </v-layout>
        <v-layout row class="mx-auto hidden-sm-and-up" style="margin-top: -3.1em;">
          <v-flex class="mx-2 zoom-rotate delay-5">
            <HexSmall @click.native="category='Sol'" text="Sol" image="https://cdn.clipart.email/a113be22cf5af56baec8abab15acdac2_28-collection-of-universe-clipart-images-high-quality-free-_612-471.jpeg" />
          </v-flex>
        </v-layout>
      </v-layout>

      <v-layout column v-if="(men || women) && category && !type" class="mx-auto" style="margin-top: calc(50vh - 70px);transform: translateY(-50%);">
        <v-layout row class="hidden-xs-only">
          <v-flex class="mx-2 zoom-rotate one-by-one">
            <HexBig class="hidden-md-and-down" @click.native="type = 'T-Shirts'" text="T-Shirts" image="https://www.mltd.com//images/category/M_T-Shirts.jpg" />
            <HexMedium class="hidden-lg-and-up" @click.native="type = 'T-Shirts'" text="T-Shirts" image="https://www.mltd.com//images/category/M_T-Shirts.jpg" />
          </v-flex>
          <v-flex class="mx-2 zoom-rotate one-by-one">
            <HexBig class="hidden-md-and-down" @click.native="type = 'Hoodies'" text="Hoodies" image="https://images.unsplash.com/photo-1500625597061-d472abd2afbb?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=700&q=80" />
            <HexMedium class="hidden-lg-and-up" @click.native="type = 'Hoodies'" text="Hoodies" image="https://images.unsplash.com/photo-1500625597061-d472abd2afbb?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=700&q=80" />
          </v-flex>
          <v-flex class="mx-2 zoom-rotate one-by-one">
            <HexBig class="hidden-md-and-down" @click.native="type = 'Sweaters'" text="Sweaters" image="https://pixel.nymag.com/imgs/daily/strategist/2017/10/03/03-uniqlo-sweater-lede.w1200.h630.jpg"/>
            <HexMedium class="hidden-lg-and-up" @click.native="type = 'Sweaters'" text="Sweaters" image="https://pixel.nymag.com/imgs/daily/strategist/2017/10/03/03-uniqlo-sweater-lede.w1200.h630.jpg"/>
          </v-flex>
        </v-layout>

        <v-layout row class="hidden-sm-and-up">
          <v-flex class="mx-2 zoom-rotate one-by-one">
            <HexBig class="hidden-md-and-down" @click.native="type = 'T-Shirts'" text="T-Shirts" image="https://www.mltd.com//images/category/M_T-Shirts.jpg" />
            <HexMedium class="hidden-lg-and-up" @click.native="type = 'T-Shirts'" text="T-Shirts" image="https://www.mltd.com//images/category/M_T-Shirts.jpg" />
          </v-flex>
          <v-flex class="mx-2 zoom-rotate one-by-one">
            <HexBig class="hidden-md-and-down" @click.native="type = 'Hoodies'" text="Hoodies" image="https://images.unsplash.com/photo-1500625597061-d472abd2afbb?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=700&q=80" />
            <HexMedium class="hidden-lg-and-up" @click.native="type = 'Hoodies'" text="Hoodies" image="https://images.unsplash.com/photo-1500625597061-d472abd2afbb?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=700&q=80" />
          </v-flex>
        </v-layout>

        <v-layout row class="mx-auto hidden-sm-and-up" style="margin-top: -8.8em;">
          <v-flex class="mx-2 zoom-rotate one-by-one">
            <HexBig class="hidden-md-and-down" @click.native="type = 'Sweaters'" text="Sweaters" image="https://pixel.nymag.com/imgs/daily/strategist/2017/10/03/03-uniqlo-sweater-lede.w1200.h630.jpg"/>
            <HexMedium class="hidden-lg-and-up" @click.native="type = 'Sweaters'" text="Sweaters" image="https://pixel.nymag.com/imgs/daily/strategist/2017/10/03/03-uniqlo-sweater-lede.w1200.h630.jpg"/>
          </v-flex>
        </v-layout>
      </v-layout>
      <v-layout v-if="(men || women) && category && type" row wrap align-content-start>
        <Item class="zoom one-by-one" v-for="item in items" :key="item.name" :item="item" />
      </v-layout>
    </v-layout>
  </v-container>
</template>

<script>
import Hex from '@/components/Hex.vue'
import HexSmall from '@/components/Hex-small.vue'
import HexMedium from '@/components/Hex-medium.vue'
import HexBig from '@/components/Hex-big.vue'
import Item from '@/components/Item.vue'

export default {
  name: 'Home',
  components: {
    Hex,
    HexSmall,
    HexMedium,
    HexBig,
    Item
  },
  data () {
    return {
      men: false,
      women: false,
      category: false,
      type: false,
      items: [
        { name: 'item-shirt', price: 88.88, sale: true, stock: 10, pics: ['', ''] },
        { name: 'item-hoodie', price: 88.88, sale: false, stock: 10, pics: ['', ''] },
        { name: 'item-shoe', price: 88.88, sale: false, stock: 10, pics: ['', ''] },
        { name: 'item-a', price: 88.88, sale: true, stock: 10, pics: ['', ''] },
        { name: 'item-b', price: 88.88, sale: false, stock: 10, pics: ['', ''] },
        { name: 'item-c', price: 88.88, sale: false, stock: 10, pics: ['', ''] },
        { name: 'item-d', price: 88.88, sale: true, stock: 10, pics: ['', ''] },
        { name: 'item-e', price: 88.88, sale: false, stock: 10, pics: ['', ''] }
      ]
    }
  }
}
</script>

<style lang="css" scoped>

</style>

<template>
  <section>
    <button @click="changeIndex">CNT</button>
    <div class="home">
      <div>
        <keep-alive :include="cacheList">
          <component :is="changeComponent()"></component>
        </keep-alive>
      </div>
      <div>
        <keep-alive max="3">
          <component :is="'comp-b'"></component>
        </keep-alive>
      </div>
      <div>
        <keep-alive max="3">
          <component :is="'comp-c'"></component>
        </keep-alive>
      </div>
    </div>
  </section>
</template>

<script>
import CompA from '@/components/CompA.vue'
import CompB from '@/components/CompB.vue'
import CompC from '@/components/CompC.vue'
import CompD from '@/components/CompD.vue'
import CompE from '@/components/CompE.vue'

export default {
  name: 'Home',
  components: {
    CompA,
    CompB,
    CompC,
    CompD,
    CompE
  },
  data () {
    return {
      cacheList: [
        'CompA',
        'CompB',
        'CompC',
        'CompD',
        'CompE'
      ],
      currentPage: 'comp-a',
      pages: ['comp-a', 'comp-b', 'comp-c', 'comp-d', 'comp-e'],
      index: 0
    }
  },
  created () {
    // window.addEventListener('keypress', (e) => {
    //   e.preventDefault()
    //   this.changeComponent
    // })
  },
  methods: {
    changeComponent () {
      return this.pages[this.index]
    },
    changeIndex () {
      if (this.index === 4) {
        this.index = 0
        return
      }
      this.index = this.index + 1
    }
  }
}
</script>

<style lang="scss" scoped>
.home {
  display: flex;
  width: 300%;

  & div {
    width: 100%;
  }

  & div >>> div {
    width: 100%;
  }
}
</style>
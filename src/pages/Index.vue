<template>
  <q-page class="flex flex-center col">
    <h3>數列填空</h3>
    <div>
      <div class = "item" v-for = "(i, idx) in items" :key="idx">
        <span v-if = "q !== idx">{{ i }}</span>
        <input v-else type="number" name="" v-model = "ans" @input = "check()"/>
      </div>
    </div>
    <q-btn v-if ="win" @click = "reset()">再來!</q-btn>
  </q-page>
</template>

<script>
export default {
  name: 'PageIndex',
  props: ['type'],
  data() {
    return {
      items: [1,2,4,8,16,32,64],
      q: 3,
      ans: 0,
      win: false
    }
  },
  methods: {
    check() {
      if (this.ans == this.items[this.q]) {
        this.win = true
      }
    },
    reset() {
      this.win = false;
      this.q = Math.floor(Math.random() * 3) + 2;
      if (this.type == 'r') {
        const r = Math.floor(Math.random() * 4) + 1;
        this.items = [1,r,r*r,r*r*r,r*r*r*r,r*r*r*r*r,r*r*r*r*r*r];
      }
      if (this.type == 'd') {
        const d = Math.floor(Math.random() * 4) + 1;
        this.items = [1,1+d,1+2*d,1+3*d,1+4*d,1+5*d];
      }
    }
  },
  mounted() {
    if (this.type == 'd') {
      this.items = [1,2,3,4,5,6,7]
    }
    if (this.type == 'r') {
      this.items = [1,2,4,8,16,32,64]
    }
  },
  watch: {
    type() {
      this.reset()
    }
  }
}
</script>

<style type="text/css" scoped="">
  
  .item {
    display: inline-flex;
    justify-content: center;
    align-items: center;
    width: 4em;
    height: 4em;
    text-align: center;
    border: 1px solid black;
  }

  input {
    width: 100%;
  }

  .col {
    flex-direction: column;
  }

</style>

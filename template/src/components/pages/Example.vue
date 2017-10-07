<template>
  <div class="example">
    <topbar></topbar>
    <main class="main">
      <img :src="logo" alt="L'Atelier">
      <div>
        <div class="text" v-on:click="appendTextToMessage">{{ msg }}</div>
        <div class="subTitle">How to display an Array : </div>
        <div v-for="v in array2" :key="v.id">
          Value -> {{v.data}}
        </div>
      </div>
    </main>
  </div>
</template>

<script>

import topbar from '@/components/Topbar';
import logo from '@/assets/logo.png';

export default {
  name: 'example',
  components: {
    topbar,
  },
  data() {
    return {
      msg: 'Click on this message to add some text',
      logo,
      array: [{ id: '453', data: 'value1' }, { id: '926', data: 'value2' }],
    };
  },
  mounted() {

  },
  methods: {
    appendTextToMessage() {
      this.msg += ' text append';
    },
  },
  watch: {
    msg(newValue) {
      console.log(`msg was modified to ${newValue}`);
    },
  },
  computed: {
    array2() {
      const newArray = this.array.slice();
      newArray.push({ id: '958', data: 'value added in computed' });
      return newArray;
    },
  },
};
</script>

<style scoped lang="scss">
@import '~style/theme.scss';

.example {
  .main {
    justify-content: space-around;
  }
}
</style>

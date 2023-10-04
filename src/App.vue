<script setup>
import HelloWorld from './components/HelloWorld.vue'
import { h } from 'vue';
import { SearchOutlined } from '@ant-design/icons-vue';
</script>

<template>
  <h1 class="text-3xl font-bold underline">
    Hello world!
  </h1>
  <a-space direction="vertical">
    <a-space warp>
      <a-button type="dashed" :icon="h(SearchOutlined)">Search</a-button>
      <a-button :icon="h(SearchOutlined)" href="https://www.google.com" />
    </a-space>
  </a-space>

  <h4>{{ getTitle() }}</h4>
  <h4>{{ getData }}</h4>
  <h6>{{ firstName }}</h6>

<h1>รายละเอียด</h1>
  <a-button type="primary" :icon="h(SearchOutlined)" @click="toggleVisble">โชว์เพิ่มเติม</a-button>

  <article v-show="isVisble">
  <hr><br>
  <h2>Hobby</h2>
  <ul>
    <li v-for="(item, index) in hobby" :key="index">{{ item }}</li>
  </ul>

  <h2>Job History</h2>
  <ul>
    <li v-for="(item, index) in job" :key="key"> {{ item.company }} - {{ item.mainJob }}</li>
  </ul>
  <a-button type="primary" :icon="h(SearchOutlined)" v-on:click="showInfo">Info</a-button>
</article>


</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      firstName: 'Mai Mai Mai',
      age: 23,
      hobby: ['ฟังเพลง', 'เล่นเกม', 'เที่ยว'],
      job: [
        { company: "hitachi ebworx", mainJob: 'Application engineer' },
        { company: 'Sansiri', mainJob: 'Developer' },
      ],
      isVisble: false
    }
  },
  methods: {// auto เมื่อรีหน้าใหม่
    getTitle() {
      return 'ข้อมูล'
    },
    showInfo() {
      alert(this.firstName)
    },
    toggleVisble(){
      this.isVisble = !this.isVisble
    }
  },
  computed: { //   เรียกเมื่อข้อมูลที่สนใจเปลี่ยนแปลง
    getData() {
      return `Name: ${this.firstName}  Age:${this.age}`;
    },
  },
  watch: { /// คอยจับตาดู
    ageValidate(value) {
      if (value > 25) {
        alert('ไม่ควรเกิน')
      }
    }

  }
}
</script>



<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}

.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}

.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>

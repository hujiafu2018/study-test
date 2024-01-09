<!--
 * @Author: Mr.Hu
 * @Date: 2022-01-18 14:06:08
 * @Description: 
-->
<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js + TypeScript App"/>
  </div>
</template>

<script lang="ts">
import { onMounted, defineProps } from "vue";
import { Options, Vue } from 'vue-class-component';
import HelloWorld from '@/components/HelloWorld.vue'; // @ is an alias to /src

@Options({
  components: {
    HelloWorld,
  },
})
export default class Home extends Vue {
  setup() {
    super(props: defineProps);
    onMounted() => {
  
    }
  }
}
</script>

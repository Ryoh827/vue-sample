<template>
  <div class="home">
    <Menu text="right"/>
    <MainContent msg="Content"/>
    <Menu text="left"/>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import MainContent from '@/components/MainContent.vue';
import Menu from '@/components/Menu.vue';

@Component({
  components: {
    MainContent,
    Menu,
  },
})
export default class Home extends Vue {}
</script>

<style lang="scss">
</style>

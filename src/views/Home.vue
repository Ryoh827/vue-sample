<template>
  <div class="home">
    <div>
      <p>Page: {{ this.$route.params.id || "Top" }} </p>
    </div>
    <Menu text="left"/>
    <MainContent msg="Content" :id="this.$route.params.id"/>
    <Menu text="right"/>
  </div>
</template>

<script lang="ts">
import { Component, Vue, Watch } from 'vue-property-decorator';
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

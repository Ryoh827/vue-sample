<template>
  <div class="home">
    <div>
      <Menu :pageId="this.info.data.leftMenuPageId"/>
      <MainContent msg="Content" :id="getPageId"/>
      <Menu :pageId="this.info.data.rightMenuPageId"/>
    </div>
    <footer>
      <div class="page-nav">
        <p>Page: {{ this.$route.params.id || "Top" }} </p>
        <ul>
          <router-link tag="li" :to="{ name: 'home'}">
            <a>Top</a>
          </router-link>
          <router-link tag="li" :to="{ name: 'page', params: { id: 1 }}">
            <a>1</a>
          </router-link>
          <router-link tag="li" :to="{ name: 'page', params: { id: 2 }}">
            <a>2</a>
          </router-link>
          <router-link tag="li" :to="{ name: 'page', params: { id: 3 }}">
            <a>3</a>
          </router-link>
          <router-link tag="li" :to="{ name: 'page', params: { id: 4 }}">
            <a>4</a>
          </router-link>
          <router-link tag="li" :to="{ name: 'page', params: { id: 5 }}">
            <a>5</a>
          </router-link>
          <router-link tag="li" :to="{ name: 'page', params: { id: 6 }}">
            <a>6</a>
          </router-link>
          <router-link tag="li" :to="{ name: 'page', params: { id: 7 }}">
            <a>7</a>
          </router-link>
        </ul>
      </div>
    </footer>
  </div>
</template>

<script lang="ts">
import { Component, Vue, Watch } from 'vue-property-decorator';
import MainContent from '@/components/MainContent.vue';
import Menu from '@/components/Menu.vue';
import axios from 'axios';

@Component({
  components: {
    MainContent,
    Menu,
  },
})

export default class Home extends Vue {
  private info: any = {
    data: {
      leftMenuPageId: 0,
      rightMenuPageId: 0,
      topPageId: 0,
    }
  };
  
  private async mounted() {
    if (this.info.satus !== 200) {
      this.info = await axios.get('/pages/info.json');
    }
  }

  private get getPageId() {
    return this.$route.params.id || this.info.data.topPageId || 0;
  }
}
</script>

<style lang="scss">
.page-nav {
  width: 100%;
  display: block;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>

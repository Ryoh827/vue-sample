<template>
  <div class="hello">
    <h1>{{ msg }} - {{ pageId || "Top" }}</h1>
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
    <p>
      For a guide and recipes on how to configure / customize this project,<br>
      check out the
      <a href="https://cli.vuejs.org" target="_blank" rel="noopener">vue-cli documentation</a>.
    </p>
    <h3>Installed CLI Plugins</h3>
    <ul>
      <li><a href="https://github.com/vuejs/vue-cli/tree/dev/packages/%40vue/cli-plugin-babel" target="_blank" rel="noopener">babel</a></li>
      <li><a href="https://github.com/vuejs/vue-cli/tree/dev/packages/%40vue/cli-plugin-typescript" target="_blank" rel="noopener">typescript</a></li>
      <li><a href="https://github.com/vuejs/vue-cli/tree/dev/packages/%40vue/cli-plugin-pwa" target="_blank" rel="noopener">pwa</a></li>
    </ul>
    <h3>Essential Links</h3>
    <ul>
      <li><a href="https://vuejs.org" target="_blank" rel="noopener">Core Docs</a></li>
      <li><a href="https://forum.vuejs.org" target="_blank" rel="noopener">Forum</a></li>
      <li><a href="https://chat.vuejs.org" target="_blank" rel="noopener">Community Chat</a></li>
      <li><a href="https://twitter.com/vuejs" target="_blank" rel="noopener">Twitter</a></li>
      <li><a href="https://news.vuejs.org" target="_blank" rel="noopener">News</a></li>
    </ul>
    <h3>Ecosystem</h3>
    <ul>
      <li><a href="https://router.vuejs.org" target="_blank" rel="noopener">vue-router</a></li>
      <li><a href="https://vuex.vuejs.org" target="_blank" rel="noopener">vuex</a></li>
      <li><a href="https://github.com/vuejs/vue-devtools#vue-devtools" target="_blank" rel="noopener">vue-devtools</a></li>
      <li><a href="https://vue-loader.vuejs.org" target="_blank" rel="noopener">vue-loader</a></li>
      <li><a href="https://github.com/vuejs/awesome-vue" target="_blank" rel="noopener">awesome-vue</a></li>
    </ul>
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue, Watch } from 'vue-property-decorator';

@Component
export default class MainContent extends Vue {
  @Prop() private msg!: string;
  @Prop() private id!: number;

  private pageId: number = this.id || 0;

  @Watch('id')
  private onIdChanged(val: number, oldVal: number) {
    this.pageId = val;
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
h3 {
  margin: 40px 0 0;
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
div.hello {
  float: left;
  width: 34%;
}
</style>

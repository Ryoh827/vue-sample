<template>
  <div class="container">
    <h1>{{ pagename }} - {{ pageId }}</h1>
    <div class="content" v-html=body ></div>
  </div>
</template>

<script lang="ts">
import { Vue, Component, Prop, Watch } from 'vue-property-decorator';
import axios from 'axios';

@Component({})

export default class Content extends Vue {

  public static info: any = null;
  @Prop() private pageId!: number;

  private body: string = '';

  private pagename: string = '';

  @Watch('pageId')
  private onChangePageId(val: number, oldVal: number): void {
    this.pageId = val;
    this.updatePage();
  }

  private async mounted() {
    this.updatePage();
  }

  private async updatePage(): Promise<void> {
    try {
      const response = await axios.get(`/pages/${this.pageId}.json`);
      if (response.status === 200) {
        this.pagename = response.data.pagename;
        this.body = response.data.body;
      } else {
        this.pagename = 'Not Found';
        this.body = '<p>This Page was maybe deleted</p>';
      }
    } catch (err) {
      this.pagename = 'Not Found';
      this.body = '<p>This Page was maybe deleted</p>';
    }
  }
}
</script>

<style lang="scss" scoped>
.content {
  height: 60vh;
}
</style>



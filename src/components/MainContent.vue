<template>
  <div class="hello">
    <Content :pageId="this.pageId"/>
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue, Watch } from 'vue-property-decorator';
import Content from '@/components/Content.vue';

@Component({
  components: {
    Content,
  },
})
export default class MainContent extends Vue {
  @Prop() private msg!: string;
  @Prop() private id!: number;

  private pageId: number = this.id || 0;

  @Watch('id')
  private onIdChanged(val: number, oldVal: number) {
    this.pageId = val || 0;
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
h3 {
  margin: 40px 0 0;
}
div.hello {
  float: left;
  width: 34%;
}
</style>

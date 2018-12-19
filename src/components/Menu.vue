<template>
    <div class="menu">
        <Content :pageId="this.pageId"/>
    </div>
</template>

<script lang="ts">
import { Component, Prop , Vue } from 'vue-property-decorator';
import Content from '@/components/Content.vue';

@Component({
    components: {
        Content,
    },
})
export default class Menu extends Vue {
  @Prop() private pageId!: number;

  @Prop() private text!: string;
}
</script>

<style lang="scss">
    div.menu {
        float: left;
        width: 33%;
    }
</style>



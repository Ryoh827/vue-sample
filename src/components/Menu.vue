<template>
    <div class="menu">
        <h2>{{text}}</h2>
    </div>
</template>

<script lang="ts">
import { Component, Prop , Vue } from 'vue-property-decorator';

@Component
export default class Menu extends Vue {
  @Prop() private text!: string;
}
</script>

<style lang="scss">
    div.menu {
        float: left;
        width: 33%;
    }
</style>



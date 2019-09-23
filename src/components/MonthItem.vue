<template>
    <li data-item>
        <router-link data-link to="/">{{val}}</router-link>
    </li>
</template>

<script lang="ts">
    import {Component, Prop, Vue} from 'vue-property-decorator';

    @Component
    export default class MonthItem extends Vue {
        @Prop(String)  val! : any
    }
</script>

<style scoped lang="scss">
    [data-item]{
        width:300px;margin-left:5%;margin-top:20px;box-shadow: 0 0 2px 1px #ccc;
        [data-link] {
            display:block;height:200px;font-size:30px;text-decoration: none;text-align: center;
            line-height:200px;color:#606266;transition: 0.2s;background: none;
            &:hover{background: #F2F6FC;font-size:40px;font-weight: bold}
        }
    }

</style>

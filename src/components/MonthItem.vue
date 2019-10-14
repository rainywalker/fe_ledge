<template>
    <li data-item >
        <router-link
                data-link
                :style="{background:`url(${item.img.uri}) no-repeat`,backgroundSize:'cover'}"
                :to="{name:'MonthPage',params:{year:currentYear,month:item.label}}"><span data-label>{{item.label}}</span></router-link>
        {{daysInMonth}}
    </li>
</template>

<script lang="ts">
    import {Component, Prop, Vue} from 'vue-property-decorator';

    @Component
    export default class MonthItem extends Vue {
        @Prop(Object)  item! : any;
        @Prop(String)  currentYear! : string;
        @Prop(Number)  daysInMonth! : number;
        @Prop(Object)  dateCtx! : any;
    }
</script>

<style scoped lang="scss">
    [data-item]{
        width:300px;height:200px;margin-left:5%;margin-top:20px;
        [data-link] {
            display:block;position:relative;height:200px;font-size:50px;text-decoration: none;text-align: center;
            line-height:200px;color:#333;transition:all 0.2s ease-in;box-shadow: 2px 0 10px rgba(0,0,0,.44);
            &:before{display: block;position: absolute;left:0;right:0;bottom:0;top:0;border:1px solid rgba(0,0,0,.2);content:''}
            &:hover{font-size:70px;font-weight: bold;transform: scale(1.1)}

            [data-label] {
                display:block;height:200px;background: rgba(0,0,0,.3);color:#fff
            }
        }
    }

</style>

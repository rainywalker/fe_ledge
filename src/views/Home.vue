<template>
    <div class="home">
        <h1 data-title>YoonJ HouseHold Ledge</h1>
        <div data-wrap>
            <div class="btnArea">
                <el-button  icon="el-icon-d-arrow-left" circle size="mini"></el-button>
                <el-button  icon="el-icon-arrow-left" circle size="mini"></el-button>
                <span data-year><strong>{{dateCtx.format('YYYY')}}</strong></span>
                <el-button  icon="el-icon-arrow-right" circle size="mini"></el-button>
                <el-button  icon="el-icon-d-arrow-right" circle size="mini"></el-button>
            </div>

            <ul data-month>
                <li data-item v-for="(n,i) in monthString" :key="i">
                    <router-link data-link to="/">{{n}}</router-link>
                </li>
            </ul>
        </div>
    </div>
</template>

<script lang="ts">
    import {Component, Vue} from 'vue-property-decorator';
    import HelloWorld from '@/components/HelloWorld.vue'; // @ is an alias to /src
    import moment from 'moment';

    @Component({
        components: {
            HelloWorld,
        },
    })
    export default class Home extends Vue {
        public dateCtx : any = moment();

        get monthString() {
            let str : any;
            const monthArray : Array<string> = [];

            for (let i=1; i<13; i++) {
                if (i < 10) str = `0${i}`;
                else str = i;
                monthArray.push(str)
            }
            return monthArray
        }

    }
</script>
<style lang="scss">
    .btnArea{display: flex;align-items: center;justify-content: center; }
    [data-title]{
        text-align: center;padding:40px 0;color:#a0cfff;text-shadow:1px 1px 1px rgba(198, 226, 255,1)
    }
    [data-wrap]{
        [data-year] {
            font-size:40px;padding:0 20px;color:#666;
        }
        [data-month] {
            display: flex;flex-wrap: wrap;padding:40px 0;justify-content: center;
            [data-item]{
                width:300px;margin-left:5%;margin-top:20px;box-shadow: 0 0 2px 1px #ccc;
                [data-link] {
                    display:block;height:200px;font-size:30px;text-decoration: none;text-align: center;
                    line-height:200px;color:#606266;transition: 0.2s;background: none;
                    &:hover{background: #F2F6FC;font-size:40px;font-weight: bold}
                }
            }
        }
    }
</style>

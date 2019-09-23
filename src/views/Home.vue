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
                <month-item  v-for="(n,i) in monthString" :key="i" :val="n"></month-item>
            </ul>
        </div>
    </div>
</template>

<script lang="ts">
    import {Component, Vue} from 'vue-property-decorator';
    import MonthItem from '@/components/MonthItem.vue'; // @ is an alias to /src
    import moment from 'moment';

    @Component({
        components: {
            MonthItem,
        },
    })
    export default class Home extends Vue {
        public dateCtx : any = moment();

        get monthString() : Array<string> {
            let str : any;
            const monthArray : Array<string> = [];

            for (let i=1; i<13; i++) {
                if (i < 10) str = `0${i}`;
                else str = i;
                monthArray.push(str.toString())
            }
            return monthArray
        }

    }
</script>
<style lang="scss" scoped>
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

        }
    }
</style>

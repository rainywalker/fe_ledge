<template>
    <div class="home">
        <h1 data-title>YoonJ HouseHold Ledge</h1>
        <div data-wrap>
            <div class="btnArea">
                <el-button  icon="el-icon-arrow-left" @click="prevYear" circle size="mini"></el-button>
                <span data-year><strong>{{year}}</strong></span>
                <el-button  icon="el-icon-arrow-right" @click="nextYear" circle size="mini"></el-button>
            </div>
            <ul data-month>
                <month-item  v-for="(item,i) in monthString" :key="i" :item="item" :dateCtx="dateCtx" :currentYear="year"></month-item>
            </ul>
        </div>
    </div>
</template>

<script lang="ts">
    import {Component, Vue} from 'vue-property-decorator';
    import MonthItem from '@/components/MonthItem.vue'; // @ is an alias to /src
    import {imgSet} from '@/assets/imgSet';
    import moment from 'moment';


    @Component({
        components: {
            MonthItem,
        },
    })
    export default class Home extends Vue {
        public dateCtx : any = moment();

        get monthString() : Array<object> {
            let str : any;
            const monthArray : Array<object> = [];

            for (let i=0; i<12; i++) {
                if (i < 10) {
                    let incre = i+1;
                    incre < 10 ? str = `0${incre}` : str = `${incre}`
                }
                else str = i+1;
                monthArray.push({
                    label : str.toString(),
                    img : imgSet[i]
                })
            }
            return monthArray
        }
        get currentDate() {
            return this.dateCtx.get('date')
        }
        get year() {
            return this.dateCtx.format('Y')
        }
        get month() {
            return this.dateCtx.format('MMMM')
        }
        get daysInMonth() {
            return this.dateCtx.daysInMonth()
        }
        prevYear() {
            this.dateCtx = moment(this.dateCtx).subtract(1, 'y');
        }

        nextYear() {
            this.dateCtx = moment(this.dateCtx).add(1, 'y');
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
            font-size:40px;padding:0 20px;color:#333;
        }
        [data-month] {
            display: flex;flex-wrap: wrap;padding:40px 0;justify-content: center;

        }
    }
</style>

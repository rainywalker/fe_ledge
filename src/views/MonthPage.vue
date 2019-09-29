<template>
    <div class="monthPage">
        <button type="button" @click="go">ok</button>
        <ul>
            <test :testData="item" @emitActive="onActive" :activeParent="activeParent" v-for="(item ,i) in testData" :key="i"></test>
        </ul>
    </div>
</template>

<script lang="ts">
    import {Component, Vue} from 'vue-property-decorator';
    import Test from '@/components/Test.vue';

    @Component({
        components : {
            Test
        }
    })
    export default class MonthPage extends Vue {
        public activeParent : any = false;
        public testData : any = [
            {
                label : 'test1',
            },
            {
                label : 'test1',
            },
            {
                label : 'test1',
            },
        ]
        onActive(v:any) {
            this.activeParent = v
        }
        go() {
            this.activeParent = false;

        }



    }
</script>

<style scoped lang="scss">

</style>

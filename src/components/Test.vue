<template>
    <li>

        <input  :class="{activeEnabled:bindText}" v-model="bindString" type="text" >
    </li>
</template>

<script lang="ts">
    import {Component, Prop,PropSync, Vue} from 'vue-property-decorator';
    @Component
    export default class Test extends Vue{
        @Prop(Object) testData !: any;
        // @PropSync('activeParent', {type:Boolean}) syncedName !: boolean
        @Prop(Boolean) activeParent !: boolean

        public isActive : boolean = this.activeParent
        public itemData : any = this.testData;
        get bindString() {
            return this.itemData.label
        }
        set bindString(v) {
            this.isActive = true
            this.$emit('emitActive',true)
            this.itemData.label = v
        }
        get bindText() {
            console.log(this.activeParent)
            if(!this.activeParent) this.isActive = false;

            return this.isActive
        }
        activeTrigger(v : any) {


        }

    }
</script>

<style scoped lang="scss">
    .activeEnabled{
        background: #a0cfff;
    }
</style>

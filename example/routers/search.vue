<template>
    <yd-layout title="Search">
        <p class="demo-search-title">行内模式：</p>
        <yd-search v-model="value1" :onSubmit="submitHandler"></yd-search>

        <p class="demo-search-title">全屏模式（带匹配结果）：</p>
        <yd-search :result="result" fullpage v-model="value2" :itemClick="clickHandler" :onSubmit="submitHandler"></yd-search>
    </yd-layout>
</template>

<script type="text/babel">
    export default {
        data() {
            return {
                value1: '',
                value2: '',
                result: []
            }
        },
        methods: {
            getResult(val) {
                if (!val) return [];
                return [
                    'Apple', 'Banana', 'Orange', 'Durian', 'Lemon', 'Peach', 'Cherry', 'Berry',
                    'Core', 'Fig', 'Haw', 'Melon', 'Plum', 'Pear', 'Peanut', 'Other'
                ].filter(value => new RegExp(val, 'i').test(value));
            },
            clickHandler(item) {
                this.$dialog.toast({mes: `搜索：${item}`});
            },
            submitHandler(value) {
                this.$dialog.toast({mes: `搜索：${value}`});
            }
        },
        watch: {
            value2(val) {
                this.result = this.getResult(val);
            }
        }
    }
</script>

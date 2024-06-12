<template>
    <div class="tabsPanelMain">
        <my-tabs :tabs="tabs" position="top" card border>
            <!-- <div v-for="(item, index) in tabs" :key="index">{{ item }}</div> -->
            <!-- <template v-slot="{ tab }">{{ tab.label }} 占位内容</template> -->
            <my-select :options="options" @change="optionsChange"></my-select>
        </my-tabs>
    </div>
</template>

<script>
export default {
    data() {
        return {
            tabs: [
                { name: '基础参数', label: '基础参数' },
                { name: '老化', label: '老化' },
                { name: '主文字', label: '主文字' },
                { name: '副文字', label: '副文字' },
                { name: '底部文字', label: '底部文字' },
                { name: '外边线', label: '外边线' },
                { name: '内边线', label: '内边线' },
                { name: '中心内容', label: '中心内容' },
                { name: '防伪码', label: '防伪码' }
            ],
            options: [
                {
                    label: '160*160(默认大小)',
                    value: 160
                },
                {
                    label: '320*320(更清晰)',
                    value: 320
                },
                {
                    label: '480*480(更清晰)',
                    value: 480
                }
            ]
        }
    },
    methods: {
        optionsChange(data) {
            console.log(data)
            this.$emit('currentSize', data)
        }
    }
}
</script>

<style lang="scss" scoped>
.tabsPanelMain {
    width: 100%;
    height: 100%;
    // height: 50vh;
    // background: red;
    border-radius: 10px;
}
::v-deep .my-tabs__body {
    height: 45vh;
    padding: 5px;
}
// ::v-deep .my-tabs__body {
//     padding: 0;
// }
</style>

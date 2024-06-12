<template>
    <div class="CreateSealsPanel">
        <el-row :gutter="50">
            <el-col :span="24">
                <div class="title">
                    在线印章生成器
                </div>
            </el-col>
            <el-col :span="16">
                <div class="operatePanel">
                    <TabsPanel />
                </div>
            </el-col>
            <el-col :span="8">
                <div class="operatePanel">
                    <CanvasPanel />
                </div>
            </el-col>
        </el-row>
    </div>
</template>

<script>
import CanvasPanel from './components/canvasPanel.vue'
import TabsPanel from './components/tabsPanel.vue'
export default {
    data() {
        return {}
    },
    components: {
        CanvasPanel,
        TabsPanel
    }
}
</script>

<style lang="scss" scoped>
.CreateSealsPanel {
    background: #fff;
    border-radius: 10px;
    padding: 0px 20px 20px 20px;
}
.el-row {
    margin-bottom: 20px;
    &:last-child {
        margin-bottom: 0;
    }
}
.el-col {
    border-radius: 10px;
}
.title {
    text-align: center;
    font-weight: bold;
    font-size: 22px;
    line-height: 44px;
    padding: 2px 0;
}
.operatePanel {
    border-radius: 10px;
    border: 3px dashed orange;
    height: 50vh;
    // overflow-y: auto;
}
</style>

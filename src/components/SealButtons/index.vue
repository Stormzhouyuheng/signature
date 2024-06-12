<template>
    <div class="container">
        <div class="grid-container">
            <div
                v-for="(item, index) in buttons"
                :key="index"
                :class="[
                    'grid-item',
                    {
                        hover: hoveredItem === index,
                        active: activeItem === index
                    }
                ]"
                @mouseover="hoveredItem = index"
                @mouseleave="hoveredItem = null"
                @click="activeItem = index"
            >
                {{ item.label }}
            </div>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            buttons: [
                {
                    label: '圆形印章'
                },
                {
                    label: '公章印章'
                },
                {
                    label: '分公司印章'
                },
                {
                    label: '合同专用章'
                },
                {
                    label: '业务专用章'
                },
                {
                    label: '椭圆印章'
                },
                {
                    label: '圆形印章'
                },
                {
                    label: '公章印章'
                },
                {
                    label: '分公司印章'
                },
                {
                    label: '合同专用章'
                },
                {
                    label: '业务专用章'
                },
                {
                    label: '椭圆印章'
                },

                {
                    label: '圆形印章'
                },
                {
                    label: '公章印章'
                },
                {
                    label: '分公司印章'
                },
                {
                    label: '合同专用章'
                },
                {
                    label: '业务专用章'
                },
                {
                    label: '椭圆印章'
                },
                {
                    label: '圆形印章'
                },
                {
                    label: '公章印章'
                },
                {
                    label: '分公司印章'
                },
                {
                    label: '合同专用章'
                },
                {
                    label: '业务专用章'
                },
                {
                    label: '椭圆印章'
                },
                {
                    label: '圆形印章'
                },
                {
                    label: '公章印章'
                },
                {
                    label: '分公司印章'
                },
                {
                    label: '合同专用章'
                },
                {
                    label: '业务专用章'
                },
                {
                    label: '椭圆印章'
                },
                {
                    label: '圆形印章'
                },
                {
                    label: '公章印章'
                },
                {
                    label: '分公司印章'
                },
                {
                    label: '合同专用章'
                },
                {
                    label: '业务专用章'
                },
                {
                    label: '椭圆印章'
                }
            ],
            hoveredItem: null,
            activeItem: null
        }
    },
    methods: {}
}
</script>

<style lang="scss" scoped>
.container {
    width: 100%;
    margin: 0 auto;
    padding: 20px 0;
}

.grid-container {
    display: grid;
    grid-template-columns: repeat(12, 1fr);
}

.grid-item {
    border-left: 2px dashed #4caf50; /* 左边框 */
    border-top: 2px dashed #4caf50; /* 上边框 */
    color: #333;
    padding: 15px 20px;
    font-size: 16px;
    text-align: center;
    box-sizing: border-box; /* 保证边框在内 */
    transition: background-color 0.3s; /* 添加平滑过渡效果 */
}

.grid-item:last-child {
    border-left: 2px dashed #4caf50;
    border-top: 2px dashed #4caf50;
    border-right: 2px dashed #4caf50;
    border-bottom: 2px dashed #4caf50;
}

.grid-item:nth-child(12n + 1) {
    border-left: 2px dashed #4caf50; /* 保留所有格子的左边框（包括外层） */
}

.grid-item:nth-child(-n + 12) {
    border-top: 2px dashed #4caf50; /* 保留所有格子的上边框（包括外层） */
}

.grid-container > .grid-item:nth-child(12n) {
    border-right: 2px dashed #4caf50; /* 每行最后一个格子的右边框 */
}

.grid-container > .grid-item:nth-last-child(-n + 12) {
    border-bottom: 2px dashed #4caf50; /* 最后一行所有格子的底部边框 */
}

.grid-item.hover {
    background-color: rgb(173, 173, 173); /* 鼠标悬停高亮 */
    // color: #fff;
    cursor: pointer;
}

.grid-item.active {
    background-color: #4caf50; /* 点击激活高亮 */
    color: #fff;
}
</style>

<template>
    <div class="canvasPanelMain">
        <div>
            <el-row>
                <el-col :span="24">
                    <div class="grid-content bg-purple-dark">
                        实时预览：
                    </div>
                    <div class="container">
                        <my-watermark
                            :text="text"
                            :color="'#cfd2d5'"
                            :lineHeight="50"
                            :mask="false"
                            :rotate="20"
                            :x="150"
                        >
                            <canvas
                                ref="sealCanvas"
                                width="400"
                                height="400"
                            ></canvas>
                        </my-watermark>
                    </div>
                </el-col>
            </el-row>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            text: ['水印1', '水印2', '水印3']
        }
    },
    methods: {
        drawSeal() {
            const canvas = this.$refs.sealCanvas
            const ctx = canvas.getContext('2d')
            const centerX = canvas.width / 2
            const centerY = canvas.height / 2
            const radius = centerY - 10

            // 绘制外圆
            ctx.beginPath()
            ctx.arc(centerX, centerY, radius, 0, 2 * Math.PI)
            ctx.strokeStyle = 'red'
            ctx.lineWidth = 5
            ctx.stroke()

            // 绘制内圆
            ctx.beginPath()
            ctx.arc(centerX, centerY, radius - 20, 0, 2 * Math.PI)
            ctx.stroke()

            // 绘制五角星
            const starRadius = 50
            this.drawStar(
                ctx,
                centerX,
                centerY,
                5,
                starRadius,
                starRadius / 2.5,
                'red'
            )

            // 绘制顶部弧形文字
            const topText = 'xxx科技有限公司'
            this.drawArcText(ctx, topText, centerX, centerY, radius - 30)

            // 绘制底部直线文字
            const bottomText = '专用章'
            ctx.font = 'bold 24px Arial'
            ctx.textAlign = 'center'
            ctx.fillStyle = 'red'
            ctx.fillText(bottomText, centerX, centerY + radius - 60)
        },
        drawStar(ctx, cx, cy, spikes, outerRadius, innerRadius, color) {
            let rot = (Math.PI / 2) * 3
            let x = cx
            let y = cy
            const step = Math.PI / spikes

            ctx.beginPath()
            ctx.moveTo(cx, cy - outerRadius)
            for (let i = 0; i < spikes; i++) {
                x = cx + Math.cos(rot) * outerRadius
                y = cy + Math.sin(rot) * outerRadius
                ctx.lineTo(x, y)
                rot += step

                x = cx + Math.cos(rot) * innerRadius
                y = cy + Math.sin(rot) * innerRadius
                ctx.lineTo(x, y)
                rot += step
            }
            ctx.lineTo(cx, cy - outerRadius)
            ctx.closePath()
            ctx.lineWidth = 5
            ctx.strokeStyle = color
            ctx.stroke()
            ctx.fillStyle = color
            ctx.fill()
        },
        drawArcText(ctx, text, centerX, centerY, radius) {
            ctx.font = 'bold 22px 宋体'
            ctx.textAlign = 'center'
            ctx.fillStyle = 'red'

            const totalChars = text.length

            // 第一个字符的位置 (240度)
            const firstCharAngle = (4 * Math.PI) / 3 // 240度
            // 最后一个字符的位置 (120度)
            // const lastCharAngle = (2 * Math.PI) / 3 // 120度

            // console.log('(2 * Math.PI) / 3', (2 * Math.PI) / 3);
            // console.log('(1 * Math.PI) / 3', (1 * Math.PI) / 3);

            // 计算字符间的角度步长
            const angleRange = firstCharAngle
            const angleStep = angleRange / (totalChars - 1)

            // 绘制所有字符
            for (let i = 0; i < totalChars; i++) {
                const angle = firstCharAngle + i * angleStep
                this.drawCharacter(
                    ctx,
                    text[i],
                    centerX,
                    centerY,
                    radius - 15,
                    angle
                )
            }
        },
        drawCharacter(ctx, char, centerX, centerY, radius, angle) {
            ctx.save()
            ctx.translate(centerX, centerY)
            ctx.rotate(angle)
            ctx.translate(0, -radius)
            // ctx.rotate(-angle) // 使文字保持正向
            ctx.fillText(char, 0, 0)
            ctx.restore()
        }
    },
    mounted() {
        this.drawSeal()
    }
}
</script>

<style lang="scss" scoped>
.canvasPanelMain {
    width: 100%;
    height: 100%;
    border-radius: 10px;
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
.bg-purple-dark {
    background: #e8e8ea;
}
.grid-content {
    border-radius: 10px 10px 0px 0px;
    min-height: 36px;
    font-size: 15px;
    font-weight: bold;
    line-height: 35px;
    padding: 0 15px;
}
.container {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100%;
    .my-watermark {
        display: flex;
        justify-content: center;
        align-items: center;
    }
}
</style>

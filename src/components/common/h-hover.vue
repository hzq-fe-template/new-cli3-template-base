/*
 * @Author: hzq
 * @Date: 2019-02-12 09:43:50
 * @Last Modified by: hzq
 * @Last Modified time: 2019-07-02 14:28:13
 * @文件说明: 灰色字体，移入手型、变蓝
 */
<template>
    <div class="h-hover cursor inline" :class="(hover||currHover)?hcolor:dcolor" @mouseover="onMouseover" @mouseout="onMouseout">
        <slot/>
    </div>
</template>

<script>
    export default {
        name: 'h-hover',
        props: {
            // 要跳转的路由
            to: {
                type: String,
                default: ''
            },
            // 未移入时的颜色
            dcolor: {
                type: String,
                default: 'c9'
            },
            // 移入时的颜色
            hcolor: {
                type: String,
                default: 'primary'
            },
            // 是否为移入状态
            hover: {
                type: Boolean,
                default: false
            }
        },
        data() {
            return {
                // 当前是否移入
                currHover: false
            }
        },
        computed: {
            listeners() {
                return {
                    ...this.$listeners,
                    click: () => {
                        if (this.to) this.$to(this.to)
                        this.$emit('click')
                    }
                }
            }
        },
        methods: {
            onMouseover() {
                if (!this.hover) {
                    this.currHover = true
                }
            },
            onMouseout() {
                if (!this.hover) {
                    this.currHover = false
                }
            }
        }
    }
</script>

<style lang='scss' scoped></style>

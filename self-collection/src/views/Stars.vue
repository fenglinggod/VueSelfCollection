<template>
    <article class="stars">
        <div v-for="n in starCount" :key="n" class="star" ref="star"></div>
    </article>
</template>
<script>
export default {
    name: 'Stars',
    data(){
        return {
            starCount: 800,
            dis: 800
        }
    },
    computed: {
        totalHeight(){
            return document.clientHeight
        }
    },
    mounted(){
        let starArr = this.$refs.star;
        starArr.forEach(el => {
            let speed = 0.2 + Math.random()
            let changedDis = this.dis + Math.random()*300
            el.style.transformOrigin = `0 0 ${changedDis}px`
            el.style.transform = `translate3d(0,0,-${changedDis}px) rotateY(${Math.random()*360}deg) rotateX(${Math.random()*(-50)}deg) scale(${speed},${speed})`
        });
    }
}
</script>
<style lang="less" scoped>
@keyframes rotate {
    0%{
        transform: perspective(400px) rotateZ(20deg) rotateX(-40deg) rotateY(0)
    }
    10%{
        transform: perspective(400px) rotateZ(20deg) rotateX(-40deg) rotateY(-360deg)
    }
}
.stars {
    transform: perspective(500px);
    transform-style: preserve-3d;
    position: absolute;
    perspective-origin: 50% 100%;
    animation: rotate 90s infinite linear;
    bottom: 0;

    .star {
        width: 2px;
        height: 2px;
        background: #f7f7b8;
        background-clip: content-box;
        border-radius: 50%;
        overflow: hidden;
        position: absolute;
        top: 0;
        left: 0;
        backface-visibility: hidden;
    }
}
</style>
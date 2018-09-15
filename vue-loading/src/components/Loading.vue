<template>
    <div class="loading" :style="loadingStyle">
        <div
            v-for="(dotNum, index) in dotNums"
            :key="index"
            :style="[doTranslate(index, dotNums), dotStyle]"
        ><span :style="[doAnimationDelay(index, dotNums), dotStyle]"></span></div>
    </div>
</template>

<script>
export default {
    props: {
        loadingRadiusVal: {
            type: Number,
            required: true,
            deafult: 168
        },
        dotRadiusVal: {
            type: Number,
            required: true,
            deafult: 24
        },
        dotColorVal: {
            type: String,
            required: true,
            deafult: '#d8d8d8'
        },
        dotNums: {
            type: Number,
            required: true,
            deafult: 12
        }
    },
    computed: {
        loadingStyle() {
            return {
                height: `${this.loadingRadiusVal}px`,
                width: `${this.loadingRadiusVal}px`,
                color: this.dotColorVal
            };
        },
        dotStyle() {
            return {
                height: `${this.dotRadiusVal}px`,
                width: `${this.dotRadiusVal}px`,
            };
        }
    },
    methods: {
        doTranslate(index, dotNums) {
            const rad = 2 * Math.PI / dotNums * index;
            const dotX = Math.cos(rad) * this.loadingRadiusVal / 2;
            const dotY = Math.sin(rad) * this.loadingRadiusVal / 2;
            return {
                transform: `translate(${dotX}px, ${dotY}px)`
            };
        },
        doAnimationDelay(index, dotNums) {
            const delayTime = `${1 + (index + 1) * 1 / dotNums}s`;
            return {
                animationDelay: delayTime
            };
        }
    }
}
</script>

<style scoped>
.loading {
    position: relative;
    font-size: 0;
    border-radius: 50%;
    transform-origin: center;
}
.loading div {
    position: absolute;
    top: 50%;
    left: 50%;
    border-radius: 100%;
}
.loading span {
    display: block;
    background-color: currentColor;
    border: 0 solid currentColor;
    border-radius: 100%;
    animation: ball-spin 1s infinite ease-in-out;
}

@keyframes ball-spin {
    0%,
    100% {
        opacity: 1;
        transform: scale(1);
    }
    20% {
        opacity: 1;
    }
    80% {
        opacity: 0;
        transform: scale(0);
    }
}

</style>

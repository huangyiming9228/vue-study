<template>
    <section>
        <h1>🍺 Make yourself some Punk Beers 🍻</h1>
        <div v-if="beers.length === 0" class="loading">Loading...</div>
        <div v-for="(beer, index) in beers" :key="index" class="beer-contain">
            <div class="beer-img">
                <img :src="beer.img" height="350" />
            </div>
            <div class="beer-info">
                <h2>{{ beer.name }}</h2>
                <p class="bright">{{ beer.tagline }}</p>
                <p><span class="bright">Description:</span> {{ beer.desc }}</p>
                <p><span class="bright">Tips:</span> {{ beer.tips }}</p>
                <h3 class="bright">Food Pairings</h3>
                <ul>
                    <li v-for="(item, index) in beer.food" :key="index">
                    {{ item }}
                    </li>
                </ul>
            </div>
        </div>
    </section>
</template>

<script>
export default {
    name: 'InfiniteScroll',
    data() {
        return {
            bottom: false,
            beers: []
        };
    },
    watch: {
        bottom(bottom) {
            console.log(bottom);
            if(bottom) {
                this.addBear();
            }
        }
    },
    created() {
        window.addEventListener('scroll', () => {
            this.bottom = this.bottomVisible();
        })
        this.addBear();
    },
    methods: {
        bottomVisible() {
            // 可视区高度
            const clientHeight = document.documentElement.clientHeight;
            // 元素内容高度
            const scrollHeight = document.documentElement.scrollHeight;
            // 垂直方向的滚动距离
            const scrollY = window.scrollY;

            // +1计算丢失的精度
            const bottomOfPage = clientHeight + scrollY + 1 >= scrollHeight;
            return bottomOfPage || scrollHeight < clientHeight;
        },
        addBear() {
            this.axios.get('https://api.punkapi.com/v2/beers/random')
                .then(resposne => {
                    let api = resposne.data[0];
                    let apiInfo = {
                        name: api.name,
                        desc: api.description,
                        img: api.image_url,
                        tips: api.brewers_tips,
                        tagline: api.tagline,
                        food: api.food_pairing
                    }
                    this.beers.push(apiInfo);
                    if(this.bottomVisible()){
                        this.addBear();
                    }
                })
        }
    }
}
</script>

<style lang="scss">
h1, h2, h3, h4 {
    font-family: 'Fjalla One', sans-serif;
}

h1 {
    margin-top: 40px;
    color: white;
    text-align: center;
}

.loading {
    color: white;
    text-align: center;
    font-size: 20px;
}

.display {
    display: flex;
    justify-content: center;
    align-content: center;
}

.beer-contain {
    @extend .display;
    width: 50%;
    margin: 20px 24%;
    box-shadow: 0 2px 3px 1px rgba(30, 0, 0, 0.1);
}

.beer-img {
    @extend .display;
    padding: 30px;
    background: #FF6542;
    border: 1px solid #88498F;
    border-right: 1px solid #f44822;
}

.beer-info {
    background: #564154;
    color: white;
    padding: 30px;
    border: 1px solid #88498F;
    .bright {
        color: #fcd7cf;
        font-family: 'Contrail One', sans-serif;
    }
}

h3 {
    margin-bottom: 5px;
}

ul {
    margin-top: 5px;
}
</style>

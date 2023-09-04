<template>
  <Start v-if="top" class="start"></Start>
  <div v-else class="count">
    <div class="count__msg">
        <p>Retrouvez-nous à la <a href="https://goo.gl/maps/BJ9yn72wMZ3DxYsHA">ferme</a> dans</p>
    </div>
    <div class="counter">
        <div class="counter__block">
            <div class="counter__block__num">
                <span v-if="days < 10">0</span>
                <span>{{ days }}</span>
            </div>
            <p class="counter__block__txt">Jours</p>
        </div>
        <div class="counter__block">
            <div class="counter__block__num">
                <span v-if="hours < 10">0</span>
                <span>{{ hours }}</span>
            </div>
            <p class="counter__block__txt">Heures</p>
        </div>
        <div class="counter__block">
            <div class="counter__block__num">
                <span v-if="minutes < 10">0</span>
                <span>{{ minutes }}</span>
            </div>
            <p class="counter__block__txt">Minutes</p>
        </div>
        <div class="counter__block">
            <div class="counter__block__num">
                <span v-if="seconds < 10">0</span>
                <span>{{ seconds }}</span>
            </div>
            <p class="counter__block__txt">Secondes</p>
        </div>
    </div>
    
  </div>
</template>

<script>
import Start from "./Start.vue"

export default {
    components: {
        Start
    },
    data () {
        return {
            top: false,
            now: 0,
            stop: 0,
            seconds: 0,
            minutes: 0,
            hours: 0,
            days: 0,
        }
    },
    watch: {
        top(value) {
            if (value)
            {
                document.getElementById("app").classList.add('none');
            }
        },
        now: {
            handler(value) {
                if (value < this.stop) {
                    this.top = false;
                    setTimeout(() => {
                        this.now = new Date().getTime();
                        let rest = ~~((this.stop - this.now) / 1000);
                        this.days = ~~(rest / 86400);
                        rest = rest % 86400;
                        this.hours = ~~(rest / 3600);
                        rest = rest % 3600;
                        this.minutes = ~~(rest / 60);
                        rest = rest % 60;
                        this.seconds = rest;
                    }, 100);
                }
                else
                {
                    this.top = true;
                }
            },
            immediate: true
        }
    },
    mounted() {
        document.getElementById("app").classList.remove('none');
        this.now = new Date().getTime();
        this.stop = this.now + 2000;
        this.stop = new Date('September 16, 2023 14:00:00').getTime();
        //this.stop = new Date('September 4, 2023 14:00:00').getTime();
        if (this.now >= this.stop)
        {
            this.top = true;
            document.getElementById("app").classList.add('none');
        }
        let rest = ~~((this.stop - this.now) / 1000);
        this.days = ~~(rest / 86400);
        rest = rest % 86400;
        this.hours = ~~(rest / 3600);
        rest = rest % 3600;
        this.minutes = ~~(rest / 60);
        rest = rest % 60;
        this.seconds = rest;
    }
}
</script>

<style scoped>

.count {
    display: flex;
    flex-direction: column;
    gap: 0.3em;
    font-size: 8em;
}

.count__msg {
    text-align: center;
    position: relative;
    z-index: 10;
    font-size: 0.5em;
}

.count__msg p {
    font-family: 'Handlee';
}

.counter {
    max-width: 100vw;
    column-gap: 3%;
    display: flex;
    justify-content: center;
    font-family: 'Fira Mono';
    margin-bottom: 0.7em;
}
.counter__block {
    width: max-content;
    padding: 0.25em 0.15em;
    position: relative;
    z-index: 10;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center
}

.counter__block::before {
    content: "";
    display: block;
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    border-radius: 0.2em;
    background-color: #FFFFFF90;
    backdrop-filter: blur(1em);
    z-index: -1;
}

.counter__block__num {
    text-align: center;
}

.counter__block__txt {
    font-size: 0.1em;
}

@media screen and (max-width: 1000px)
{
    .count {
        font-size: 3em;
    }
}

@media screen and (max-width: 320px)
{
    .count {
        font-size: 2em;
    }
}
</style>

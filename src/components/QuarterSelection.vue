<template>
    <div class="placeholder">
        <div class="cursor" @click="prevQuarter">prev<ConfettiExplosion v-if="visibleLeft" :stageWidth="500" :particleCount="200" :force="0.3"/></div>
        <div class="date">
            Quarter {{ quarter.number }} - {{ quarter.year }}
        </div>
        <div class="cursor" @click="nextQuarter">next<ConfettiExplosion v-if="visibleRight" :stageWidth="500" :particleCount="200" :force="0.3"/></div>
    </div>
    <div class="log placeholder">
        <div class="inline">
            <div class="header">
                <div>
                    <b>Start:</b>
                    {{ quarter.range.start.toLocaleDateString() }}
                </div>
                <div>
                    <b>End:</b>
                    {{ quarter.range.end.toLocaleDateString() }}
                </div>
            </div>
            <div class="code">
                <b>Payload:</b>
                <textarea readonly cols="30" rows="10">{{ quarter }}</textarea>
            </div>
        </div>
    </div>
</template>

<script setup>

import { computed, ref, nextTick } from 'vue'
import ConfettiExplosion from "vue-confetti-explosion";

  const visibleLeft = ref(false);
  const visibleRight = ref(false);

  const explodeLeft = async () => {
    visibleLeft.value = false;
    await nextTick();
    visibleLeft.value = true;
  };
  const explodeRight = async () => {
    visibleRight.value = false;
    await nextTick();
    visibleRight.value = true;
  };

let cursor = ref(new Date())

const q = [4, 1, 2, 3]

let qCalc = q[Math.floor((cursor.value.getMonth() / 3))];

let actualQuarter = () => {
    const startFullQuarterActual = new Date(cursor.value.getFullYear(), Math.floor((cursor.value.getMonth() / 3)) * 3, 1);
    const endFullQuarterActual = new Date(startFullQuarterActual.getFullYear(), startFullQuarterActual.getMonth() + 3, 0);
    return { "start": startFullQuarterActual, "end": endFullQuarterActual }
}

const quarter = computed(() => {
    return {
        "number": qCalc,
        "year": qCalc == 4 ? cursor.value.getFullYear() - 1 : cursor.value.getFullYear(),
        "range": actualQuarter()
    };
})

let nextQuarter = () => {
    cursor.value = new Date(cursor.value.setMonth(cursor.value.getMonth() + 3))
    qCalc = q[Math.floor((cursor.value.getMonth() / 3))];
    explodeRight();
}

let prevQuarter = () => {
    cursor.value = new Date(cursor.value.setMonth(cursor.value.getMonth() - 3))
    qCalc = q[Math.floor((cursor.value.getMonth() / 3))];
    explodeLeft();
}


</script>

<style scoped>
@media only screen and (min-device-width: 300px) and (max-device-width: 600px) {
    .placeholder {
        width: 90% !important;
    }
}

.placeholder {
    margin-left: auto;
    margin-right: auto;
    width: 50%;
    display: flex;
    justify-content: space-between;
    border: 1px solid;
    padding: 5px;
    border-radius: 10px;
    margin-top: 10px;
}

.cursor {
    cursor: pointer;
    border: 1px solid #191929;
    padding: 10px;
    border-radius: 10px;
    background: rgb(176 176 196);
    color: #191929;
}

.cursor:hover {
    background: rgb(3, 144, 168);
}

.date {
    padding: 10px;
    color: white;
}

.log {
    margin-top: 10px;
    justify-content: center;
}

.inline div {
    margin: 10px;
    color: white;
    text-align: center;
}

textarea {
    background: rgb(25, 25, 41);
    color: #00b22f;
    border: 0px;
    width: 95%;
    margin-top: 20px;
    resize: none;
    outline: none;
    -webkit-box-shadow: none;
    -moz-box-shadow: none;
    box-shadow: none;
    font-size: 13px;
}

.code {
    text-align: left !important;
    border: 1px solid #009134;
    padding: 10px;
    border-radius: 5px;
}

.header {
    border: 1px solid #191929;
    border-radius: 5px;
    background: #2e2e4e;
    margin-bottom: 15px !important;
}

particle {
    border-radius: 50%;
    left: 0;
    pointer-events: none;
    position: fixed;
    top: 0;
}
</style>
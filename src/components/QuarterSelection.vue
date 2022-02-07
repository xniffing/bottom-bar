<template>
    <div class="placeholder">
        <div class="cursor" @click="prevQuarter">prev</div>
        <div class="date">Quarter {{ quarter.number }} - {{ quarter.year }}</div>
        <div class="cursor" @click="nextQuarter">next</div>
    </div>
    <div class="log placeholder">
        <div class="inline">
            <div>
                <b>Start:</b>
                {{ quarter.range.start.toLocaleDateString() }}
            </div>
            <div>
                <b>End:</b>
                {{ quarter.range.end.toLocaleDateString() }}
            </div>
        </div>
    </div>
</template>

<script setup>

import { computed, ref } from 'vue'

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
}

let prevQuarter = () => {
    cursor.value = new Date(cursor.value.setMonth(cursor.value.getMonth() - 3))
    qCalc = q[Math.floor((cursor.value.getMonth() / 3))];
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
}
</style>
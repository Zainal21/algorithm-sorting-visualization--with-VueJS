<template>
<div id="app">
    <button class="btn btn-primary" v-on:click="start">Start</button>
    <div class="sort-list">
        <sort algorithm="QuickSort" :inarr="qsArray"></sort>
    </div>
</div>
</template>

<script>
import Vue from 'vue'
import sort from './Sort.vue'

const initialArr = [2, 42, 3, 19, 6, 32, 15, 7, 49, 30, 38, 36, 17, 2, 14, 46, 39, 41, 3, 44, 4, 1, 22, 29, 22, 23, 8, 33, 10, 16, 48, 31, 34, 12, 27, 40, 20, 35, 21, 25];

let data = {
    qsArray: [initialArr, 0, initialArr.length -1],
    // bsArray: [initialArr, 0, 1]
};
let results;

import qs from './QuickSort'

var start = function() {
    var data = visualize(data.qsArray, qs(initialArr.slice()));
    console.log(data)
    visualize(data.bsArray, bs(initialArr.slice()));
}

var visualize = function(resArray, results) {
    console.log('visualize', results);
    let ticks = setInterval(function() {
        if (results.length) {
            var res = results.shift();
            Vue.set(resArray, 0, res[0]);
            Vue.set(resArray, 1, res[1]);
            Vue.set(resArray, 2, res[2]);
        } else {
            clearInterval(ticks);
        }
    }, 100);
}

export default {
    name: 'App',
    data: function() {
        var res = data;
        return res;
    },
    methods: {
        start: start
    },
    components: {
        sort
    },
};

</script>


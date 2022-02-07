<template>
<trading-vue :data="this.$data"></trading-vue>
</template>
<script>

import TradingVue from 'trading-vue-js'
import axios from 'axios'

export default {
    name: 'app',
    components: { TradingVue },
    data() {
        return {
            ohlcv: [
              [1600646400000, 10920.28, 10988.86, 10296.35, 10417.22],
              [1600732800000, 10417.22, 10572.71, 10353, 10529.61],
              [1600819200000, 10529.61, 10537.15, 10136.82, 10241.46],
              [1600905600000, 10241.46, 10795.24, 10190.93, 10736.32],
              [1600992000000, 10736.33, 10760.53, 10556.24, 10686.67],
                // [ 1551128400000, 33,  37.1, 14,  14,  196 ],
                // [ 1551132000000, 13.7, 30, 6.6,  30,  206 ],
                // [ 1551135600000, 29.9, 33, 21.3, 21.8, 74 ],
                // [ 1551139200000, 21.7, 25.9, 18, 24,  140 ],
                // [ 1551142800000, 24.1, 24.1, 24, 24.1, 29 ],
            ]
        }
    },
    mounted() {
      console.log(this.ohlcv);
      axios.get('http://127.0.0.1:8000/forex/btceth').then(response => (this.ohlcv = response.data));
      // axios.get('http://127.0.0.1:8000/crypto/btc').then(response => (this.ohlcv = response.data));
      // axios.get('http://127.0.0.1:8000/crypto/btc').then(function(response) {
      //   console.log(response);
      // });
    }
}

</script>

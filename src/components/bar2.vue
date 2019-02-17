<template>
  <div  :style="{paddingLeft: '20px',paddingRight:'20px'}">

    <template>
        <div class="gutter-example">
            <a-row :gutter="16">
            <a-col class="gutter-row" :span="6">
                <div class="gutter-box">
                    <zc></zc>
                    <market></market>
                    <announcement></announcement>
                </div>
            </a-col>
            
            <a-col class="gutter-row" :span="18">
                <div class="gutter-boxset"  style="margin-bottom:20px;border-radius: 6px 6px 0 0;padding:10px;">
                    <div>
                        <div class="s1d711xa-1 jgsWFi s1p4en3j-0 ghSPYW s62mpio-0 cTnfIm">
                            <div class="s1p4en3j-1 txlto s62mpio-0 iLeqAn" direction="column" wrap="nowrap">
                                <div class="s1p4en3j-2 eBcVXx s62mpio-0 dBSZfv">最新价</div>
                                <div>
                                    <span class="s1p4en3j-5 djLwBB s1p4en3j-3 hyOgjG">6,835.60</span>
                                    <span class="s1p4en3j-3 hyOgjG">
                                        <span class="s1p4en3j-6 kVsvyQ">
                                            <span>¥47,332.43</span>
                                        </span>
                                    </span>
                                </div>
                            </div>
                            <div class="s1p4en3j-1 txlto s62mpio-0 iLeqAn" direction="column" wrap="nowrap">
                                <div class="s1p4en3j-2 eBcVXx s62mpio-0 dBSZfv">24h涨跌</div>
                                <div style="color: #5FB84A; !important">
                                    <span class="s1p4en3j-5 djLwBB s1p4en3j-3 hyOgjG" style="color: #5FB84A; !important">-151.60</span>
                                    <span class="s1p4en3j-5 djLwBB s1p4en3j-3 hyOgjG" style="color: #5FB84A; !important">&nbsp;&nbsp;-2.17%</span>
                                </div>
                            </div>
                            <div class="s1p4en3j-1 txlto s62mpio-0 iLeqAn" direction="column" wrap="nowrap">
                                <div class="s1p4en3j-2 eBcVXx s62mpio-0 dBSZfv">24h最高价</div>
                                <span class="s1p4en3j-3 hyOgjG">7,120.41</span>
                            </div>
                            <div class="s1p4en3j-1 txlto s62mpio-0 iLeqAn" direction="column" wrap="nowrap">
                                <div class="s1p4en3j-2 eBcVXx s62mpio-0 dBSZfv">24h最低价</div>
                                <span class="s1p4en3j-3 hyOgjG">6,650.00</span>
                            </div>
                            <div class="s1p4en3j-1 txlto s62mpio-0 iLeqAn" direction="column" wrap="nowrap">
                                <div class="s1p4en3j-2 eBcVXx s62mpio-0 dBSZfv">24h成交量</div>
                                <span class="s1p4en3j-3 hyOgjG">411,411,181.50 USDT</span>
                            </div>
                        </div>
                    </div>

                </div>
                <div style="margin-bottom:20px;">
                    <div id="trade-view" style="width: 100%;height: 636px;"></div>
                </div>
                <!-- 买入卖出 -->
                <div :style="{height:'400px',borderRadius: '6px;',margin:'5px'}">
                    <a-row :gutter="10">
                        <a-col :span="16" >
                            <mairumaichu></mairumaichu>
                        </a-col>
                        <a-col :span="8" >
                            <newdata></newdata>
                        </a-col>
                    </a-row>
                    
                </div>
                <!-- 委托 -->
                <div :style="{height:'401.364px'}">
                    <a-row>
                        <a-col :span="16">
                            <commission></commission>
                            <depth></depth>
                            
                        </a-col>
                        <a-col :span="8">
                            <realt></realt>
                        </a-col>
                    </a-row>
                </div>
            </a-col>
            
            </a-row>
        </div>
    </template>
    
  </div>
</template>

<script>
import { widget as TvWidget } from '../../static/tradingview/charting_library/charting_library.min';
// import datafeeds from '../lib/socketDatafeed';
import {UDFCompatibleDatafeed} from '../../static/tradingview/datafeeds/udf/lib/udf-compatible-datafeed';


import mairumaichu from './mairumaichu/index.vue';
import newdata from './newdata/index.vue';
import commission from './commission/index.vue';
import realt from './realt/index.vue';
import depth from './depth/index.vue';
import zc from './zc/index.vue';
import market from './market/index.vue';
import announcement from './announcement/index.vue';

// 图表显示项配置
const chartDisabledFeatures = [
    'header_symbol_search',
    'left_toolbar',
    'header_screenshot',
    'header_widget_dom_node',
    "header_resolutions",
    "header_fullscreen_button",
    'timeframes_toolbar',
    // 'edit_buttons_in_legend',
    'pane_context_menu',
    'legend_context_menu',
    'volume_force_overlay'
];
export default {
    name: 'bar2',
     components: {
        mairumaichu,
        newdata,
        commission,
        realt,
        depth,
        zc,
        market,
        announcement,
        ops: {
            vuescroll: {},
            scrollPanel: {},
            rail: {},
            bar: {}
          }
    },
    data () {
        return {
        msg: 'Welcome to Your Vue.js App',
        client: null,
            subscription: null,
            list:[],
            listStash: [],
            widget: null,
            datafeeds: new UDFCompatibleDatafeed("https://demo_feed.tradingview.com"),
            // datafeeds: new datafeeds(this),
            // datafeeds: null,
            exchange: null,
            symbol: null,
            interval: '1min',
            ticker: null,
            cacheData: {},
            lastTime: null,
            lastInterval: null,
            lastLength: 0,
            getBarTimer: null,
            isLoading: true,
            intervalOptions: [{
                name: '1min',
                value: '1min'
            }, {
                name: '5min',
                value: '5min'
            }, {
                name: '15min',
                value: '15min'
            }, {
                name: '30min',
                value: '30min'
            }, {
                name: '60min',
                value: '60min'
            }, {
                name: '日线',
                value: '1day'
            }, {
                name: '周线',
                value: '1week'
            }]
        }
    },
    created() {
       

    },
    mounted() { 
        this.init();
    },
    computed: {
        
    },
    watch:{
    
    }, 
    methods: {
       init() {
            // this.exchange = exchange;
            // this.symbol = symbol
            // this.interval = interval
            // this.ticker = `${this.symbol}-${interval}`
            if (!this.widget) {
                this.widget = new TvWidget({
                    // symbol: symbol,
                    // interval: interval,
                    symbol: 'AAPL',
                    interval: 1,
                    // fullscreen: true,
                    container_id: 'trade-view',
                    datafeed: this.datafeeds,
                    library_path: '/static/tradingview/charting_library/',
                    disabled_features: chartDisabledFeatures,
                    enabled_features: ['move_logo_to_main_pane'],
                    timezone: 'Asia/Shanghai',
                    locale: 'zh',
                    overrides: {
                        "paneProperties.background": "#191F27",
                        "paneProperties.vertGridProperties.color": "#000",
                        "paneProperties.horzGridProperties.color": "#000"
                    },
                    debug: false,
                    autosize: true,
                    // custom_css_url: '/static/widgetCss/widget.css',
                    loading_screen: {
                        backgroundColor: '#000'
                    }
                })
            }
       }
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}

.gutter-example >>> .ant-row > div {
  background: transparent;
  border: 0;
}
.gutter-box {
  /* background: #00A0E9; */
  /* padding: 5px 0; */
}
</style>

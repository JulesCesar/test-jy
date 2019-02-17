<template>
  <div class="hello" style="min-width: 1280px;">
    <template>
        <a-layout id="components-layout-demo-top" class="layout" style="">
            <a-layout-header style="position:fixed;width: 100%;top: 0;left: 0;z-index: 999;min-width: 1280px;">
                <a-row>
                    <a-col :span="2" style="text-align:left;">
                        <div class="logo">
                            <img src="../assets/Artboard19.png" style="width:100%;">
                        </div>
                    </a-col>
                    <a-col :span="10">
                         <a-menu
                                theme="dark"
                                mode="horizontal"
                                :defaultSelectedKeys="['1']"
                                :style="{ lineHeight: '64px' }"
                            >
                                <a-menu-item key="1" @click="nav(1)">首页</a-menu-item>
                                <a-menu-item key="2" @click="nav(2)">交易中心</a-menu-item>
                                <a-menu-item key="3" @click="nav(3)">场外交易</a-menu-item>
                        </a-menu>

                        <!-- <a-menu v-model="current"  mode="horizontal" @click="changePage">
                                            <a-menu-item key="home" style="margin-right: 60px;">
                                           <span><span style="font-size: 16px;font-weight: 500;">首页</span></span> 
                                            </a-menu-item>
                                            <a-menu-item key="trading" style="margin-right: 60px;">
                                                <span style="font-size: 16px;font-weight: 500;">策略交易</span>
                                            </a-menu-item>
                                            <a-menu-item key="strategyLib" style="margin-right: 60px;">
                                            <span style="font-size: 16px;font-weight: 500;">策略库</span>
                                            </a-menu-item>
                                            <a-menu-item  key="platform" style="">
                                            <span style="font-size: 16px;font-weight: 500;">开放平台</span>
                                            </a-menu-item>
                                        </a-menu> -->
                    </a-col>
                    <a-col :span="12" style="text-align:right;">
                        <a-row>
                            <a-col :span="12"></a-col>
                            <a-col :span="12">
                                <a-row>
                                    <a-col :span="12"  style="color:#fff;">中文简体<a-icon type="caret-down" style="margin-left:8px;"/></a-col>
                                    <a-col :span="4" style="color:#fff;">
                                        <a-icon type="skin" />
                                    </a-col>
                                    <a-col :span="4" style="color:#fff;">登录</a-col>
                                    <a-col :span="4" style="color:#fff;">注册</a-col>
                                </a-row>
                            </a-col>
                        </a-row>
                        <!-- <div style="color:#fff;">中文简体</div> -->
                        
                    </a-col>
                </a-row>
            </a-layout-header>
            <a-layout-content>
                <div @click="qie" :style="{ minHeight: '280px',marginTop: '82px',minWidth:'1200px'}">
                    <router-view />
                </div>
            </a-layout-content>
            <a-layout-footer style="text-align: center">
                <a-row style="background-color:#252e37;text-align:left;padding: 40px 0 40px 0;">
                      <a-col :span="1"></a-col>
                    <a-col :span="11">
                        <div class="logo">
                            <img src="../assets/Artboard19.png" width="153px">
                        </div>
                        <div>
                            <p  style=" font-size: 16px;color: #A5A4A4;padding-left:20px;">安全 稳定 可信 资产交换平台</p>
                        </div>
                        <div>
                            <div style="padding-left:20px;">
                                <a-avatar style="backgroundColor:#2c373f;margin-right:8px;" icon="wechat" />
                                <a-avatar style="backgroundColor:#2c373f;margin-right:8px;" icon="weibo" />
                                <a-avatar style="backgroundColor:#2c373f;margin-right:8px;" icon="qq" />
                            </div>
                        </div>
                    </a-col>
                    <a-col :span="12">
                        <a-row>
                            <a-col :span="6"></a-col>
                            <a-col :span="16">
                                <a-row>
                                    <a-col :span="6" style="color:#fff;text-align: right;">产品</a-col>
                                    <a-col :span="6" style="color:#fff;text-align: right;">关于我们</a-col>
                                    <a-col :span="6" style="color:#fff;text-align: right;">服务协议</a-col>
                                    <a-col :span="6" style="color:#fff;text-align: right;">支持</a-col>
                                </a-row>
                                <a-row style="margin-top:20px;">
                                    <a-col :span="6" style="font-size: 16px;color: rgb(90, 90, 90);text-align: right;line-height: 22px;">BIEX</a-col>
                                    <a-col :span="6" style="font-size: 16px;color: rgb(90, 90, 90);text-align: right;line-height: 22px;">关于BIEX</a-col>
                                    <a-col :span="6" style="font-size: 16px;color: rgb(90, 90, 90);text-align: right;line-height: 22px;">费率说明</a-col>
                                    <a-col :span="6" style="font-size: 16px;color: rgb(90, 90, 90);text-align: right;line-height: 22px;">帮助中心</a-col>
                                </a-row>
                                <a-row>
                                    <a-col :span="6" style="font-size: 16px;color: rgb(90, 90, 90);text-align: right;line-height: 22px;">币书</a-col>
                                    <a-col :span="6" style="font-size: 16px;color: rgb(90, 90, 90);text-align: right;line-height: 22px;">联系我们</a-col>
                                    <a-col :span="6" style="font-size: 16px;color: rgb(90, 90, 90);text-align: right;line-height: 22px;"></a-col>
                                    <a-col :span="6" style="font-size: 16px;color: rgb(90, 90, 90);text-align: right;line-height: 22px;"></a-col>
                                </a-row>
                            </a-col>
                             <a-col :span="2"></a-col>
                        </a-row>
                        
                    </a-col>
                </a-row>
            </a-layout-footer>
        </a-layout>
    </template>
  </div>
</template>

<script>
export default {
    name: 'btcindex',
    data () {
        return {
        msg: 'Welcome to Your Vue.js App'
        }
    },
    
    created() {
       this.$router.replace({name: 'bar1'})
    },
    mounted() { 
    },
    computed: {
    },
    watch:{
    }, 
    methods: {
       qie(){

       },
       nav(val) {
           if (val == 1) {
               this.$router.push({name: 'bar1'})
           } else if (val == 2) {
               this.$router.push({name: 'bar2'})
           } else {
               this.$router.push({name: 'bar3'})
           }
       }
    }
}
</script>
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
</style>

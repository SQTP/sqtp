<template>
<div class="building">
  <v-app id="inspire">
    <v-content>
      <v-container class="fill-height" fluid >
        <v-row align="center" justify="center">
          <v-col cols="12" sm="8" md="4">
            <v-card class="elevation-12">
                <v-toolbar color="primary" dark flat>
                  <v-toolbar-title>我想成为</v-toolbar-title>
                  <v-spacer></v-spacer>
                  <v-tooltip bottom>
                    <template v-slot:activator="{ on }">
                      <v-btn :href="source" icon large target="_blank" v-on="on">
                        <v-icon>mdi-code-tags</v-icon>
                      </v-btn>
                    </template>
                    <span>Source</span>
                  </v-tooltip>
                </v-toolbar>
                <v-card-text>
                  <v-form>
                    <v-text-field v-model="query" label="一个什么样的人" type="text"></v-text-field>
                  </v-form>
                </v-card-text>
                <v-card-actions>
                  <v-spacer></v-spacer>
                  <v-btn color="primary" @click="clickHandler">查询</v-btn>
                </v-card-actions>
            </v-card>
          </v-col>
        </v-row>
      </v-container>
    </v-content>
  </v-app>
  </div>
</template>

<script>
import Bmob from "hydrogen-js-sdk";
  export default {
    props: {
      source: String,
    },
    name: 'productdetailspage',
    data(){
      return {
        note: {
          backgroundImage: "url(" + require("../assets/bg.jpg") + ")",
          backgroundRepeat: "repeat",
          backgroundSize: "25px auto",
          marginTop: "5px",
        },
      }
    },
    methods: {
      clickHandler(){
        console.log('clk');//测试语句
        if(this.query==''){
          console.log('null');
          alert('请输入内容')
        }
        else{
          const query = Bmob.Query('Article');
          query.equalTo("name","==",this.query);
            query.find().then(res => {
              console.log(res);
              if (res && Array.isArray(res) && res.length) {
                this.$store.commit('setSearchData', res);
                this.$router.push({ name: 'SearchResult' })
              }
            }).catch(err => {
                console.log(err)
            });
            console.log('this is query')
            console.log(query)
            console.log('query end')
        }
      }
    }
  }
</script>


<style>
#inspire,
  .building {
    justify-content: center;
    align-items: center;
    background-image: url('../assets/bg.jpg');
    background-size: 100% 100%;
    height: 100%;
    background-size: cover;

  }
  .grey--text {
  position: absolute;
  bottom: 30px;
  color: #fff;
  left: 30%;
}
  
</style>

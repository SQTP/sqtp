<template>

  <v-app id="inspire">
    <div class="building">

      <div id="home">


        <div style="text-align:left;">

          <img src="../assets/zju2.png">

        </div>

        <v-content>
          <v-container class="fill-height"
                       fluid>
            <v-row align="center"
                   justify="center">
              <div id="title">
                <div style="position:relative;
                        width:500px; margin:0 auto;"
                     class="title">
                  <h1 class="blue--text">
                    计算机职业生涯规划
                  </h1>
                </div>
              </div>
            </v-row>
          </v-container>
        </v-content>

        <v-content>
          <v-container class="fill-height"
                       fluid>
            <v-row align="center"
                   justify="center">
              <div id="description">
                <div style="position:relative;
                        width:500px; margin:0 auto;"
                     class="grey--text">
                  本项目旨在帮助初入计算机专业的同学们规划自己将来的职业生涯。
                  输入你感兴趣的计算机职业（硬件、前端、数据库乃至全栈工程师）
                  点击查询，即可得到该职业需要的技能树，也可以了解到就业方向和
                  薪资水平等信息。希望这些信息可以帮助计算机专业的同学们更好地
                  综合规划自己的职业生涯。
                </div>
              </div>
              <v-col cols="12"
                     sm="8"
                     md="4">
                <v-card class="elevation-12">
                  <v-toolbar color="primary"
                             dark
                             flat>
                    <v-toolbar-title>
                      <v-icon>accessibility</v-icon>
                      我想成为
                    </v-toolbar-title>
                    <v-spacer></v-spacer>
                    <v-tooltip bottom>
                      <template v-slot:activator="{ on }">
                        <v-btn :href="source"
                               icon
                               large
                               target="_blank"
                               v-on="on">
                          <v-icon>mdi-code-tags</v-icon>
                        </v-btn>
                      </template>
                      <span>Source</span>
                    </v-tooltip>
                  </v-toolbar>
                  <v-card-text>
                    <v-form>
                      <v-icon>help</v-icon>
                      <v-text-field v-model="query"
                                    label="一个什么样的人"
                                    type="text">

                      </v-text-field>
                    </v-form>
                  </v-card-text>
                  <v-card-actions>
                    <v-spacer></v-spacer>
                    <v-btn class="blue white--text" @click="clickHandler">
                      <v-icon>search</v-icon>
                      <span>查询</span>
                    </v-btn>
                  </v-card-actions>
                </v-card>
              </v-col>
            </v-row>
          </v-container>
        </v-content>
      </div>
      <div style="margin:0 auto;">
        <h2 class="grey--text">Presented by 李智,刘泽铖,徐正浩,李蕴祺,陶嘉辰,俞晓锋,于嘉伟,宋逸群,李俊松</h2>
      </div>
    </div>
  </v-app>
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
          backgroundImage: "url(" + require("../assets/login-background.jpg") + ")",
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
        }
        else{
          const query = Bmob.Query('Article');
          query.equalTo("name","==",this.query);
            query.find().then(res => {
                this.$store.commit("setName",res[0].text);
            }).catch(err => {
                console.log(err)
            });
            console.log(query)
          this.$router.push("/query/"+this.query);
        }
      }
    }
  }
</script>


<style>
  .building {

    justify-content: center;
    align-items: center;
    background-image: url('../assets/login-background.jpg');
    background-size: 100% 100%;
    height: 100%;
    background-size: cover;
  }
  
</style>

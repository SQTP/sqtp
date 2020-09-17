<template>

  <v-app id="inspire">
    <v-content>
      <v-container
        class="fill-height"
        fluid
      >
        <v-row
          align="center"
          justify="center"
        >
          <v-col
            cols="12"
            sm="8"
            md="4"
          >
            <v-card class="elevation-12">
              <v-toolbar
                color="primary"
                dark
                flat
              >
                <v-toolbar-title>我想成为</v-toolbar-title>
                <v-spacer></v-spacer>
                <v-tooltip bottom>
                  <template v-slot:activator="{ on }">
                    <v-btn
                      :href="source"
                      icon
                      large
                      target="_blank"
                      v-on="on"
                    >
                      <v-icon>mdi-code-tags</v-icon>
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

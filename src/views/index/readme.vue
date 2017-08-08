<template>
  <div class="app-container">
    <code>
    <div id="header" style="margin-top:-50px">
        
        <div id="person">
        <a href="#/example/myBooklist">
          <el-button type="text" icon="star-on">我的书单</el-button>
          </a>
          <el-button type="text" icon="message">系统公告</el-button>
        </div>
        <div id="search">
          <el-input placeholder="请输入书名、作者、类型" icon="search" v-model="input2" :on-icon-click="handleIconClick">
            <el-select v-model="select" slot="prepend" placeholder="全部分类">
              <el-option label="经典文学" value="1"></el-option>
              <el-option label="儿童读物" value="2"></el-option>
              <el-option label="经管" value="3"></el-option>
              <el-option label="旅游/休闲" value="4"></el-option>
              <el-option label="幽默漫画、画集" value="5"></el-option>
              <el-option label="科技" value="6"></el-option>
            </el-select>
          </el-input>
        </div>
        <br/>
    </div>

        <h1 style="font-family:'华文新魏';font-size:60px" align="center">图书信息管理系统</h1>
    
    <div id="show" style="width:60%; height:400px;">
      <el-carousel :interval="5000" arrow="always" style="height:380px;">
        <el-carousel-item v-for="item in 4" :key="item"></el-carousel-item>
      </el-carousel>
    </div>
     
      <ul id="kinds">
        <!-- 推荐书目 -->
        <li id="good">
          <h4>推荐书目</h4>
          <el-col :span="4" >
            <img src="http://img3x8.ddimg.cn/92/3/23464478-1_l_5.jpg">
            <p>《解忧杂货铺》</p>
            <p>(日)东野圭吾</p>
            <p>南海出版社</p>
            <!-- <i class="el-icon-star-off"></i> -->
            <el-button type="primary" icon="star-off"></el-button>
            <el-button type="text">加入书单</el-button>
          </el-col>

          <el-col :span="4" >
            <img src="http://img3x5.ddimg.cn/64/1/25087555-1_l_3.jpg">
            <p>《重返19次人生》</p>
            <p>（英）克莱儿·斯沃特曼</p>
            <p>百花洲文艺出版社</p>
            <el-button type="primary" icon="star-off"></el-button>
            <el-button type="text">加入书单</el-button>
          </el-col>

          <el-col :span="4" >
            <img src="http://img3x4.ddimg.cn/7/17/23808814-1_l_8.jpg">
            <p>《鬼吹灯》(全集)</p>
            <p>天下霸唱</p>
            <p>青岛出版社</p>
            <el-button type="primary" icon="star-off"></el-button>
            <el-button type="text">加入书单</el-button>
          </el-col>

          <el-col :span="4" >
            <img src="http://img3x0.ddimg.cn/28/9/23822200-1_l_11.jpg">
            <p>《天才在左，疯子在右》</p>
            <p>高铭</p>
            <p>浙江文艺出版社</p>
            <el-button type="primary" icon="star-off"></el-button>
            <el-button type="text">加入书单</el-button>
          </el-col>

          <el-col :span="4" >
            <img src="http://img3x8.ddimg.cn/35/10/23274638-1_l_19.jpg">
            <p>《追风筝的人》</p>
            <p>[美]卡勒德·胡赛尼</p>
            <p>上海人民出版社</p>
            <el-button type="primary" icon="star-off"></el-button>
            <el-button type="text">加入书单</el-button>
          </el-col>

          <el-col :span="4" >
            <img src="http://img3x0.ddimg.cn/49/26/22864990-1_l_2.jpg">
            <p>《活着》</p>
            <p>余华</p>
            <p>作家出版社</p>
            <el-button type="primary" icon="star-off"></el-button>
            <el-button type="text">加入书单</el-button>
          </el-col>
        </li>

        <hr  style="border:1px solid #eef1f6;"/><br/>

        <!-- 畅销排行榜 -->
        <li id="sell">
          <h4 style="margin:0 0">畅销排行榜</h4>
          <el-row :gutter="20">
            <el-col :span="8" >
              <h4>Top1</h4>
              <img src="http://img3x3.ddimg.cn/81/7/23055003-1_l_16.jpg">
              <p>《小王子》</p>
              <p>(法) 圣-埃克苏佩里 著</p>
              <p>梅思繁 译</p>
              <p>浙江文艺出版社</p>
              <p>"如果你爱上了某个星球的一朵花。那么，只要在夜晚仰望星空，就会觉得漫天的繁星就像一朵朵盛开的花。"</p>
              <p>"所有的大人都曾经是小孩，虽然，只有少数的人记得"</p>
              <el-button type="primary">收藏</el-button>
              <el-button type="primary">加入书单</el-button>
            </el-col>

            <el-col :span="8" >
              <h4>Top2</h4>
              <img src="http://img3x5.ddimg.cn/60/0/23407125-1_l_1.jpg">
              <p>《目送》</p>
              <p>（台）龙应台</p>
              <p>浙江文艺出版社</p>
              <p>"我慢慢地、慢慢地了解到，所谓父女母子一场，只不过意味着，你和他的缘分就是今生今世不断地在目送他的背影渐行渐远。你站在小路的这一端，看着他逐渐消失在小路转弯的地方，而且，他用背影默默告诉你：不必追。"</p>
              <el-button type="primary">收藏</el-button>
              <el-button type="primary">加入书单</el-button>
            </el-col>

            <el-col :span="8" >
              <h4>Top3</h4>
              <img src="http://img3x8.ddimg.cn/94/5/25098178-1_l_3.jpg">
              <p>《知更鸟女孩3：神秘人》</p>
              <p>（美）查克·温迪格 </p>
              <p>百花洲文艺出版社</p>
              <p>"十字架上，横的那一条线代表人类，它指的是当下的世界，一个充斥着物质、肉体和污垢的世界。泥巴，鲜血，石头，骨头。竖的那一条是代表上帝的神圣线，处于支配地位。它垂直于人类世界，是来世与未知世界的轴线。"</p>
              <el-button type="primary">收藏</el-button>
              <el-button type="primary">加入书单</el-button>
            </el-col>
          </el-row>
        </li>

        <hr  style="border:1px solid #eef1f6;"/>

        <!-- 图书分类 -->
        <li>
          <h4>图书分类</h4>
          
          <el-tabs v-model="activeName2" type="card" @tab-click="handleClick">

            <el-tab-pane label="青春文学">
              <el-col :span="4" >
                <img src="http://img3x5.ddimg.cn/38/17/23429675-1_l_4.jpg">
                  <p>《你是最好的自己》</p>
              </el-col>
              <el-col :span="4" >
                <img src="http://img3x5.ddimg.cn/38/17/23429675-1_l_4.jpg">
                  <p>《你是最好的自己》</p>
              </el-col>
              <el-col :span="4" >
                <img src="http://img3x5.ddimg.cn/38/17/23429675-1_l_4.jpg">
                  <p>《你是最好的自己》</p>
              </el-col>
              <el-col :span="4" >
                <img src="http://img3x5.ddimg.cn/38/17/23429675-1_l_4.jpg">
                  <p>《你是最好的自己》</p>
              </el-col>
              <el-col :span="4" >
                <img src="http://img3x5.ddimg.cn/38/17/23429675-1_l_4.jpg">
                  <p>《你是最好的自己》</p>
              </el-col>
               <el-col :span="4" >
                <img src="http://img3x5.ddimg.cn/38/17/23429675-1_l_4.jpg">
                  <p>《你是最好的自己》</p>
              </el-col>
            </el-tab-pane>

            <el-tab-pane label="经典名著" name="second">
              <el-col :span="4" >
                <img src="http://img3x7.ddimg.cn/90/24/21090357-1_l_40.jpg">
                  <p>《百年孤独》</p>
              </el-col>
              <el-col :span="4" >
                <img src="http://img3x7.ddimg.cn/90/24/21090357-1_l_40.jpg">
                  <p>《百年孤独》</p>
              </el-col>
              <el-col :span="4" >
                <img src="http://img3x7.ddimg.cn/90/24/21090357-1_l_40.jpg">
                  <p>《百年孤独》</p>
              </el-col>
              <el-col :span="4" >
                <img src="http://img3x7.ddimg.cn/90/24/21090357-1_l_40.jpg">
                  <p>《百年孤独》</p>
              </el-col>
              <el-col :span="4" >
                <img src="http://img3x7.ddimg.cn/90/24/21090357-1_l_40.jpg">
                  <p>《百年孤独》</p>
              </el-col>
              <el-col :span="4" >
                <img src="http://img3x7.ddimg.cn/90/24/21090357-1_l_40.jpg">
                  <p>《百年孤独》</p>
              </el-col>
            </el-tab-pane>

            <el-tab-pane label="儿童读物" name="third">
              <el-col :span="4" >
                <img src="http://img3x1.ddimg.cn/35/3/8964881-1_l_3.jpg">
                  <p>《安徒生童话》</p>
              </el-col>
              <el-col :span="4" >
                <img src="http://img3x1.ddimg.cn/35/3/8964881-1_l_3.jpg">
                  <p>《安徒生童话》</p>
              </el-col>
              <el-col :span="4" >
                <img src="http://img3x1.ddimg.cn/35/3/8964881-1_l_3.jpg">
                  <p>《安徒生童话》</p>
              </el-col>
              <el-col :span="4" >
                <img src="http://img3x1.ddimg.cn/35/3/8964881-1_l_3.jpg">
                  <p>《安徒生童话》</p>
              </el-col>
              <el-col :span="4" >
                <img src="http://img3x1.ddimg.cn/35/3/8964881-1_l_3.jpg">
                  <p>《安徒生童话》</p>
              </el-col>
              <el-col :span="4" >
                <img src="http://img3x1.ddimg.cn/35/3/8964881-1_l_3.jpg">
                  <p>《安徒生童话》</p>
              </el-col>
            </el-tab-pane>

            <el-tab-pane label="人文社科" name="fourth">
              <el-col :span="4" >
                <img src="http://img3x4.ddimg.cn/52/26/22915384-1_l_1.jpg">
                  <p>《乡土中国》</p>
              </el-col>
              <el-col :span="4" >
                <img src="http://img3x4.ddimg.cn/52/26/22915384-1_l_1.jpg">
                  <p>《乡土中国》</p>
              </el-col>
              <el-col :span="4" >
                <img src="http://img3x4.ddimg.cn/52/26/22915384-1_l_1.jpg">
                  <p>《乡土中国》</p>
              </el-col>
              <el-col :span="4" >
                <img src="http://img3x4.ddimg.cn/52/26/22915384-1_l_1.jpg">
                  <p>《乡土中国》</p>
              </el-col>
              <el-col :span="4" >
                <img src="http://img3x4.ddimg.cn/52/26/22915384-1_l_1.jpg">
                  <p>《乡土中国》</p>
              </el-col>
              <el-col :span="4" >
                <img src="http://img3x4.ddimg.cn/52/26/22915384-1_l_1.jpg">
                  <p>《乡土中国》</p>
              </el-col>
            </el-tab-pane>

            <el-tab-pane label="教育科技" name="fifth">
              <el-col :span="4" >
                <img src="http://img3x0.ddimg.cn/66/31/23224080-1_l_2.jpg">
                  <p>《经济学原理（第六版）》</p>
              </el-col>
              <el-col :span="4" >
                <img src="http://img3x0.ddimg.cn/66/31/23224080-1_l_2.jpg">
                  <p>《经济学原理（第六版）》</p>
              </el-col>
              <el-col :span="4" >
                <img src="http://img3x0.ddimg.cn/66/31/23224080-1_l_2.jpg">
                  <p>《经济学原理（第六版）》</p>
              </el-col>
              <el-col :span="4" >
                <img src="http://img3x0.ddimg.cn/66/31/23224080-1_l_2.jpg">
                  <p>《经济学原理（第六版）》</p>
              </el-col>
              <el-col :span="4" >
                <img src="http://img3x0.ddimg.cn/66/31/23224080-1_l_2.jpg">
                  <p>《经济学原理（第六版）》</p>
              </el-col>
              <el-col :span="4" >
                <img src="http://img3x0.ddimg.cn/66/31/23224080-1_l_2.jpg">
                  <p>《经济学原理（第六版）》</p>
              </el-col>
            </el-tab-pane>

            <el-tab-pane label="保健/养生" name="sixth">
              <el-col :span="4" >
                <img src="http://img3x2.ddimg.cn/5/25/20771492-1_l_2.jpg">
                  <p>《二十四节气养生法》</p>
              </el-col>
              <el-col :span="4" >
                <img src="http://img3x2.ddimg.cn/5/25/20771492-1_l_2.jpg">
                  <p>《二十四节气养生法》</p>
              </el-col>
              <el-col :span="4" >
                <img src="http://img3x2.ddimg.cn/5/25/20771492-1_l_2.jpg">
                  <p>《二十四节气养生法》</p>
              </el-col>
              <el-col :span="4" >
                <img src="http://img3x2.ddimg.cn/5/25/20771492-1_l_2.jpg">
                  <p>《二十四节气养生法》</p>
              </el-col>
              <el-col :span="4" >
                <img src="http://img3x2.ddimg.cn/5/25/20771492-1_l_2.jpg">
                  <p>《二十四节气养生法》</p>
              </el-col>
              <el-col :span="4" >
                <img src="http://img3x2.ddimg.cn/5/25/20771492-1_l_2.jpg">
                  <p>《二十四节气养生法》</p>
              </el-col>
            </el-tab-pane>
          </el-tabs>
        </li>
        <li>
          <h4>好文推荐</h4>
          <ul id="article">
            <li>
              <img src="https://img2.cache.netease.com/news/2017/8/2/201708021454369af58.jpg?imageView&quality=90&thumbnail=285y180">
              <p><router-link to="#">长得好看不如活得热闹</router-link></p>
              <p>来源：靠垫儿</p>
              <p>你可以选择烟火气，也可以选择热气腾腾的人生。</p>
              <p>
              <i class="el-icon-star-off"></i>596
              <i class="el-icon-share"></i>428
              </p>
            </li>
            <li>
              <img src="https://img6.cache.netease.com/news/2017/8/2/20170802142817426b2.jpg?imageView&quality=90&thumbnail=285y180">
              <p><router-link to="#">录取通知书</router-link></p>
              <p>来源：靠垫儿</p>
              <p>从此父母只剩背影，故乡只有夏冬。</p>
              <p>
              <i class="el-icon-star-off"></i>493
              <i class="el-icon-share"></i>634
              </p>
            </li>
            <li>
              <router-link to="#">我只是想当个有用的人</router-link>
              <p>或许我依旧一事无成，但我已经拥有很多。</p>
              <router-link to="#">在火热的重庆，吃澈凉的冰粉</router-link>
              <p>思君不见下渝州。</p>
              <router-link to="#">这家书店5年搬家300次，还在坚持</router-link>
              <p>  “我很快乐，想一直继续下去。”</p>
              <router-link to="#">给别人一个好评就是一种善良</router-link>
              <p> 前路漫漫，愿我们都能择善而行。</p>
            </li>
          </ul>
        </li>
      </ul>   
    </code>

    <div id="about" style="margin:80px 0;">
    <h3 align="center">关于我们</h3><br/>
      <el-row :gutter="20">
          <el-col :span="4"  :offset="3"><router-link to="/movie/movieSearch">图书搜索 <i class="el-icon-search"></i></router-link></el-col>
          <el-col :span="4" ><router-link to="/systemSet/personalCenter">个人中心 <i class="el-icon-menu"></i></router-link></el-col>
          <el-col :span="4" ><router-link to="/systemSet/permissionsManage">管理权限 <i class="el-icon-setting"></i></router-link></el-col>
          <el-col :span="4" ><router-link to="/example/myBooklist">我的书单 <i class="el-icon-star-on"></i></router-link></el-col>
          <el-col :span="4" ><router-link to="/example/table2">历史记录 <i class="el-icon-time"></i></router-link></el-col>
        </el-row>
    </div>
  </div>
</template>

<script>
//  import { mapGetters } from 'vuex';
// import {global} from 'src/global/global';
// import {api} from 'src/global/api';


export default {
  data() {
    return {
        
    }
  },
  computed: {
        // ...mapGetters({
        //     personalInfo_init:'userInfo'
        // })
    },
  mounted() {
    
   },
  methods: {
    

  }
};
</script>

<style rel="stylesheet/scss" lang="scss">
    /*轮播*/
    #show{
      margin: 20px 20%; 
    }

   .el-carousel__item{
    width: 700px;
    height: 380px; 
   }
    
    .el-carousel__item:nth-child(3) {
      background-image: url(https://img2.cache.netease.com/news/2017/8/3/20170803140232245da.jpg);
    }

    .el-carousel__item:nth-child(4) {
      background-image: url(https://img3.cache.netease.com/news/2017/7/28/20170728100330deb38.jpg);
    }

    .el-carousel__item:nth-child(5) {
      background-image: url(https://img3.cache.netease.com/news/2017/8/2/2017080214505468980.jpg);
    }
    
    .el-carousel__item:nth-child(6) {
      background-image: url(https://img1.cache.netease.com/news/2017/7/21/201707211136511235a.jpg);
    }

    /*搜索*/
    #search{
      width: 26%;
      float: right;
    }

    .el-select .el-input {
      width: 100px;
    }

    #person{
      width:16%;
      float:right;
      margin-left: 55px; 
    }

    /*其他*/
    #kinds{
      padding-top: 20px;
      list-style: none;
      line-height: 30px;
    }

    #sell img{
      float: left;
    }

    #kinds p{
      font-size: 14px;
    }

    #kinds li ul{
      list-style: none;
    }

    #good p{
      line-height: 10px;
    }

    #article{
      height: 350px;
    }

    #article li{
      width: 30%;
      margin: 10px;
      float: left;
    }
</style>

<script>
export default {
  data() {
    return {
      currentDate: new Date()
    };
  }

</style>

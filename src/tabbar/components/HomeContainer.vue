<template>
  <div>
    <mt-swipe :auto="4000">
        <mt-swipe-item v-for="item in lunbotuList" :key="item.img">
            <img :src="item.img" alt="">
        </mt-swipe-item>
    </mt-swipe>


    <!-- <router-view></router-view> -->



    <ul class="mui-table-view mui-grid-view mui-grid-9">
		<li class="mui-table-view-cell mui-media mui-col-xs-4 mui-col-sm-3">
            <router-link to="/home/newsList">
		    <img src="../../images/menu1.png" alt="">
		    <div class="mui-media-body">新闻资讯</div>
            </router-link>
        </li>
		<li class="mui-table-view-cell mui-media mui-col-xs-4 mui-col-sm-3"><a href="#">
		    <img src="../../images/menu2.png" alt="">
		    <div class="mui-media-body">图片分享</div></a></li>
		<li class="mui-table-view-cell mui-media mui-col-xs-4 mui-col-sm-3"><a href="#">
		    <img src="../../images/menu3.png" alt="">
		    <div class="mui-media-body">商品购买</div></a></li>
		<li class="mui-table-view-cell mui-media mui-col-xs-4 mui-col-sm-3"><a href="#">
		    <img src="../../images/menu4.png" alt="">
		    <div class="mui-media-body">留言反馈</div></a></li>
		<li class="mui-table-view-cell mui-media mui-col-xs-4 mui-col-sm-3"><a href="#">
		    <img src="../../images/menu5.png" alt="">
		    <div class="mui-media-body">视频专区</div></a></li>
		<li class="mui-table-view-cell mui-media mui-col-xs-4 mui-col-sm-3"><a href="#">
		    <img src="../../images/menu6.png" alt="">
		    <div class="mui-media-body">联系我们</div></a></li>
	</ul> 
  </div>
</template>





<script>
    import {Toast} from 'mint-ui'
    export default({
        data() {
            return {
                lunbotuList:[]
            }
        },
        created() {
            this.getLunbotu()
        },
        methods: {
            getLunbotu() {
                this.$http.get('api/getlunbo').then(result => {
                    console.log(result)
                    if(result.body.status === 0){
                        this.lunbotuList = result.body.message;
                        Toast('获取数据成功。。。')
                    }else{
                        Toast('获取数据失败。。。')
                    }
                })
            }
        }
    })
</script>



<style lang="scss" scoped>
   .mint-swipe {
       height: 200px;
       .mint-swipe-item {
           &:nth-child(1){
           background-color: red;
       }
       &:nth-child(2){
           background-color: blue;
       }
       &:nth-child(3){
           background-color: yellow;
       }
       img {
           width:100%;
           height:100%;
       }
       }
   }

   .mui-grid-view.mui-grid-9 {
       background-color: #fff;
       border:none;
       li {
           border:none;

           img {
               width:50%;
               height:50%;
           }
       }
   }
</style>


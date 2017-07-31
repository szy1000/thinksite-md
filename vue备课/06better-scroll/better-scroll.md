##better-scroll

###1.0 安装

	"better-scroll": "^0.1.7",

npm install

###1.1使用

	import BScroll from 'better-scroll';

通过ref获取DOM节点

	<div class="menu-wrapper" ref="menuWrapper">
	<div class="goods-wrapper" ref="goodsWrapper">

获取节点：
	
	let scroll = new BScroll(document.getElementById('wrapper'), {
	  startX: 0,
	  startY: 0
	})
	

	this.$refs.menuWrapper

使用节点

	methods: {
      _initScroll() {
        this.menuScroll = new BScroll(this.$refs.menuWrapper, {});
		this.foodScroll = new BScroll(this.$refs.foodWrapper, {});
      }
    }

初始化调用

	created() {
		this._initScroll();
	}

数据渲染是异步的

	this.$nextTick(() => {
      this._initScroll();
    });

放到https里面

	this.$http.get("/api/goods").then((response) => {
    this.goods = response.body.data;
    this.$nextTick(() => {
      this._initScroll();
    })
	 }),

响应式数据的高度：


- 准备数据获取height值
- nextTick下面调用

获取foodMenu的高度

	_calculateHeight() {
        let foodList = this.$refs.foodWrapper.getElementsByClassName('food-list-hook');
        let height = 0;
        this.listHeight.push(height);
        for (let i = 0; i < foodList.length; i++) {
          let item = foodList[i];
          height += item.clientHeight;
          this.listHeight.push(height);
        }

	console.log(this.listHeight); //可以打印出来看看
      }

记得在nextTick里面调用

官网的event:

	let scroll = new BScroll(document.getElementById('wrapper'),{
	   probeType: 3
	})
	
	scroll.on('scroll', (pos) => {
	  console.log(pos.x + '~' + pos.y)
	  ...
	})


监听滚动的高度
	 probeType: 3,
	

	this.foodScroll.on('scroll', (pos) => {
          this.scrollY = Math.abs(Math.round(pos.y));
          console.log(this.currentIndex);
        });


由高度值做映射

	currentIndex() {
        for (let i = 0; i < this.listHeight.length; i++) {
          let height1 = this.listHeight[i];
          let height2 = this.listHeight[i + 1];
          if (!height2 || (this.scrollY >= height1 && this.scrollY < height2)) {
            return i;
          }
        }
        return 0;
      }

对class类名进行检测

	:class="{'current': currentIndex === index}"



左侧点击按钮：

	selectMenu(index){
		console.log(index)
	}

	@click="selectMenu(index)";

事件的派发：
	
	@click="selectMenu(index,$event)"
	
	console.log(event);
	selectMenu(index,event){
        if(!event._constructed){
          return;
        }
	...
	｝




	<template>  
  <div class="goods">
  	<div class="menu-wrapper" ref="menuWrapper">
    	<ul v-if="goods">
        <li v-for="(item,index) in goods" class="menu-item border-1px" :class="{'current': currentIndex === index}">
            <span class="text">
            <span class="icon" v-if="item.type>0" :class="classMap[item.type]">
            </span>
              {{item.name}}
            </span>
        </li>
    	</ul>
  	</div>
  	<div class="foods-wrapper" ref="foodWrapper">
  		<ul>
        <li v-for="item in goods" class="food-list food-list-hook">
          <h2 class="title">{{item.name}}</h2>
          <ul>
            <li v-for="food in item.foods" class="food-item">
              <div class="icon">
                <img :src="food.icon" width="57" height="57" alt="">
              </div>
              <div class="content">
                <h3 class="name">{{food.name}}</h3>
                <p class="desc">{{food.description}}</p>
                <div class="extra">
                  <span>月售:{{food.sellCount}}</span>
                  <span>好评率:{{food.rating}}%</span>
                </div>
                <div class="price">
                  <span class="nowPrice">￥{{food.price}}</span>
                  <span v-show="food.oldPrice"  class="oldPrice">{{food.oldPrice}}</span>
                </div>
              </div>
            </li>
          </ul>
        </li>
      </ul>
  	</div>
  </div>
</template>

<script>
  import BScroll from 'better-scroll';
  export default {
	  data() {
	  	return {
		  	goods: [],
      listHeight: [],
      scrollY: 0
	  	};
	  },
	  created() {
	    this.seller = this.$http.get('./api/goods').then((response) => {
        this.goods = response.body.data;
        this.$nextTick(() => {
          this._initScroll();
          this._calculateHeight();
        });
      }, (response) => {
        alert('error');
      });
      this.classMap = ['decrease', 'discount', 'guarantee', 'invoice', 'special'];
	  },
    computed: {
      currentIndex() {
        for (let i = 0; i < this.listHeight.length; i++) {
          let height1 = this.listHeight[i];
          let height2 = this.listHeight[i + 1];
          if (!height2 || (this.scrollY >= height1 && this.scrollY < height2)) {
            return i;
          }
        }
        return 0;
      }
    },
    methods: {
      _initScroll() {
        this.menuScroll = new BScroll(this.$refs.menuWrapper, {
          click: true
        });
        this.foodScroll = new BScroll(this.$refs.foodWrapper, {
          probeType: 3,
          click: true
        });
        this.foodScroll.on('scroll', (pos) => {
          this.scrollY = Math.abs(Math.round(pos.y));
          console.log(this.currentIndex);
        });
      },
      _calculateHeight() {
        let foodList = this.$refs.foodWrapper.getElementsByClassName('food-list-hook');
        let height = 0;
        this.listHeight.push(height);
        for (let i = 0; i < foodList.length; i++) {
          let item = foodList[i];
          height += item.clientHeight;
          this.listHeight.push(height);
        }
      }
    }
  };
</script>

<style lang="scss" scoped>
  @import '../../common/scss/mixin.scss';

  .goods{
		display:flex;
		position: absolute;
		top:174px;
		bottom: 46px;
		width: 100%;
		overflow: hidden;
		.menu-wrapper{
			flex: 0 0 80px;
			width: 80px;
      background-color: #f3f5f7;
      .menu-item{
        display: table;
        height: 54px;
        width: 56px;
        line-height: 14px;
        padding: 0 12px;
        @include border1px(rgba(7,17,27,.1));
        &.current{
          z-index: 10;
          margin-top: -1px;
          background: #fff;
          font-weight: 700;
          .text{
            @include border-none(rgba(0,0,0,0));
          }
        }
        .icon{
          display: inline-block;
          margin-right:2px;
          width:16px;
          height:16px;
          vertical-align:top;
          background-size:16px 16px;
          background-repeat: no-repeat;
          &.decrease{
            @include bg-images('decrease_3');
          }
          &.discount{
            @include bg-images('discount_3');
          }
          &.guarantee{
            @include bg-images('guarantee_3');
          }
          &.invoice{
            @include bg-images('invoice_3');
          }
          &.special{
            @include bg-images('special_3');
          }
        }
        .text{
          display: table-cell;
          width: 56px;
          vertical-align: middle;
          font-size: 12px;
        }
      }
		}
    .foods-wrapper{
      flex:1;
      .title{
        padding-left:14px;
        height:26px;
        line-height:26px;
        border-left:2px solid #d9dde1;
        font-size:12px;
        color:rgb(147,153,159);
        background-color: #f3f5f7;
      }
      .food-item{
        display:flex;
        margin:18px;
        padding-bottom:18px;
        @include border1px(rgba(7,17,27,.1));
        &:last-child{
          @include border-none(rgba(7,17,27,.1))
          padding-bottom:0;
        }
        .icon{
          flex: 0 0 57px;
          margin-right: 10px;
        }
        .content{
          flex: 1;
          .name{
            margin: 2px 0 8px 0;
            height:14px;
            font-size: 14px;
            line-height:14px;
            color:rgb(7,17,27);
          }
          .desc,.extra{
            line-height: 1.2;
            font-size: 10px;
            color:rgb(147, 153, 159);
          }
          .desc{
            margin-bottom: 8px;
          }
          .extra{
            line-height:10px;
            .count{
              margin-right:12px;
            }
          }
          .price{
            font-weight: 700;
            line-height: 24px;
            .nowPrice{
              margin-right: 8px;
              font-size: 14px;
              color:rgb(240,20,20);
            }
            .oldPrice{
              font-size: 10px;
              color:rgb(147, 153, 159);
              text-decoration: line-through;
            }
          }
        }
        .cartcontrol-wrapper{
          position: absolute;
          right:0;
          bottom:12px;
        }
      }
    }
  }
</style>
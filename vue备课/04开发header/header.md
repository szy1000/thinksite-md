##header

函数前面必须有空格，不喜欢的可以删除

	"space-before-function-paren": ["error", "always"]

我们需要去使用vue-resource

	"dependencies": {
	    "vue": "^2.3.3",
	    "vue-router": "^2.6.0",
	    "vue-resource": "^1.3.0"
	  },

添加vue-resource, 安装；


main.jss里面注册使用

	import VueResource from 'vue-resource';
	Vue.use(VueResource);

回到App,获取seller

	created() {
      this.$http.get('./api/seller').then((response) => {
        this.seller = response.body;
      }, (response) => {
        alert('error');
      });
    },

利用：传参

	:seller = "seller"

header组件：接受

	props: {
		seller: {
			type:Object
		}
	}


不允许用tab tab和空格混用  

	"no-tabs": "off",
    "no-mixed-spaces-and-tabs": 2,

 定义mixin.scss

1px 

	@mixin border-1px($color){
		position: relative;
		&:after{
			display:block;
			position: absolute;
			left:0;
			bottom:0;
			content: '';
			width:100%;
			height:1px;
			background:$color;
			}
		}
	
	@mixin border-none($color){
		position: relative;
		&:after{
			display:none;
			position: absolute;
			left:0;
			bottom:0;
			content: '';
			width:100%;
			height:1px;
			background:$color;
		}
	}

	@media (-webkit-min-device-pixel-ratio: 2),(min-device-pixel-ratio: 2){
		.border-1px{
			&:after{
				transform: scaleY(.7);
			}
		}
	}

	@media (-webkit-min-device-pixel-ratio: 3),(min-device-pixel-ratio: 3){
		.border-1px{
			&:after{
				transform: scaleY(.5);
			}
		}
	}

v-if = "seller.supports"

	:class="classMap[supports[index].type]

javascript

	created() {
    	this.classMap = ['decrease', 'discount', 'guarantee', 'invoice', 'special'];
    }	

背景样式：

	.icon{
		display:inline-block;
		margin-right:4px;
		width:12px;
		height:12px;
		background-size: 12px 12px;
		background-repeat: no-repeat;
		vertical-align: top;
		&.decrease{
			@include bg-images('decrease_1');
		}
		&.discount{
			@include bg-images('discount_1');
		}
		&.guarantee{
			@include bg-images('guarantee_1');
		}
		&.invoice{
			@include bg-images('invoice_1');
		}
		&.special{
			@include bg-images('special_1');
		}
	}
	.text{
		line-height:12px;
		font-size: 10px;
		vertical-align:top;
	}

背景显示 2x图 3x图：

	@mixin bg-images($url){
		background-image: url($url+ "@2x.png");
		@media (-webkit-min-device-pixel-ratio: 2),(min-device-pixel-ratio: 2){
			background-image: url($url+ "@3x.png");
		}
	}

背景图片：

	filter:blur(10px);

超出隐藏

	white-space:nowrap;
	overflow:hidden;
	text-overflow:ellipsis;
	box-sizing: border-box;

固定遮罩：

	<transition name="fade"></fade>

	.fade-enter,.fade-leave-active{
		opacity: 0;
	}
	.fade-enter-active, .fade-leave-active{
		transition: all .5s;
	}


显示影藏

	data() {
	  	return {
			  detailShow: false
	  	};
	  },
	  methods: {
		  showDetail() {
		    this.detailShow = true;
  		},
	    closeDtail() {
      	this.detailShow = false;
    	}
	  },
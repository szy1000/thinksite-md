##shopCart

css




js逻辑：

app.vue页面需要传递 seller对象

	<router-view :seller="seller"></router-view>


goods.vue


	<shopcart :delivery="seller.deliveryPrice" :minPrice="seller.minPrice"></shopcart>


	props:{
      seller:{
        return: Object
      }
    },

shopcart:

	props:{
		delivery: {
			type: Number,
			default: 0
		},
		minPrice: {
			type: Number,
			default: 0
		}
	}

自己预定义一个组件数据：
	selectFoods:{
		type: Array,
		default() {
			return [
				{	
					price: 10,
					count: 2
				}
			]
		}
	}

利用计算熟悉

	computed:{
		totalPrice(){
			let total = 0;
			this.selectFoods.forEach((food) => {
				total += food.price * food.count
			});
			return total
		},
		totalCount(){
			let count = 0;
			this.selectFoods.forEach((food) => {
				count += food.count;
			})
			return count;
		},
		pay(){
			if(this.totalPrice === 0){
				return `还差￥${this.minPrice}起送`
			}else if(this.totalPrice < this.minPrice){
				let diff = this.minPrice - this.totalPrice
				return `还差￥${diff}起送`
			}
			else{
				return "去结算"
			}
		},
		payClass(){
			if(this.totalPrice >= this.minPrice){
				return 'enough'
			}else{
				return 'not-enough'
			}
		}
	}

## cartcontrol

引入组件：

	<div class="cartcontrol-wrapper">
      <cartcontrol :food="food"></cartcontrol>
    </div>

	.cartcontrol-wrapper{
      position: absolute;
      right:0;
      bottom:12px;
    }

传入food值

	

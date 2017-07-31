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


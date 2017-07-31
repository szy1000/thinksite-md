##商品页面

html：

	<div class="goods">
	    <div class="menu-wrapper"></div>
	    <div class="goods-wrapper"></div>
 	 </div>


固定定位   flex 布局 

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
		}
  }	


计算top bottom 的值




flex 左边固定右边自适应


<template>
  <div class="goods">
  	<div class="menu-wrapper">
    	<ul v-if="goods">
    		<li v-for="item in goods">{{item.name}}</li>
    	</ul>
  	</div>
  	<div class="foods-wrapper">
  		
  	</div>
  </div>
</template>

<script>
  export default {
	  data() {
	  	return {
		  	goods: []
	  	};
	  },
	  created() {
	    this.seller = this.$http.get('./api/goods').then((response) => {
        this.goods = response.body.data;
        console.log(this.goods);
      }, (response) => {
        alert('error');
      });
	  }
  };
</script>

<style lang="scss" scoped>
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
</style>
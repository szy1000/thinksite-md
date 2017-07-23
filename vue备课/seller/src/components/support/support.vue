<template>
  <ul class="supports">
		<li class="support-item" v-for="(item ,index) in supports">
			<span class="icon" :class="classMap[supports[index].type]"></span>
			<span class="text">{{ supports[index].description }}</span>
		</li>
	</ul>
</template>

<script>
  export default {
    props: {
    	supports: {
    		type: Array
    	}
    },
    created() {
    	this.classMap = ['decrease', 'discount', 'guarantee', 'invoice', 'special'];
    }
  };
</script>

<style lang="scss" scoped>
	@import '../../common/scss/mixin.scss';

  .supports{
  	.support-item{
  		margin-bottom: 12px;
  		&:last-child{
  			margin-bottom: 0;
  		}
  	}
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
	}
</style>
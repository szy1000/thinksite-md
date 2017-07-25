##better-scroll

###1.0 安装

	"better-scroll": "^0.1.7",

npm install

###1.1使用

	import BScroll from 'better-scroll';

通过ref获取DOM节点

	<div class="menu-wrapper" ref="menuWrapper">

使用节点

	methods: {
      _initScroll() {
        this.menuScroll = new BScroll(this.$refs.menuWrapper, {
          click: true
        });
		this.foodScroll = new BScroll(this.$refs.foodWrapper, {
	      probeType: 3,
	      click: true
		});
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
      }

监听滚动的高度

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
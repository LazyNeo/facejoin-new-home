<template>
	<div class="imgSlider-wrap">
		<div class="imgSlider-container">
			<div class="imgSlider-body"
					 style="width: 300%">
				<div class="imgSlider-item"
						 v-for="item of slider_items"
						 :style="{backgroundImage: 'url(' + item.src + ')',
						 				 width: '33%'}">
				</div>
			</div>
		</div>
		<div class="imgSlider-wrap"></div>
	</div>
</template>

<script>
export default {
  data () {
    return {
      slider_items: [{
        src: 'http://facejoin.img-cn-shenzhen.aliyuncs.com/facejoin/Wc3jbhNdFeB5Zxx4.png',
        isActive: false
      }, {
        src: 'http://facejoin.img-cn-shenzhen.aliyuncs.com/facejoin/Wc3jbhNdFeB5Zxx4.png',
        isActive: false
      }, {
        src: 'http://facejoin.img-cn-shenzhen.aliyuncs.com/facejoin/Wc3jbhNdFeB5Zxx4.png',
        isActive: false
      }]
    }
  },
  props: {
    img_num: '3',
    slider_imgs: [{
      src: 'http://facejoin.img-cn-shenzhen.aliyuncs.com/facejoin/Wc3jbhNdFeB5Zxx4.png',
      isActive: false
    }, {
      src: 'http://facejoin.img-cn-shenzhen.aliyuncs.com/facejoin/Wc3jbhNdFeB5Zxx4.png',
      isActive: false
    }, {
      src: 'http://facejoin.img-cn-shenzhen.aliyuncs.com/facejoin/Wc3jbhNdFeB5Zxx4.png',
      isActive: false
    }]
  },
  computed: {

  },
  methods: {}
}
</script>

<style lang="less">
	.imgSlider-wrap {
		position: relative;
	}
	.imgSlider-container {
		overflow: hidden;
	}
	.imgSlider-body {
		font-size: 0;
	}
	.imgSlider-item{
		display: inline-block;
		width: 100%;
		height: 530px;
		background: center/cover;
	}
</style>
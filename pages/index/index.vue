<template>
	<view style="width: 100vw;">
		<!-- <text>position: {{ position }}</text>
		<movable-area style="width: 100vw; height: 100vw; background: #8F8F94;" >
			<movable-view :x="x" :y="y" direction="all" @change="onChange" style="width: 100px; height: 100px; background: #ececec;;"> 
				<image src="../../static/1.jpg" mode="aspectFit" style="width: 100px; height: 100px;"></image>
			</movable-view>
			 
        </movable-area>
		 -->
		<button type="primary" @click="chooseImage">选择照片</button>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				title: 'Hello',
				x: 0,
				y: 0,
				choosenImagePaths: [],
				currentImageIndex: -1,
			}
		},
		
		computed:{
			position(){
				return `x:${this.x}, y:${this.y}`
			}
		},
		
		onReady() {
			// this.x = -30,
			this.y = -50
		},
		methods: {
			//选择图片
			chooseImage() {
				const _this = this
				uni.chooseImage({
					success(res) {
						_this.choosenImagePaths = res.tempFilePaths
						_this.currentImageIndex = 0
						// _this.opacity = 1
					}
				})
			},
			onChange(e){
				console.log(e.detail)
				this.x = e.detail.x
				this.y = e.detail.y
			},
			
			tap(){
				this.$nextTick(function(){
					this.x = 100,
					this.y = 100
				})
			}
		}
	}
</script>

<style>
	.content {
		text-align: center;
		height: 400upx;
	}

	.logo {
		height: 200upx;
		width: 200upx;
		margin-top: 200upx;
	}

	.title {
		font-size: 36upx;
		color: #8f8f94;
	}
</style>

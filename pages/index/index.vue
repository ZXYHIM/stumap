<template>
	<view class="container">
		<view>
			<image src="../../static/image/banner@2x.png" class="banner"></image>
		</view>
		<view class="features">
			<navigator class="create" url="../list/list">
				<image src="../../static/image/create@2x.png" mode="" class="featuresImg"></image>
				<text class="featuresText">创建同学录</text>
			</navigator>
			<view class="enter">
				<image src="../../static/image/Input@2x.png" mode="" class="featuresImg"></image>
				<text class="featuresText">输入邀请码</text>
			</view>
		</view>
		<view class="cu-bar bg-white solid-bottom margin-top listw">
						<view class="action">
							<text class="stutitle">同学录列表</text>
						</view>
					</view>
					<view class="cu-list menu-avatar listw">
						<view class="cu-item" v-for="(users,index) in user" :key=index>
							<view class="cu-avatar round lg" style="background-image:url(../../static/image/listimg@2x.png);"></view>
							<view class="content">
								<view class="text-grey">{{users.name}}</view>
								<view class="text-gray text-sm flex">
									<view class="text-cut">
										<text></text>
										{{users.category_id}}
									</view> </view>
							</view>
							<view class="aclick" @tap="iconClick" :data-id=users.category_id>
								<image src="../../static/image/mapicon@2x.png" mode="" class="iconimg"></image>
								<text class="icontext">地图</text>
							</view>
						</view>
					</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				user: [],
				
			}
		},
		onLoad:function(){
			uni.request({
				url:"https://elm.cangdu.org/shopping/v2/foods?offset=0&limit=20&restaurant_id=2",
				method:"GET",
				data:{},
				success: (res) => {
					this.user=res.data;
					
				},
				fail: () => {
					
				},
				complete: () => {
					
				}
			})
		},
		methods: {
		    iconClick(e){
				var id =e.currentTarget.dataset.id;
				uni.navigateTo({
					url:'../map/map?id='+id
				})
			}
		},
		
	}
</script>

<style>
	page{
		margin: 0;
		padding: 0;
	}
	.container {
	}
	.banner{
		width: 750rpx;
		height: 220rpx;
	}
	.features{
		width: 750rpx;
		height: 140rpx;
		display: flex;
		flex-direction: row;
		margin-top: -50rpx;
		position: relative;
	}
	.create{
		width: 340rpx;
		height: 140rpx;
		margin-left: 24rpx;
		display: flex;
		align-items: center;
		background:rgba(255,255,255,1);
		box-shadow:0pt 2pt 5pt 0pt rgba(7,189,99,0.25);
		border-radius:10rpx;
		align-content: center;
			}
	.featuresImg{
		width: 76rpx;
		height: 76rpx;
		margin-left: 40rpx;
		margin-top: 32rpx;
		margin-bottom: 32rpx;
	}
	.featuresText{
		font-size:30rpx;
		font-family:PingFang SC;
		font-weight:bold;
		color:rgba(7,189,99,1);
		line-height:37rpx;
		margin-left: 20rpx;
	}
	.enter{
		width: 340rpx;
		height: 140rpx;
		margin-left: 22rpx;
		margin-right: 24rpx;
		display: flex;
		align-items: center;
		background:rgba(246,252,249,1);
		box-shadow:0pt 2pt 5pt 0pt rgba(7,189,99,0.25);
		border-radius:10rpx;
		
	}
	.stutitle{
		font-size:32rpx;
		font-weight:400;
		color:rgba(7,189,99,1);
	}
	.listw{
		width: 702rpx;
		margin-left: 24rpx;
		margin-right: 24rpx;
		box-shadow:0px 2px 5px 0px rgba(7,189,99,0.25);
		border-radius:8rpx;
	}
	.iconclick{
		display: flex;
		justify-content: row;
	}
	.aclick{
		display: flex;
		flex-direction: column;
		align-items: center;
		margin-right: 38rpx;
	}
	.iconimg{
		width: 80rpx;
		height: 80rpx;
	}
	.icontext{
		font-size: 20rpx;
		color: #07BD63;
	}
</style>

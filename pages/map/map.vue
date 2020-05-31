<template>
	<view class="">
		<map id="map1" ref="map1" class="mapstyle"></map>
			<cover-view class="mapflex">
				<cover-view class="maptop">
					<cover-view>{{food}}</cover-view>
					<cover-view>{{foodid}}</cover-view>
					<cover-view>查看地图</cover-view>
				</cover-view>
				<cover-view class="mapconter">
					<cover-image src="../../static/image/usersimg@2x.png" mode="" class="mapconterimg"></cover-image>
					<cover-view></cover-view>
					<cover-view></cover-view>
					<cover-image src="../../static/image/into@2x.png" mode="" class="mapcontericon"></cover-image>
				</cover-view>
				<cover-view class="mapfooter">
					<cover-view class="mapfoot">
						<cover-image src="../../static/image/invite@2x.png" mode="" class="mapfootimg"></cover-image>
						<cover-view class="mapfoottext">邀请同学加入</cover-view>
					</cover-view>
					<cover-view class="mapxian"></cover-view>
					<cover-view class="mapfoot">
						<cover-image src="../../static/image/share@2x.png" mode="" class="mapfootimg"></cover-image>
						<cover-view class="mapfoottext">分享同学地图</cover-view>
					</cover-view>
				</cover-view>
			</cover-view>
		</view>
		
	</view>
</template>

<script>
	export default{
		data(){
			return{
				foodid:[],
				foodname:[],
				food:[]
			}
		},
		onLoad:function(option){
			console.log(option.id)
			var food=option.id;
			console.log(food)
			uni.request({
				url:'https://elm.cangdu.org/shopping/v2/menu/'+food,
				method:"GET",
				data:{},
				success: (res) => {
					this.foodid=res.data;
					console.log(this.foodid)
				},
				fail: () => {
					
				},
				complete: () => {
					
				}
			})
		}
	}
</script>

<style>
	page{
		margin: 0;
		padding: 0;
	}
	.mapstyle{
		width: 750rpx;
		height: 1334rpx;
	}
	.mapflex{
		width: 750rpx;
		height: 700rpx;
		background-color: #FFFFFF;
		position: fixed;
		bottom: 0rpx;
		left: 0rpx;
		min-height: 700rpx;
	}
	.maptop{
		width: 750rpx;
		height: 144rpx;
	}
	.mapconter{
		width: 750rpx;
		height: 466rpx;
		margin-left: 20rpx;
		margin-top: 19rpx;
	}
	.mapcontericon{
		width: 14rpx;
		height: 26rpx;
		
	}
	.mapconterimg{
		width: 87rpx;
		height: 87rpx;
	}
	.mapfooter{
		width: 750rpx;
		height: 100rpx;
		display: flex;
		align-items: center;
		align-content: center;
		flex: 1;
	}
	.mapfoot{
		width: 374rpx;
		display: flex;
		flex-wrap: wrap;
		align-content: center;
	}
	.mapxian{
		width:1px;
		height:70px;
		background:rgba(230,230,230,1);
	}
	.mapfootimg{
		width: 46rpx;
		height: 46rpx;
		margin-left: 66rpx;
	}
	.mapfoottext{
		font-size:28rpx;
		font-weight:400;
		color:rgba(7,189,99,1);
		margin-left: 25rpx;
	}
</style>

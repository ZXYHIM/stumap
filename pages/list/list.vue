<template>
	<view class="create">
		<form @submit="tijiao">
				        <view class="cu-form-group margin-top">
							<view class="title">普通选择</view>
							<picker @change="PickerChange" :value="index" :range="picker" v-model='formdata.xuanze'>
								<view class="picker">
									{{index>-1?picker[index]:'请选择'}}
								</view>
							</picker>
						</view>
						<view class="cu-form-group">
							<view class="title">邮件</view>
							<input placeholder="两字短标题" name="input" v-model='formdata.emal'></input>
						</view>
						<view class="cu-form-group">
							<view class="title">输入框</view>
							<input placeholder="三字标题" name="input" v-model='formdata.shuru'></input>
						</view>
						<view class="cu-form-group">
							<view class="title">收货地址</view>
							<input placeholder="统一标题的宽度" name="input" v-model='formdata.shouhuo'></input>
						</view>
			<button form-type="submit" class="btn-group">提交</button>			
		</form>
	</view>
</template>

<script>
	export default{
		data(){
			return{
				index:-1,
				picker: ['喵喵喵', '汪汪汪', '哼唧哼唧'],
				formdata:[
					{shouhuo:'',
					shuru:'',
					emal:'',
					xuanze:''}
				],
				datas:[]
			}
		},
		methods:{
			PickerChange(e) {
				this.index = e.detail.value;
			    console.log(this.index)
						},
			tijiao(e){
					// uni.navigateBack({
					// 	delta:1
					// })
					var formshuju={};
					formshuju.shuru=this.formdata.shuru;
					formshuju.xuanze=this.picker[this.index];
					formshuju.shouhuo=this.formdata.shouhuo;
					formshuju.emal=this.formdata.emal;
					console.log(formshuju)
					// uni.request({
					        // url: '', //  数据传到的地址
					        // data: formdata,//传入的数据
					        // method: 'POST', 
					        // header: {// 设置请求的 header
					        //   'content-type': 'application/x-www-form-urlencoded'   //这是传输方式为post的写法 ； 如果是get 则是'Content-Type': 'application/json'
					        // },
					        // success: function (res) {
					        //   console.log(JSON.stringify(res.data))
					        //   wx.showModal({      //提交成功 ，弹框
					        //     content: '提交成功',
			// 		            success: function (res) {
			// 		              if (res.confirm) {   //如果点击弹框的确认则进行下面的操作
			// 		              }
			// 		            }
			// 		          })
			//                }
			// })
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
			
		}
	
	}
</script>

<style>
</style>

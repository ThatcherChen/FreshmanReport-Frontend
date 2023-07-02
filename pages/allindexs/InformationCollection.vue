<template>

	<view class="">
		<u-form :model="form" ref="uForm">

			<u-form-item label="姓名" prop="name">
				<u-input v-model="form.name" type="text" />

			</u-form-item>
			<u-form-item label="身份证号" prop="idnumber">
				<u-input v-model="form.idnumber" type="text" />

			</u-form-item>
			<u-form-item label="简介" prop="intro">
				<u-input v-model="form.intro" />
			</u-form-item>
			<u-form-item label="性别">
				<u-input v-model="form.sex" type="select" border: true @click="show=true" />
				<u-action-sheet :list="actionSheetList" v-model="show" @click="actionSheetCallback"></u-action-sheet>
			</u-form-item>
			<u-form-item label="兴趣">
				<u-checkbox-group @change="checkboxGroupChange">
					<u-checkbox @change="checkboxChange" v-model="item.checked" v-for="(item, index) in interestlist"
						:key="index" :name="item.name">{{item.name}}</u-checkbox>
				</u-checkbox-group>
			</u-form-item>
			
			<u-form-item label="专业">
				<u-input v-model="form.major" type="select" border: true @click="showmajor=true" />
				<u-select v-model="showmajor" mode="single-column" :list="majorlist" @confirm="confirmmajor"
					@click="majorback"></u-select>
			</u-form-item>
			<u-form-item label="所在地区">
				<u-input v-model="form.city" type="select" border: true @click="showcity=true" />
				<u-select v-model="showcity" mode="mutil-column-auto" :list="citylist" @confirm="confirmcity"
					@click="cityback"></u-select>
			</u-form-item>
		</u-form>
		<view>
			<u-upload ref="uUpload" @on-uploaded="onUploaded" :action="action" :auto-upload="false" :show-tips="false"
				@on-remove="onRemove"></u-upload>
			<u-button :ripple="true" ripple-bg-color="#909399" shape="square" size="medium"
				@click="submit">上传图片</u-button>
		</view>
		<u-button @click="submit">提交</u-button>

	</view>
</template>

<script>
	export default {
		data() {
			return {
				//////////
				form: {
					name: '',
					intro: '',
					sex: '',
					city: '',
					major: '',
					idnumber: ''
				},
				/////////////
				
				avatarArr: [],
				show: false,
				showcity: false,
				showmajor: false,
				//////////
				actionSheetList: [

					{
						text: '男'
					},
					{
						text: '女'
					},
					{
						text: '保密'
					}
				],
				////////////////
				rules: {
					name: [{
						required: true,
						message: '请输入姓名',
						// 可以单个或者同时写两个触发验证方式 
						trigger: ['change', 'blur'],
					}],
					intro: [{
						min: 5,
						message: '简介不能少于5个字',
						trigger: 'change',
					}],
					idnumber: [
						{
							len: 18,
							message: '身份证位数不是18位',
							trigger: 'change'
						}
					]
				},
				/////////////
				citylist: [{
						value: 1,
						label: '中国',
						children: [{
								value: 2,
								label: '广东',
								children: [{
										value: 3,
										label: '深圳'
									},
									{
										value: 4,
										label: '广州'
									}
								]
							},
							{
								value: 5,
								label: '广西',
								children: [{
										value: 6,
										label: '南宁'
									},
									{
										value: 7,
										label: '桂林'
									}
								]
							}
						]
					},
					{
						value: 8,
						label: '美国',
						children: [{
							value: 9,
							label: '纽约',
							children: [{
								value: 10,
								label: '皇后街区'
							}]
						}]
					}
				],
				//////////////////////
				majorlist: [{
						value: '1',
						label: '物联网'
					},
					{
						value: '2',
						label: '软件工程'
					},
					{
						value: '3',
						label: '大数据技术'
					},
					{
						value: '4',
						label: '信息安全'
					}
				],
				//////////////////
				src: 'http://pic2.sc.chinaz.com/Files/pic/pic9/202002/hpic2119_s.jpg',
				////////////////
				interestlist: [{
						name: '跳绳',
						checked: false,
						disabled: false
					},
					{
						name: '游泳',
						checked: false,
						disabled: false
					},
					{
						name: '跑步',
						checked: false,
						disabled: false
					}
				],
				///////////////
			};
		},
		///////////////////////////////////////////////////
		methods: {

			////////////
			actionSheetCallback(index) {
				this.form.sex = this.actionSheetList[index].text;
			},
			//////////////////

			///////////////

			//////////////
			submit() {
				this.$refs.uForm.validate(valid => {
					if (valid) {
						console.log('验证通过');
					} else {
						console.log('验证失败');
					}
				});
			},
			///////////////
			confirmmajor(major) {
				this.form.major = major[0].label;
			},
			///////////////
			confirmcity(city) {
				this.form.city = city[0].label + '-' + city[1].label + '-' + city[2].label;
			},
			///////////////
			// 选中某个复选框时，由checkbox时触发
			checkboxChange(e) {
				//console.log(e);
			},
			// 选中任一checkbox时，由checkbox-group触发
			checkboxGroupChange(e) {
				// console.log(e);
			},
			//////////////
			submit() {
				this.$refs.uUpload.upload();
			},
			////////////
			onUploaded(lists) {
				this.avatarArr = lists;
			},
			/////////////
			onRemove(index, lists) {
				console.log('图片已被移除')
			},
			/////////////
			beforeUpload(index, list) {
				// 返回一个promise
				return new Promise((resolve, reject) => {
					this.$u.post('http://www.tp5.com/index.php/index/index/hello').then(res => {
						// resolve()之后，将会进入promise的组件内部的then回调，相当于返回true
						resolve();
					}).catch(err => {
						// reject()之后，将会进入promise的组件内部的catch回调，相当于返回false
						reject();
					})
				})
			},
			////////////
			
			/////////////
		},
		///////////////////////////////////////////////////////
		// 必须要在onReady生命周期，因为onLoad生命周期组件可能尚未创建完毕
		onReady() {
			this.$refs.uForm.setRules(this.rules);
		}
	};
</script>
<style lang="scss">

</style>
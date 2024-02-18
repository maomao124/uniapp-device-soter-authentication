<template>
	<view class="content">
		<view v-for="url in urlList">
			<button type="primary" @click="to(url)">{{url}}</button>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				title: 'Hello',
				urlList: ['test1', 'test2','test3','test4','test5'],
			}
		},
		onLoad() {

		},
		methods: {
			to(url) {
				uni.navigateTo({
					url: '/pages/index/' + url + '/' + url
				})
			}
		}
	}
</script>

<style>
	button {
		margin: 5px;
	}
</style>
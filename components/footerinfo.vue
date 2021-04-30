<template name="footerinfo">
	<view class="tm-every-center flex-direction text-sm line-sub justify-center">
		<view class="margin-sm text-grey text-center">©2020 {{name}}</view>
		<view class="margin-sm text-grey text-center" @click="copy('https://space.bilibili.com/86643192')">Powered by Linkia.</view>
		<text>\n</text>
		<text>\n</text>
		<text>\n</text>
		<text>\n</text>
	</view>
</template>

<script>
	import cfg from '@/static/config.js';
	import API from '@/utils/api.js';
	export default {
		data() {
			return {
				domain: API.getDomain(),
				name: cfg.getname
			};
		},
		methods: {
			copy(href) {
				// #ifdef H5
				window.open(href);
				// #endif
				// #ifdef APP-PLUS
				plus.runtime.openURL(href, function(res) {});
				// #endif
				// #ifdef MP
				uni.setClipboardData({
					data: href,
					success: function() {
						uni.showToast({
							title: '链接已复制',
							duration: 2000
						});
					}
				});
				// #endif
			}
		}
	}
</script>

<style>

</style>

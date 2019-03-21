<template>
	<view class="center">
		<view class="header" v-bind:class="{ status: isH5Plus }">
			<view class="userinfo">
				<view class="face"><image :src="userinfo.face"></image></view>
				<view class="info">
					<view class="username">{{ userinfo.username }}</view>
					<view class="integral">积分:{{ userinfo.integral }}</view>
				</view>
			</view>
			<view class="setting"><image src="../../static/mycenter/setting.png"></image></view>
		</view>
		<view class="orders">
			<view class="box">
				<view class="label" v-for="(row, index) in orderTypeLise" :key="row.name" hover-class="hover" @tap="toOrderType(index)">
					<view class="icon">
						<view class="badge" v-if="row.badge > 0">{{ row.badge }}</view>
						<image :src="'../../static/mycenter/' + row.icon"></image>
					</view>
					{{ row.name }}
				</view>
			</view>
		</view>
		<view class="list" v-for="(list, list_i) in severList" :key="list_i">
			<view class="li" v-for="(li, li_i) in list" @tap="toPage(list_i, li_i)" v-bind:class="{ noborder: li_i == list.length - 1 }" hover-class="hover" :key="li.name">
				<view class="icon">
					<image :src="'../../static/mycenter/sever/' + li.icon"></image>
				</view>
				<view class="text">{{ li.name }}</view>
				<image class="to" src="../../static/mycenter/to.png"></image>
			</view>
		</view>
	</view>
</template>
<script>
export default {
	data() {
		return {
			//#ifdef APP-PLUS
			isH5Plus: true,
			//#endif
			userinfo: {},
			orderTypeLise: [
				//name-标题 icon-图标 badge-角标
				{ name: '事件', icon: 'event.png', badge: 0 },
				{ name: '关注', icon: 'like.png', badge: 0 },
				{ name: '活动', icon: 'activity.png', badge: 0 },
				{ name: '订单', icon: 'order.png', badge: 2 }
			],
			severList: [
				[
					{ name: 'Item1', icon: 'point.png' },
					{ name: 'Item2', icon: 'quan.png' },
					{ name: 'Item3', icon: 'momey.png' },
					{ name: 'Item4', icon: 'renw.png' }
				],
				[
					{ name: 'Item5', icon: 'mingxi.png' },
					{ name: 'Item6', icon: 'choujiang.png' },
					{ name: 'Item7', icon: 'addr.png' },
					{ name: 'Item8', icon: 'bank.png' }
				]
			]
		};
	},
	onLoad() {
		//加载
		this.init();
	},
	methods: {
		init() {
			//用户信息
			this.userinfo = {
				face: '../../static/mycenter/face.jpeg',
				username: '哈哈user',
				integral: '1435'
			};
		},
		//用户点击订单类型
		toOrderType(index) {
			uni.showToast({ title: this.orderTypeLise[index].name });
		},
		//用户点击列表项
		toPage(list_i, li_i) {
			uni.showToast({ title: this.severList[list_i][li_i].name });
		}
	}
};
</script>

<style lang="scss">
page {
	background-color: #fff;
}
.header {
	&.status {
		padding-top: var(--status-bar-height);
	}
	background-color: #1296db;
	width: 92%;
	height: 30vw;
	padding: 0 4%;
	display: flex;
	align-items: center;
	.userinfo {
		width: 90%;
		display: flex;
		.face {
			flex-shrink: 0;
			width: 15vw;
			height: 15vw;
			image {
				width: 100%;
				height: 100%;
				border-radius: 100%;
			}
		}
		.info {
			display: flex;
			flex-flow: wrap;
			padding-left: 30upx;
			.username {
				width: 100%;
				color: #fff;
				font-size: 40upx;
			}
			.integral {
				display: flex;
				align-items: center;
				padding: 0 20upx;
				height: 40upx;
				color: #fff;
				background-color: rgba(0, 0, 0, 0.1);
				border-radius: 20upx;
				font-size: 24upx;
			}
		}
	}
	.setting {
		flex-shrink: 0;
		width: 6vw;
		height: 6vw;
		image {
			width: 100%;
			height: 100%;
		}
	}
}
.hover {
	background-color: #eee;
}
.orders {
	background-color: #1296db;
	width: 100%;
	height: 11vw;
	margin-bottom: calc(11vw + 40upx);
	display: flex;
	align-items: flex-start;
	margin-top: 20upx;
	.box {
		width: 100%;
		height: 22vw;
		background-color: #fefefe;
		box-shadow: 0 0 20upx rgba(0, 0, 0, 0.15);
		margin-bottom: 40upx;
		display: flex;
		align-items: center;
		justify-content: center;
		.label {
			display: flex;
			align-items: center;
			justify-content: center;
			flex-flow: wrap;
			width: 100%;
			height: 16vw;
			color: #666666;
			font-size: 26upx;
			.icon {
				position: relative;
				width: 7vw;
				height: 7vw;
				margin: 0 10vw;
				.badge {
					position: absolute;
					width: 4vw;
					height: 4vw;
					background-color: #ec6d2c;
					top: -1vw;
					right: -1vw;
					border-radius: 100%;
					font-size: 20upx;
					color: #fff;
					display: flex;
					align-items: center;
					justify-content: center;
					z-index: 10;
				}
				image {
					width: 7vw;
					height: 7vw;
					z-index: 9;
				}
			}
		}
	}
}
.list {
	width: 100%;
	border-bottom: solid 26upx #f1f1f1;
	.li {
		width: 92%;
		height: 100upx;
		padding: 0 4%;
		border-bottom: solid 1upx #e7e7e7;
		display: flex;
		align-items: center;
		&.noborder {
			border-bottom: 0;
		}
		.icon {
			flex-shrink: 0;
			width: 50upx;
			height: 50upx;
			image {
				width: 50upx;
				height: 50upx;
			}
		}
		.text {
			padding-left: 20upx;
			width: 100%;
			color: #666;
		}
		.to {
			flex-shrink: 0;
			width: 40upx;
			height: 40upx;
		}
	}
}
</style>

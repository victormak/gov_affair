<template>
	<view class="content">
		<uni-swipe-action :options="options" :messagesList="messages">
		</uni-swipe-action>
	</view>
</template>

<script>
import uniSwipeAction from "@/components/uni-swipe-action/uni-swipe-action.vue"
export default {
	components: {uniSwipeAction},
	data() {
		return {
		focus:false,
    isShowView:true,
		options: [{
				text: '置顶',
				style: {
						backgroundColor: '#C7C6CD'
				}
		}, {
				text: '删除',
				style: {
						backgroundColor: '#dd524d'
				}
		}],
    messages:[
      {
        title:"马云",
        url:"../../static/logo.png",
        message:"什么鬼，我有支付宝",
        time:"15:15",
        count:5,
				stick: false,//是否为置顶状态
				disabled: true //是否禁止滑动

      },
      {
        title:"马化腾",
        url:"../../static/logo.png",
        message:"哈哈哈，我要一统江湖啦",
        time:"15:15",
        count:22,
				stick: true,
				disabled: false

        },
      {
        title:"李彦宏",
        url:"../../static/logo.png",
        message:"抄袭我的吧，我早都做过了",
        time:"12:13",
        count:1,
				stick: false,
				disabled: false
        },
      {
        title:"雷军",
        url:"../../static/logo.png",
        message:"微信给你下线，看你还嘚瑟",
        time:"12:11",
        count:0,
				stick: false,
				disabled: false
        },
      {
        title:"前端开发者",
        url:"../../static/logo.png",
        message:"我们的春天来啦，哈哈哈",
        time:"11:35",
        count:0,
				stick: false,
				disabled: false
        },
      {
        title:"微信小程序",
        url:"../../static/logo.png",
        message:"谁有内测资格啊啊，300万买一个",
        time:"08:23",
        count:0,
				stick: false,
				disabled: false
        },
      {
        title:"小程序",
        url:"../../static/logo.png",
        message:"这个IDE方便都不要配置了",
        time:"03:21",
        count:5,
				stick: false,
				disabled: false
        },
      {
        title:"微信应用号开发群",
        url:"../../static/logo.png",
        message:"开发的局限性太大了",
        time:"03:08",
        count:99,
				stick: false,
				disabled: false
         },
      {
        title:"后台",
        url:"../../static/logo.png",
        message:"不看好小程序",
        time:"02:45",
        count:0,
				stick: false,
				disabled: false
        },
      {
        title:"闯天下",
        url:"../../static/logo.png",
        message:"微信太强大了",
        time:"01:09",
        count:0,
				stick: false,
				disabled: false
        },
      {
        title:"小程序",
        url:"http://img1.3lian.com/gif/more/11/201212/58ec7c89b16c529fc9d0dc440a72e14d.jpg",
        message:"有快来看直播啦，学习开始啦",
        time:"00:24",
        count:2,
				stick: false,
				disabled: false
         }
    ]
		};
	},
	onLoad() {},
	methods: {}
};
</script>

<style>
.content {
}

</style>

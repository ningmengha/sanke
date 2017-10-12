<template>
    <div class="fillcontain">
        <head-top></head-top>
        <p class="explain_text">淘亿服装批发后台管理系统</p>
        <p class="explain_text">首次注册成为普通管理员</p>
        <p class="explain_text">管理员可添加，修改信息</p>
        <p class="explain_text">超级管理员可删除信息</p>
    </div>
</template>

<script>
	import headTop from '../components/headTop'
    export default {
    	components: {
    		headTop,
    	},
    }
</script>

<style lang="less">
	@import '../style/mixin';
	.explain_text{
		margin-top: 20px;
		text-align: center;
		font-size: 20px;
		color: #333;
	}
</style>

<template>
<div class="app-container">
	<el-tooltip placement="bottom">
  		<div slot="content">
  			名称：你是最好的自己<br /><br />
  			作者：杨杨<br /><br />
  			出版日期：2014-03-10<br /><br />
  			评分：8.6
  		</div>
  		<el-button>Top center</el-button>
	</el-tooltip>
</div>
</template>

<script>
	import {global} from 'src/global/global';
	import {api} from 'src/global/api';
</script>
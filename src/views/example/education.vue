<template>
	<div class="app-container">
  		<el-table :data="tableData" border style="width: 100%" :default-sort = "{prop: 'date', order: 'descending'}">
    		<el-table-column prop="id" label="编号" sortable width="180"></el-table-column>
    		<el-table-column prop="image" label="封面"> 
    			<!-- <img :src="img1" alt="" style="vertical-align: middle;"> -->
    		</el-table-column>
    		<el-table-column prop="name" label="名称"></el-table-column>
    		<el-table-column prop="author" label="作者"></el-table-column>
    		<el-table-column prop="date" label="日期" sortable width="180"></el-table-column>
    		<el-table-column prop="score" label="评分" sortable width="180"></el-table-column>
  		</el-table>
	</div>
</template>

<script>
 	import {global} from 'src/global/global';
 	import {api} from 'src/global/api';
 	import img1 from 'assets/img/edu/edu0001.jpg';


  	export default {
    	data() {
      		return {
        		tableData: [{
	        		id: 'edu0001',
	        		image: img1,
	        		name: '代码大全（第2版）',
	        		author: '[美]史蒂夫·迈克康奈尔',
	          		date: '2006-03-05',
	          		score:'9.3'	
	        	}, {
	          		id: 'edu0002',
	        		image: '',
	        		name: 'C程序设计语言',
	        		author: '[美]Brian W. Kernighan',
	          		date: '2004-01-01',
	          		score:'9.4'
	        	}, {
	          		id: 'edu0003',
	        		image: '',
	        		name: '算法导论（原书第2版）',
	        		author: '[美] Thomas H.Comen',
	          		date: '2006-09-09',
	          		score:'9.3'
	        	}, {
	          		id: 'edu0004',
	        		image: '',
	        		name: '算法（第4版）',
	        		author: '[美]Nicholas C.Zakas',
	          		date: '2012-03-29',
	          		score:'9.3'
        		}, {
	          		id: 'edu0005',
	        		image: '',
	        		name: 'Java编程思想',
	        		author: '[美] Bruce Eckel',
	          		date: '2007-06-03',
	          		score:'9.1'
        		}, {
	          		id: 'edu0006',
	        		image: '',
	        		name: '黑客与画家',
	        		author: '[美] Paul Graham',
	          		date: '2011-04-05',
	          		score:'8.7'
        		}, {
	          		id: 'edu0007',
	        		image: '',
	        		name: '集体智慧编程',
	        		author: 'TOBY SEGARAN',
	          		date: '2009-01-08',
	          		score:'9.0'
        		}, {
	          		id: 'edu0008',
	        		image: '',
	        		name: 'Python编程：从入门到实践',
	        		author: '斯维加特',
	          		date: '2016-07-01',
	          		score:'8.7'
        		}, {
	          		id: 'edu0009',
	        		image: '',
	        		name: '程序员的自我修养',
	        		author: '俞甲子',
	          		date: '2009-04-08',
	          		score:'8.8'
        		}, {
	          		id: 'edu0010',
	        		image: '',
	        		name: 'Fluent Python',
	        		author: 'Andrew Hunt',
	          		date: '2005-01-08',
	          		score:'9.5'
        		}]
      		}
    	},
    	methods: {
      		formatter(row, column) {
        		return row.address;
      		}
    	}
  	}
</script>
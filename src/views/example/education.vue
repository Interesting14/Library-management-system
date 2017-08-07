<template>
	<div class="app-container">

  		<el-table :data="tableData" border style="width: 100%" :default-sort = "{prop: 'date', order: 'descending'}">
    		<el-table-column prop="id" label="编号" sortable width="180" align="center"></el-table-column>
    		<el-table-column  label="封面" align="center"> 
    			<template scope="scope">
    				<img :src="scope.row.image">
    				<!-- 组件里面包含组件，作用域的问题，应用封装好的scope.row.方法 -->
    				<!-- prop是渲染文本的 -->
    			</template>
    		</el-table-column>
    		<el-table-column prop="name" label="名称" align="center"></el-table-column>
    		<el-table-column prop="author" label="作者" align="center"></el-table-column>
    		<el-table-column prop="date" label="日期" sortable width="180" align="center"></el-table-column>
    		<el-table-column prop="score" label="评分" sortable width="180" align="center"></el-table-column>

    		<el-table-column label="操作" width="120" align="center">
      			<template scope="scope">
        			<el-button @click.native.prevent="deleteRow(scope.$index, tableData)" type="text" size="small">删除
        			</el-button>

        			<el-button type="text" @click="dialogVisible = true">详情</el-button>
						<el-dialog 
							title="详情"
  							:visible.sync="dialogVisible"
  							size="tiny"
  							:before-close="handleClose"
  						>
  							<span>
								<h2>代码大全（第2版）</h2>
								<p style="text-indent:2em;">第2版的《代码大全》是著名IT畅销书作者史蒂夫·迈克康奈尔11年前的经典著作的全新演绎：第2版不是第一版的简单修订增补，而是完全进行了重写；增加了很多与时俱进的内容。这也是一本完整的软件构建手册，涵盖了软件构建过程中的所有细节。它从软件质量和编程思想等方面论述了软件构建的各个问题，并详细论述了紧跟潮流的新技术、高屋建瓴的观点、通用的概念，还含有丰富而典型的程序示例。这本书中所论述的技术不仅填补了初级与高级编程技术之间的空白，而且也为程序员们提供了一个有关编程技巧的信息来源。这本书对经验丰富的程序员、技术带头人、自学的程序员及几乎不懂太多编程技巧的学生们都是大有裨益的。可以说，无论是什么背景的读者，阅读这本书都有助于在更短的时间内、更容易地写出更好的程序。</p>
  							</span>

  							<span slot="footer" class="dialog-footer">
    							<el-button @click="dialogVisible = false">取 消</el-button>
    							<el-button type="primary" @click="dialogVisible = false">确 定</el-button>
  							</span>
						</el-dialog>
      			</template>
    		</el-table-column>

  		</el-table>

  		<div class="block">
    		<el-pagination 
    			@size-change="handleSizeChange" 
    			@current-change="handleCurrentChange" 
    			:current-page="currentPage4" 
    			:page-sizes="[10, 20, 30, 40]" 
    			:page-size="10" 
    			layout="total, sizes, prev, pager, next, jumper" 
    			:total="400"
    			style="margin-top: 30px;"
    		>
    		</el-pagination>
  		</div>

	</div>
</template>

<script>
 	import {global} from 'src/global/global';
 	import {api} from 'src/global/api';
 	import img1 from 'assets/img/edu/edu0001.jpg';
 	import img2 from 'assets/img/edu/edu0002.jpg';
 	import img3 from 'assets/img/edu/edu0003.jpg';
 	import img4 from 'assets/img/edu/edu0004.jpg';
 	import img5 from 'assets/img/edu/edu0005.jpg';
 	import img6 from 'assets/img/edu/edu0006.jpg';
 	import img7 from 'assets/img/edu/edu0007.jpg';
 	import img8 from 'assets/img/edu/edu0008.jpg';
 	import img9 from 'assets/img/edu/edu0009.jpg';
 	import img10 from 'assets/img/edu/edu0010.jpg';


  	export default {
    	data() {
      		return {
        		dialogVisible: false,
        		tableData: [{
	        		id: 'edu0001',
	        		image: img1,
	        		name: '代码大全（第2版）',
	        		author: '[美]史蒂夫·迈克康奈尔',
	          		date: '2006-03-05',
	          		score:'9.3'	
	        	}, {
	          		id: 'edu0002',
	        		image: img2,
	        		name: 'C程序设计语言',
	        		author: '[美]Brian W. Kernighan',
	          		date: '2004-01-01',
	          		score:'9.4'
	        	}, {
	          		id: 'edu0003',
	        		image: img3,
	        		name: '算法导论（原书第2版）',
	        		author: '[美] Thomas H.Comen',
	          		date: '2006-09-09',
	          		score:'9.3'
	        	}, {
	          		id: 'edu0004',
	        		image: img4,
	        		name: '算法（第4版）',
	        		author: '[美]Nicholas C.Zakas',
	          		date: '2012-03-29',
	          		score:'9.3'
        		}, {
	          		id: 'edu0005',
	        		image: img5,
	        		name: 'Java编程思想',
	        		author: '[美] Bruce Eckel',
	          		date: '2007-06-03',
	          		score:'9.1'
        		}, {
	          		id: 'edu0006',
	        		image: img6,
	        		name: '黑客与画家',
	        		author: '[美] Paul Graham',
	          		date: '2011-04-05',
	          		score:'8.7'
        		}, {
	          		id: 'edu0007',
	        		image: img7,
	        		name: '集体智慧编程',
	        		author: 'TOBY SEGARAN',
	          		date: '2009-01-08',
	          		score:'9.0'
        		}, {
	          		id: 'edu0008',
	        		image: img8,
	        		name: 'Python编程：从入门到实践',
	        		author: '斯维加特',
	          		date: '2016-07-01',
	          		score:'8.7'
        		}, {
	          		id: 'edu0009',
	        		image: img9,
	        		name: '程序员的自我修养',
	        		author: '俞甲子',
	          		date: '2009-04-08',
	          		score:'8.8'
        		}, {
	          		id: 'edu0010',
	        		image: img10,
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
      		},
      		deleteRow(index, rows) {
        		rows.splice(index, 1);
      		},
      		handleClose(done) {
        		this.$confirm('确认关闭？')
          		.then(_ => {
            		done();
          		})
          		.catch(_ => {});
            }
    	}
  	}
</script>
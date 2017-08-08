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
  							<h2>{{scope.row.name}}</h2>	
							<p style="text-indent:2em;">{{scope.row.detail}}</p>
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
 	import img1 from 'assets/img/yth/yth0001.jpg';
 	import img2 from 'assets/img/yth/yth0002.jpg';
 	import img3 from 'assets/img/yth/yth0003.jpg';
 	import img4 from 'assets/img/yth/yth0004.jpg';
 	import img5 from 'assets/img/yth/yth0005.jpg';
 	import img6 from 'assets/img/yth/yth0006.jpg';
 	import img7 from 'assets/img/yth/yth0007.jpg';
 	import img8 from 'assets/img/yth/yth0008.jpg';
 	import img9 from 'assets/img/yth/yth0009.jpg';
 	import img10 from 'assets/img/yth/yth0010.jpg';


  	export default {
    	data() {
      		return {
      			dialogVisible: false,
        		tableData: [{
	        		id: 'yth0001',
	        		image: img1,
	        		name: '挪威的森林',
	        		author: '[日] 村上春树',
	          		date: '2001-03-05',
	          		score:'8.0'	
	        	}, {
	          		id: 'yth0002',
	        		image: img2,
	        		name: '最好的我们',
	        		author: '八月长安',
	          		date: '2013-08-05',
	          		score:'8.7'
	        	}, {
	          		id: 'yth0003',
	        		image: img3,
	        		name: '一个人的好天气',
	        		author: '[日] 青山七惠',
	          		date: '2007-09-10',
	          		score:'7.6'
	        	}, {
	          		id: 'yth0004',
	        		image: img4,
	        		name: '此间的少年',
	        		author: '江南',
	          		date: '2004-01-29',
	          		score:'8.3'
        		}, {
	          		id: 'yth0005',
	        		image: img5,
	        		name: '动物凶猛',
	        		author: '王朔',
	          		date: '2004-02-03',
	          		score:'8.2'
        		}, {
	          		id: 'yth0006',
	        		image: img6,
	        		name: '余生，请多指教',
	        		author: '柏林石匠',
	          		date: '2016-10-05',
	          		score:'7.5'
        		}, {
	          		id: 'yth0007',
	        		image: img7,
	        		name: '何以笙箫默',
	        		author: '顾漫',
	          		date: '2007-04-08',
	          		score:'8.0'
        		}, {
	          		id: 'yth0008',
	        		image: img8,
	        		name: '少年巴比伦',
	        		author: '路内',
	          		date: ' 2008-08-01',
	          		score:'8.5'
        		}, {
	          		id: 'yth0009',
	        		image: img9,
	        		name: '坏一坏',
	        		author: '凉炘',
	          		date: '2017-04-01',
	          		score:'8.6'
        		}, {
	          		id: 'yth0010',
	        		image: img10,
	        		name: '你是最好的自己',
	        		author: '杨杨',
	          		date: '2014-03-10',
	          		score:'7.2',
	          		detail:"给所有年轻人信心的故事，“一个”app、微博、豆瓣、人人网最火热作者杨杨、张皓宸联合打造温情励志故事集加超人气手机摄影&创意插图，给你正能量的青春，不畏惧的未来！全彩四色，附赠三张祝福正能量明信片，一张随身行捧花卡！21个最感人的励志故事，150张最文艺摄影，10组超 级创意插图，构筑给所有年轻人的完美励志故事集。每个人都曾遭遇拒绝，遭遇失败，遭遇人生中的各种不快，都会在失败的时候怀疑自己是不是不够好，都会觉得世界上是不是没有人爱自己……不！你要相信，你是最好的自己。每当遇到阴雨天，就努力做自己的小太阳，正能量的青春，不畏惧的未来，你也可以拥有。“在给这本书起名字的最开始，我们本打算用‘愿你成为最好的自己’，假若这本书是你找回自己的航班的话，我们希望你也能在合上书本时，在旅程的最后找到生活的动力，成为最好的自己。"
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
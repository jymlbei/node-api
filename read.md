<!-- 项目需求 -->
	->需要使用到的
		create-react-app ---创建react脚手架
		npm start 启动命令
		npm run eject 讲项目解压
		项目需要安装以下依赖：
			1->axios //用于ajaxs请求
			2->element element-theme 作为项目的UI组件库
			3->redux 安装redux
			4->redux-thunk 安装redux-thunk用于redux发起异步请求
			5->react-redux 安装react-redux用于react与redux使用
			6->babel-plugin-transform-decorators-legacy 安装babel-plugin-transform-decorators-legacy 用于简化redux写法 :
				const App = connect()(APP) ====> @connect()
				<!-- 注意 需要在package.json中配置-->
					 "babel": {
						    "presets": [
						      "react-app"
						    ],
						    "plugins": [
						      "transform-decorators-legacy"
						    ]
						  },

			7->prop-styles 安装prop-styles 用于做为props值的校验

			8-> react-router-dom 安装react-router-dom 用于路由跳转


			<!-- 关于redux的理解 -->
			import {
				createStore
			} from 'redux'
			//引入一个对象，然后给对象方法

			const store =  createStore(someFunction)

			createStore 创建一个对象去改变state ，然后只有 someFunction 可以去改变 state的值，
			其他的组件通过指令去控制someFunction方法
			<!-- 方法 -->
			<!-- 这里的方法就是根据后面的指令去执行不同的操作 -->
			function someFunction(state=0,action){
				switch (action.type) {
					case add:
						return state + 1
					case remove:
						return state - 1
					default:
						return state
				}
			}
			<!-- 增加指令 -->
			export function doAdd() {
				return {
					type: add
				}
			}
			<!-- 减少指令 -->
			export function doRemove() {
				return {
					type: remove
				}
			}
			<!-- 异步增加指令 -->
			export function addAsync() {
				return dispatch => {
					setTimeout(() => {
						dispatch(doAdd())
					}, 2000)
				}
			}

<!--  -->


父子组件通信
子组件点击事件里通过this.props.somefunction(val)  调用，父组件在somefunction={(val)=>{
        this.setState({
            key:val
        })
    }}
进行子组件完成到父组件的传值通信

安装prop-types 进行检测暴露的组件方法传参的类型

import PropTypes from 'prop-types'

static propTypes = {
	selectAvator: PropTypes.func.isRequired // func指类型为function，isRequired（可选）  如果有isRequired，则function必传
}

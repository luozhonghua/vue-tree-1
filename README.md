# v-tree

> A Vue.js project


### 初始化参数
<table>
  <tr>
    <td>参数</td>
    <td>类型</td>
     <td>默认值</td>
    <td>描述</td>
  </tr> 
    <tr>
    <td>treeData</td>
    <td>Array</td>
     <td></td>
    <td>数据源，包含'id','text','icon','children'属性。<br/>示例：[
        {text:'xiaoming',
          id:'1',
          icon:'folder',
          children:[
              {text:'1-1',
                id:'1-1',
                icon:'folder',
                children:[
                  {text:'1-1-1',
                    id:'1-1-1',
                    icon:'file',
                  },{text:'1-1-2',
                    id:'1-1-2',
                    icon:'file'
                  }]
              },{
                text:'1-2',
                id:'1-2',
                icon:'folder',
              }]
        }
        ]</td>
  </tr>
   <tr>
    <td>checkBox</td>
    <td>Boolen</td>
     <td>false</td>
    <td>是否显示checkbox</td>
  </tr>
   <tr>
    <td>clickFun</td>
    <td>Function</td>
     <td></td>
    <td>鼠标点击事件</td>
  </tr>
 </table>
 ### 方法
 <table>
    <tr>
       <td>方法名称</td>
      <td>参数</td>
      <td>返回值</td>
      <td>描述</td>
    </tr>
   <tr>
       <td>getSelectedNode</td>
      <td>-</td>
      <td>返回选中的tree节点</td>
      <td></td>
    </tr>
    <tr>
       <td>getCheckedNodes</td>
      <td>-</td>
      <td>返回多选的tree节点</td>
      <td>在多选属性checkbox为true时有效。</td>
    </tr>
  </table>

![Image text]( /vtree.png )
### 使用示例
```
<template><div class="hello">
  <vtree :treeData='datas' ref='vtree' :clickFun='clickNode' :checkBox='checkbox'></vtree>
  <button @click='findSelected'>getNode</button></div>
</template>
<script>
  import vtree from './v-tree'
  export default {
  name: 'HelloWorld',
  methods:{
      findSelected(){
          console.log('you clicked' + JSON.stringify(this.$refs.vtree.getSelectedNode()));
          if(this.checkbox){
               console.log('you choosed ' + JSON.stringify(this.$refs.vtree.getCheckedNodes()))
          }
      },
      clickNode(target){
        console.log('you clicked '+ target)
      }
  },
  data () {
    return {
      msg: 'Welcome to Your vtree App',
      checkbox:true,
      datas:[
        {text:'xiaoming',
          id:'1',
          icon:'folder',
          children:[
              {text:'1-1',
                id:'1-1',
                icon:'folder',
                children:[
                  {text:'1-1-1',
                    id:'1-1-1',
                    icon:'file',

                  },{text:'1-1-2',
                    id:'1-1-2',
                    icon:'file'

                  }]
              
              },{
                text:'1-2',
                id:'1-2',
                icon:'file',
              }]
        },
        {text:'hua',
          id:'2',
          icon:'folder',
          children:[{
            text:'2-2',
            id:'2-2',
            icon:'file',
          }]
        },
        {text:'hua',
          id:'3',
          icon:'folder',
          children:[{
            text:'3-3',
            id:'3-3',
            icon:'file',
          }]
        }
        ]
    }
  },
  components:{vtree}
}
</script>
<style scoped>
.hello{
    float:left;
    width:400px;
    border:1px solid black;
}
</style>
```
## Build Setup

``` bash
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build

# build for production and view the bundle analyzer report
npm run build --report
```

For a detailed explanation on how things work, check out the [guide](http://vuejs-templates.github.io/webpack/) and [docs for vue-loader](http://vuejs.github.io/vue-loader).

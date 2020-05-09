<template>
  <div id="myChart" :style="{width: '500px', height: '400px'}"></div>
</template>

<script>
export default {
  name: 'hello',
  data () {
    return {
     testRes:[
          {
              name:"重庆",  //name点的名称
              value:169,   //value在y轴的位置高度
              orgNum:15485,
              regCapital:1907
          },  
          {
              name:"上海",
              value:176,
              orgNum:15485,
              regCapital:1907
          },
            {
              name:"文档",
              value:163,
              orgNum:15485,
              regCapital:1907
          },
            {
              name:"sss",
              value:113,
              orgNum:15485,
              regCapital:1907
          },
           {
              name:"kss",
              value:113,
              orgNum:15485,
              regCapital:1907
          }
      ]
    }
  },
  mounted(){
    this.drawLine();
  },
  methods: {
    drawLine(){
        // 基于准备好的dom，初始化echarts实例
        let myChart = this.$echarts.init(document.getElementById('myChart'))

// this.testRes = res.responBody.map(item => {
//      let jsonData = {}
//      jsonData.name = item.adminArea
//      jsonData.value = item.orgNum 
//      jsonData.regCapital = item.regCapital 
    
//      return jsonData
// })

        // 绘制图表
        myChart.setOption({
            title: { text: 'echarts' },
            tooltip: {
    trigger: 'item',
    formatter: function(a, b) {
        //进行格式处理
        return (
            `${a['name']}</br>机构数量: ${a['value']} (${a['data'].orgNum}%)</br>注册资金: ${a['data'].regCapital} 亿元 (${a['data'].regCapitalPercent}%)</br>职工人数: ${a['data'].orgNum} (${a['data'].employeeNumPercent}%)`
        )
    }
},

            xAxis: {
                data: ["重庆","上海","文档","sss","kss"]
            },
            yAxis: {},
            //series用于设置多个折线图
            series: [
                {
                    type:'line',
                    data:this.testRes
                }
            ]
        });
    }
  }
}
</script>

<style>

</style>
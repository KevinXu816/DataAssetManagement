<template>
  <div id="BasicInformation">
  
    <ul>
  
      <li>
  
        <span>所属数据实体</span>
  
        <span>{{data2.dataentityname}}</span>
  
      </li>
  
      <li>
  
        <span>属性名称</span>
  
        <span>{{data2.dataattributename}}</span>
  
      </li>
  
      <li>
  
        <span>业务定义</span>
  
        <span>{{data2.businessdefinition}}</span>
  
      </li>
  
      <li>
  
        <span>业务规则</span>
  
        <span>{{data2.businessrule}}</span>
  
      </li>
  
    </ul>
  
  </div>
</template>

<script>
  import $ from 'jquery'
  
  export default {
  
    name: 'BasicInformation',
  
    data() {
  
      return {
  
        data2: [],
  
      }
  
    },
  
    mounted() {
  
      var _this = this;
  
      console.log(this.$route.query.data)
  
      $.ajax({
  
        url: `${this.Root}datagovern/contentbaseinfo/findBusAttr`,
  
        dataType: "json",
  
        method: 'POST',
  
        data: {
  
          "maintenanceid": this.$route.query.data.id
  
        },
  
        success: function(data) {
  
          console.log(data);
  
          _this.data2 = data.data ? data.data : {
  
            "dataentityname": "--",
  
            "dataattributename": "--",
  
            "businessdefinition": "--",
  
            "businessrule": "--"
  
          }
  
  
  
        }
  
      })
  
  
  
    },
  
    computed: {
  
  
  
    },
  
    watch: {
  
  
  
    },
  
    methods: {
  
  
  
    }
  
  }
</script>

<style scoped>
  #BasicInformation {
  
    width: 100%;
  
    height: 100%;
  
    box-sizing: border-box
  
  }
  
  
  
  #BasicInformation ul {
  
    width: 100%;
  
    height: 100%;
  
    background: #fff;
  
    box-sizing: border-box;
  
    border: solid 1px #E3E7F1;
  
  }
  
  
  
  #BasicInformation ul li {
  
    display: flex;
  
    justify-content: space-between;
  
    align-items: center;
  
    line-height: 34px;
  
    border-bottom: solid 1px #E3E7F1;
  
  }
  
  
  
  #BasicInformation ul li:last-child {
  
    border: 0;
  
  }
  
  
  
  #BasicInformation ul li span {
  
    color: #778199;
  
    font-size: 14px;
  
  }
  
  
  
  #BasicInformation ul li span:first-child {
  
    width: 220px;
  
    padding-left: 20px;
  
    box-sizing: border-box
  
  }
  
  
  
  #BasicInformation ul li span:last-child {
  
    flex: 1;
  
  }
  
  
  
  #BasicInformation ul li:nth-child(2n) {
  
    background: #FCFCFC;
  
  }
</style>

<template>
  <div style="min-height: 842px;">
    <section class="personInfo">
      <div>
        <span>{{name}}</span>
        <p>{{descript}}</p>
        <div class="infoList">
          <span v-for="(item,index) in infoList">{{item}}</span>
        </div>
      </div>
      <img src="../assets/nn.jpg">
    </section>
    <section class="personCtn">
      <ul class="ulWrap">
        <li>
          <p><i class="fa fa-bookmark-o"></i>求职意向</p>
          <div class="content jobIntention">
            <span><i class="fa fa-bank"></i>{{jobIntention.job}}</span>
            <span><i class="fa fa-map-marker"></i>{{jobIntention.location}}</span>
            <span><i class="fa fa-jpy"></i>{{jobIntention.salary}}</span>
            <span><i class="fa fa-undo"></i>{{jobIntention.worktime}}</span>
          </div>
        </li>
        <li>
          <p><i class="fa fa-bookmark-o"></i>教育背景</p>
          <div class="content generalStyle">
           <p>
             <span>{{educationBg.startTime}}——{{educationBg.endTime}}</span>
             <span>{{educationBg.school}}</span>
             <span>{{educationBg.major}}</span>
           </p>
           <p v-show="educationBg.info">{{educationBg.info}}</p>
          </div>
        </li>
        <li>
          <p><i class="fa fa-bookmark-o"></i>技能特长</p>
          <div class="content" style="display: flex;flex-wrap: wrap;">
            <div class="svgInfo" v-for="(item,index) in skills">
              <svg width="70" height="70" viewbox="0 0 70 70">
                  <circle cx="35" cy="35" r="30" stroke-width="5" stroke="#EBF0FA" fill="none" stroke-linecap="round" :stroke-dasharray="2*3.14*30*0.75"></circle>
                <circle cx="35" cy="35" r="30" stroke-width="5" fill="none" stroke-linecap="round" stroke="#a6cffe" :stroke-dasharray="2*3.14*30*0.75*Number(item.rate)+' 503'" style="transition: all 3s ease;"></circle>
              </svg>
              <span>{{item.rate*100}}%</span>
              <span>{{item.name}}</span>
            </div>
          </div>
        </li>
        <li>
          <p><i class="fa fa-bookmark-o"></i>工作经验</p>
          <div class="content generalStyle">
             <p>
               <span>{{workExperience.startTime}}——{{workExperience.endTime}}</span>
               <span>{{workExperience.company}}</span>
               <span>{{workExperience.job}}</span>
             </p>
             <p v-html='workExperience.info'></p>
           </div>
        </li>
        <li v-show="honoraryAward!=''">
          <p><i class="fa fa-bookmark-o"></i>荣誉奖项</p>
          <div class="content">{{honoraryAward}}</div>
        </li>
        <li>
          <p><i class="fa fa-bookmark-o"></i>自我评价</p>
          <div class="content">{{selfAssessment}}</div>
        </li>
      </ul>
    </section>
  </div>
</template>

<script>
export default {
  name: 'personal',
  data () {
    return {
      name: '刘宁',
      descript: '恪尽职守,做最好的自己',
      infoList: ['女', '24岁', '汉','本科','三年'],//性别 年龄 民族 学历 工作年限 电话 邮箱
      jobIntention: {'job':'前端开发','location':'陕西西安','salary':'1K','worktime':'到岗时间另议'},//求职意向
      educationBg: {'startTime': '2013.9', 'endTime': '2017.7', 'school': '西安邮电大学', 'major':'软件工程', 'info':'一堆描述...'},//教育背景
      workExperience: {'startTime': '2016.11', 'endTime': '至今', 'company': '赞同科技股份有限公司', 'job':'web前端开发工程师', 'info':'配套监控项目主要用来监控系统运行的异常以及系统信息的采集统计等。<br>\
项目主要功能：afa实例监控、性能监控、业务流水推送、流水查询、功能预警、实例管理等。<br>\
责任描述：采用css3+html5实现页面布局，ajax+jquery实现数据实时显示。'},//工作经验
      skills: [{'name': 'HTML', 'rate': 0.5}, {'name': 'CSS', 'rate': 0.8}, {'name': 'CSS', 'rate': 0.8}, {'name': 'CSS', 'rate': 0.8}, {'name': 'CSS', 'rate': 0.8}, {'name': 'CSS', 'rate': 0.8}, {'name': 'CSS', 'rate': 0.8}, {'name': 'CSS', 'rate': 0.8}],//技能特长
      honoraryAward: '一堆描述...',//荣誉奖项
      selfAssessment: '善于沟通，有很强的适应能力，乐观积极有责任心，具有较强的学习能力，能独立思考问题解决问题！喜欢钻研学习新知识新技能，提高专业技能水平。',//自我评价
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.personInfo{
  display: flex;
  justify-content: space-between;
  padding: 30px 30px 40px;
  font-size: 12px;
  color: #757575;
  border-bottom: 1px dashed #989898;
}
.personInfo>div{
  max-width: 400px;
}
.personInfo>div>span{
  font-size: 20px;
}
.personInfo>div>p{
  margin-bottom: 60px;
}
.personInfo img{
  width: 90px;
  height: 110px;
}
.personInfo .infoList{
  display: flex;
  flex-wrap: wrap;
}
.personInfo .infoList span{
  padding: 0 8px;
  height: 12px;
  line-height: 12px;
  margin-bottom: 5px;
}
.personInfo .infoList span+span{
  border-left: 1px solid #757575;
}
.personCtn{
  padding: 25px 30px 30px;
}
.ulWrap{
  background:linear-gradient(to bottom,#579af7,#579af7);
  background-size: 1px 100%;
  background-repeat: repeat-y;
  background-position: 9px 0;
  margin:0;
  padding: 0;
}
.ulWrap li{
  min-height: 100px;
  position: relative;
  padding: 0 10px 0 20px;
  list-style: none;
  font-size: 12px;
  color: #757575;
  overflow: hidden;
}
.ulWrap li:before{
  content:"";
  width: 20px;
  height: 20px;
  border-radius: 50%;
  background-color: #579af7;
  display: block;
  position: absolute;
  left: 0;
  top: 0;
}
.ulWrap li>p{
  font-size: 14px;
  color: #579af7;
  margin: 0 0 0 10px;
}
.ulWrap li>p i{
  font-size: 12px;
  color: #fff;
  position: absolute;
  transform: translate(-25px, 5px);
}
.ulWrap li>div.content{
  margin: 20px 0 40px 10px;
  box-sizing: border-box;
}
.jobIntention{
  display: flex;
  justify-content: space-between;
}
.jobIntention span{
  display: flex;
  align-items: center;
  margin-right: 8px;
}
.jobIntention span i{
  margin-right:8px;
  font-size: 10px;
  text-align: center;
  line-height: 12px;
}
.jobIntention span i:before{
  width: 12px;
  height: 12px;
  border-radius: 50%;
  display: block;
  border:1px solid #757575;
}
.generalStyle p:first-child{
  display: flex;
  justify-content: space-between;
}
circle {
    transform-origin: center;
    transform:rotate(135deg);
}
.svgInfo{
  position: relative;
  text-align: center;
  width: 70px;
  height: 80px;
  margin-right: 10px;
}
.svgInfo span:nth-child(2){
    position: absolute;
    bottom: 50%;
    left: 50%;
    transform: translateX(-50%);
}
.svgInfo span:nth-child(3){
  width: 100%;
  position: absolute;
  top: 60px;
  left: 0;
}
</style>

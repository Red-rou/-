<template>
    <div class="jianzhi">
        <div class="sou">
            <div class="di">
                <div @click="chulai">
                    <span>{{$t("jianzhi.place")}}</span>
                    <img src="../assets/img/la.png" alt="">
                </div>
                <div>
                    <input type="text" placeholder="请输入关键字搜索">
                    <img src="../assets/img/sou.png" alt="">
                </div>
            </div>
            <div class="yin" v-show='chu'>
                <ul>
                    <li v-for='(d,index) in di' :key='index'>
                        <a>{{di[index]}}</a>
                    </li>
                </ul>
            </div>
            <hr>
            <div class="ul">
                <ul>
                    <li>雇主保障 :</li>
                    <li>全部</li>
                    <li v-for='(z,index) in zhu' :key=index>
                        <a>{{zhu[index]}}</a>
                    </li>
                </ul>
                 <ul>
                    <li>兼职角色 :</li>
                    <li>全部</li>
                    <li v-for='(j,index) in jianzhi' :key=index>
                        <a>{{jianzhi[index]}}</a>
                    </li>
                </ul>
            </div>
            <button>{{$t("home.registration")}}</button>
            <button>{{$t("home.release")}}</button>  
        </div>
        <div class="jiazai" v-for='(m,index) in msg' :key='index'>
            <div class="left">
                <img :src=msg[index].imgAddr alt="">
                <p>{{msg[index].category}}</p>
            </div>
            <div class="content">
                <h3>{{msg[index].title}}</h3>
                <p>
                    <span>技术经验：</span>
                    {{msg[index].jiShu}}
                </p>
                <p>
                    <span>项目经验:</span>
                     {{msg[index].xiangMu}}
                </p>
            </div>
            <div class="gang"></div>
            <div class="right">
                <p>
                    <span>{{msg[index].price}}</span>元/8小时
                </p>
                <p>
                    {{msg[index].phoneNum}}
                    <img src="../assets/img/web-off.gif" alt="">
                </p>
                <p>
                    可兼职时间：
                    <span v-for='(t,i) in msg[index].time' :key=i>
                        {{msg[index].time[i]}}、
                    </span>
                </p>
                <p>可兼职地点：<span>{{msg[index].address}}</span></p>
                <div class="btn">
                    <button>立即预约</button>
                    <button>关注</button>
                </div>
                
            </div>

        </div>







    </div>
</template>
<script>
export default {
    name:'Jianzhi',
    data() {
        return {
            di:[
                '全部','北京','上海','天津','重庆','河北','山西','内蒙古',
                '辽宁','吉林','黑龙江','江苏','浙江','安徽','福建','江西','山东',
                '河南','湖北','湖南','广东','广西','海南','四川','贵州','云南',
                '西藏','陕西','甘肃','青海','宁夏','新疆','台湾','香港','澳门'
            ],
            zhu:[
                '1小时不满意退款','保证完成','保证原创','保证维护',
                '提供源码','保证推广效果'
            ],
            jianzhi:[
                '移动开发','后端开发','前端开发','运维人员','DBA',
                '视觉设计','交互设计','产品经理','运营人员','测试人员','其他','产品设计师',
                '市场/营销'
            ],
            
            chu:false,
            msg:[]
        }
    },
    created(){
        ajax('get',{"flag":'list'},resURL,(err,res)=>{
        if(null != err){
            console.log(err)
            return
        }
        this.msg = res
        // console.log(res)
        })
    },
    methods: {
        chulai(){
            this.chu = !this.chu
        },
        
    },
}
</script>
<style scoped>
    .jianzhi{
        background:#ebeced;
        padding: 100px ;
    }
    a{
        text-decoration: none;
        color: #536892;
        font-size: 14px;
    }
    a:hover{
        color: orange;
    }
    li{
        padding: 0 10px;
    }
    .sou,.jiazai{
        border: 1px solid white;
        background: white;
        width: 1200px;
        border-radius: 10px;
        padding: 20px;
        margin-bottom: 20px;
    }
    .sou .di{
        height: 50px;
    }
    .sou .di div:nth-child(1){
        float: left;
        position: relative;
    }
    .sou .di input{
        width: 40%;
        float: right;
        margin-right: 20px;
        height:36px;
        border: 1px solid #536892;
        border-radius: 18px;
        padding-left:12px;
        /* 去输入框的亮框 */
        outline: medium none ;
        background:#e6eaed;
    }
    .sou .di input:focus{
        width: 45%;
        border-radius: 18px;
    }
     .sou .di div:nth-child(2){
           position: relative;
     }
    .sou .di div:nth-child(2) img{
        position: absolute;
        right: 36px;
        top:10px;
    }
    .sou .di span,.sou .ul li:nth-child(1),.jiazai .content span{
        color: #000;
    }
    .sou .di span{
        font-size: 25px;
    }
    .sou .yin{
        width: 500px;
        border: 1px solid #536892;
        border-radius: 5px;
        box-shadow: 0 0 5px 0.5px #536892;
        position: absolute;
        top:200px;
        background:white;
    }
    .sou .ul{
        text-align: left;
        padding:20px;
    }
    .sou .ul ul{
        padding: 0;
    }
    .sou .ul li:nth-child(2){
        color: orange;
        font-size: 14px;
    }
    .sou button{
         color: white;
        font-size: 14px;
        margin: 0 20px;
        padding: 5px 10px;
        border-radius: 5px;
    }
    .sou button:nth-child(5){
        background: #49afcd;
    }
     .sou button:nth-child(6){
        background: #5bb75b;
    }
    .jiazai{
        height: 300px;
        padding: 60px;
    }
    .jiazai>div{
        float: left;
    }
    .jiazai .left,.content,.right,.gang{
        margin: 20px;
    }
    .jiazai .left img{
        border-radius: 80px;
    }
    .jiazai .left p{
        background: red;
        color: white;
        border-radius: 5px;
        margin-top: 20px;
    }
    .jiazai .content{
        width: 50%;
        text-align: left;
    }
    .jiazai .content h3{
        color: #049fbb;
        margin-bottom: 20px;
    }
    .jiazai .content p{
        font-size: 14px;
        margin-top: 10px;
    }
    .jiazai .content span{
        font-size: 16px;
    }
    .jiazai .gang{
        height: 150px;
        border: 0.5px solid gray;
    }
    .jiazai .right{
        width: 23%;
        text-align: left;
    }
    .jiazai .right p{
       margin-bottom: 10px;
        color: #333;
    }
    .jiazai .right p:nth-child(1){
        color: red;
        margin-bottom: 20px;
    }
    .jiazai .right p:nth-child(1) span{
        font-size: 24px;
    }
    .jiazai .right p:nth-child(2){
        color: #08c;
        font-weight: bold;
        font-size: 16px;
    }
     .jiazai .right button{
        float: right;
        font-size: 14px;
        padding: 2px 5px;
        margin: 10px 10px 10px 0;
        border-radius: 5px;
    }
    .jiazai .right .btn button:last-child {
        background-color:  #f5f5f5;
        color: #787878;
    }
     .jiazai .right .btn button:nth-child(1){
       background-color:red; 
     color: #ffffff;
    }
    
</style>

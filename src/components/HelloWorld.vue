<style>
#works>ul{display: flex}
#works>ul>li{width: 160px;margin-right: 10px;cursor: pointer;}
#works>ul>li>.video{width: 160px;height: 90px;background-size: 100%;background-position: 50%}
#works>ul>li>.dialog>img{display: none}
#works>ul>li>.dialog{
  width: 160px;height: 90px;
  background-color: rgba(0, 0, 0, 0);
  position: absolute;top: 0;
  display: flex;
  justify-content: center;
  align-items: center
}
#works>ul>li:hover>.video{background-size: 120%}
#works>ul>li:hover>.dialog{background-color: rgba(0, 0, 0, 0.3)}
#works>ul>li:hover>.dialog>img{display: block}
.el-dialog video{margin-left: 50%;transform: translateX(-50%)}
</style>

<template>
  <div id="works">
    <ul>
      <li @click="play(msg)" v-for="(msg,index) of msgs" :key="index">
        <div class="video" :style="{'background-image':'url(http://101.132.46.146:8080/elfinder/files/zhangtao25/pc/test.jpg)'}">
        </div>
        <div style="padding:5px;background-color:#f8f8f8;width:150px">
          <p>{{msg.work_name}}</p>
          <p style="color:#999">{{msg.des}}</p>
        </div>
        <div class="dialog">
          <img style="width:32px;height:32px" src="http://101.132.46.146:8080/elfinder/files/zhangtao25/zhizhi/压缩后/播放.png" alt="">
        </div>
      </li>
    </ul>
    <el-dialog
      title="视频"
      :visible.sync="dialogVisible"
      width="70%"
      :before-close="handleClose">
      <video ref="video" :src="work_url" controls="controls"></video>
    </el-dialog>
  </div>
</template>
<script>
export default {
  data(){
    return{
      msgs:[
        {work_name:'陈敏坤1.30',des:'描述性文字',work_url:'http://101.132.46.146:8080/elfinder/files/zhangtao25/zhizhi/压缩后/陈敏坤1.30.mp4'},
        {work_name:'老有所伴',des:'描述性文字',work_url:'http://101.132.46.146:8080/elfinder/files/zhangtao25/zhizhi/压缩后/老有所伴.mp4'},
        {work_name:'灵芝宣传片',des:'描述性文字',work_url:'http://101.132.46.146:8080/elfinder/files/zhangtao25/zhizhi/压缩后/灵芝宣传片.mp4'},
        {work_name:'杨春1.29字幕',des:'描述性文字',work_url:'http://101.132.46.146:8080/elfinder/files/zhangtao25/zhizhi/压缩后/杨春1.29字幕.mp4'},
        {work_name:'音乐会倒计时3',des:'描述性文字',work_url:'http://101.132.46.146:8080/elfinder/files/zhangtao25/zhizhi/压缩后/音乐会倒计时3.mp4'},
        {work_name:'张岩1.29字幕',des:'描述性文字',work_url:'http://101.132.46.146:8080/elfinder/files/zhangtao25/zhizhi/压缩后/张岩1.29字幕.mp4'},
        {work_name:'足迹-淮南）',des:'描述性文字',work_url:'http://101.132.46.146:8080/elfinder/files/zhangtao25/zhizhi/压缩后/足迹-淮南）.mp4'},
        {work_name:'MG动画宣传片',des:'描述性文字',work_url:'http://101.132.46.146:8080/elfinder/files/zhangtao25/zhizhi/压缩后/MG动画宣传片.mp4'}
      ],
      work_url:'',
      dialogVisible: false
    }
  },
  methods: {
    handleClose(done) {
      this.$confirm('确认关闭？')
        .then(_ => {
          done();
          this.$refs.video.pause()
        })
        .catch(_ => {});
    },
    play(val) {
      this.$prompt('请输入张涛是帅哥', '提示', {
        confirmButtonText: '确定',
        cancelButtonText: '取消',
        inputPattern: /张涛是帅哥/,
        inputErrorMessage: '快点个~'
      }).then(({ value }) => {
        this.work_url = val.work_url
        this.dialogVisible = true
      }).catch(() => {
        this.$message({
          type: 'info',
          message: '快点输，小学森！'
        });       
      });
    }
  }
}
</script>
<template>
    <div id="show-menu">
        <div class="menu-cont">
            <div class="logo"><a target="_blank" href="https://github.com/yanzhang-sheridan"><i class="icon-github icon-5x"></i></a></div>
            <div class="file" @click="fileClick">
                <i class=" icon-file-alt icon-5x"></i>
                <p class="file-des">Generate Resume</p>
            </div>
            <div class="download-file" @click="downloadClick">
                <i class=" icon-download-alt icon-5x"></i>
            </div>
            <transition name="fade">
            <div class="download-choice" v-show="showDownloadChoice">
                <div class="dpi96 setdpi">
                    <p>96 pixels/inch</p>
                    <p>A4 794×1123</p>
                    <input type="radio" @click="choiceClick({'width':794,'height':1123})">
                </div>
                <div class="dpi120 setdpi">
                    <p>120 pixels/inch</p>
                    <p>A4 1487×2105</p>
                    <input type="radio" @click="choiceClick({'width':1487,'height':2015})">
                </div>
                <div class="custom">
                    width :<input type="text" v-model="customPx.width"  placeholder="px">
                    height:<input type="text" v-model="customPx.height"  placeholder="px">
                    <span class="ok-choice" @click="choiceClick({'width':parseInt(customPx.width),'height':parseInt(customPx.height)})">download</span>
                </div>
            </div>
            </transition>
        </div>
    </div>
</template>

<script type="text/ecmascript-6">
    export default{
        data(){
            return {
                msg: 'hello vue',
                showDownloadChoice:false,
                customPx:{
                    width:"",
                    height:""
                }
            }
        },
        created(){

        },
        methods: {
            fileClick: function () {
                this.$emit('listenShowMenu', {"type": "fileClick", "showFlag": true});
            },
            downloadClick: function () {
                this.showDownloadChoice = !this.showDownloadChoice;
            },
            choiceClick: function (size) {
                if(size.width && size.height){
                    this.$emit('listenShowMenu', {"type": "choiceClick","size":size});
                    this.showDownloadChoice = !this.showDownloadChoice;
                }
            }
        },
        components: {}
    }
</script>

<style>
    #show-menu {
        float: left;
        width: 8%;
        height: 100%;
        background: #ffffff;
    }
    .menu-cont {
        position: relative;
        width: 90%;
        height: 99%;
        margin: 0 auto;
        padding-top: 1rem;
        box-sizing: border-box;
        box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
    }
    .logo, .file, .download-file {
        width: 100%;
        color: #42b983;
        text-align: center;
        font-size: 1.2rem;
        margin-bottom: 2rem;
    }
    .logo a{
        color: #42b983;
    }
    .file .file-des {
        font-size: 1.6rem;
    }
    .download-file {
        position: absolute;
        bottom: 2rem;
    }
    .logo, .file, .download-file:hover {
        cursor: pointer;
    }
    .download-choice {
        position: absolute;
        z-index: 9999;
        bottom: 3.5rem;
        left: 110%;
        width: 35rem;
        text-align: center;
        background: #ffffff;
        box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
    }
    .setdpi{
        display: inline-block;
        padding: 1rem;
        font-size: 1.6rem;
        color: #3ca777;
    }
    .custom{
        display: inline-block;
        width: 10rem;
        font-size: 1.6rem;
        color: #3ca777;
    }
    .custom input{
        width: 5rem;
        text-align: right;
    }
    .ok-choice{
        display: inline-block;
        text-align: center;
        border: 1px solid #4cd195;
        border-radius: 6px;
        padding: 1px 8px;
        box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
    }
    .ok-choice:hover{
        box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0);
        cursor: pointer;
    }
</style>

<template>
    <div id="show-resume">
        <div id="resume_content" class="resume-content clearfloat" :style="{width:pfdSize.width+'px',height:pfdSize.height+'px'}">
            <section class="section-left">
                <div class="head">
                    <h2>{{resumeData.head.name}}</h2>
                    <h3>Job Title:{{resumeData.head.intention}}</h3>
                    <p><i class="icon-phone icon-2x"></i></p>
                    <p>{{resumeData.head.tel}}</p>
                    <p><i class="icon-envelope-alt icon-2x"></i></p>
                    <p>{{resumeData.head.email}}</p>
                    <ul class="clearfloat">
                        <li>
                            <p>Address</p>
                            <p>{{resumeData.head.address}}</p>
                        </li>
                       
                    </ul>
                </div>
                <div class="edu">
                    <h3><span class="item-title">Education</span></h3>
                    <p>{{resumeData.head.school}} ({{resumeData.head.graduation}})</p>
                    <p>{{resumeData.head.graduationTime}}</p>
                    <p>Program:{{resumeData.head.major}}</p>
                    <p class="honor-title">Honour</p>
                    <p v-for="item in resumeData.head.honor.split('.')">{{item}}</p>
                </div>
                <div class="interest">
                    <h3><span class="item-title">Hobbies</span></h3>
                    <p><span class="inte-span" v-for="item in resumeData.head.interest.split('.')">{{item}}</span></p>
                </div>
                <div class="skill">
                    <h3><span class="item-title">Skills</span></h3>
                    <div class="sk" v-for="(item,index) in resumeData.head.speciality.split('.')">{{item}}
                        <div class="sk-wrap">
                            <span class="sk-per" :style="{width:resumeData.head.specialityPer.split('.')[index]+'%'}"></span>
                        </div>
                    </div>
                </div>
            </section>
            <section class="section-right">
                <div class="blog-box clearfloat">
                    <div class="blog">
                        <div class="title-name">LINKS</div>
                        <div class="link github"><i class="icon-github-alt icon-1x"></i>Github: <a target="_blank" href="https://github.com/yanzhang-sheridan">{{resumeData.blogLink.github}}</a></div>
                        <div class="link personal-blog"><i class="icon-flag icon-1x"></i>Portfolio <a target="_blank" href="https://yanzhang@nofinsports.com">{{resumeData.blogLink.blog}}</a></div>
                    </div>
                </div>
                <div class="experience work-experience">
                    <div class="title">
                        <div class="title-name">Experience</div>
                        <div class="title-date">{{resumeData.workExperience.time}}</div>
                    </div>
                    <div class="show" v-for="item in resumeData.workExperience.experience">
                        <div class="item"  v-if="item.name" >
                            <div class="item-title">
                                <span class="item-name">{{item.name}}</span>
                                <span class="item-skill">/ {{item.skill}}</span>
                                <span class="item-date">{{item.time}}</span>
                            </div>
                            <ul>
                                <li v-for="des in item.describe">{{des}}</li>
                            </ul>
                        </div>
                    </div>
                </div>
                <div class="experience project-experience">
                    <div class="title">
                        <div class="title-name">Projects</div>
                        <div class="title-date">{{resumeData.projectExperience.time}}</div>
                    </div>
                    <div class="show" v-for="item in resumeData.projectExperience.experience">
                        <div class="item" v-if="item.name">
                            <div class="item-title">
                                <span class="item-name">{{item.name}}</span>
                                <span class="item-skill">/ {{item.skill}}</span>
                                <span class="item-date">{{item.time}}</span>
                            </div>
                            <ul>
                                <li v-for="des in item.describe" v-if="des!=''">{{des}}</li>
                            </ul>
                        </div>
                    </div>
                </div>
                <div class="experience skill-experience">
                    <div class="title">
                        <div class="title-name">Skills</div>
                    </div>
                    <div class="show" v-for="item in resumeData.skill">
                        <div class="item"  v-if="item.type">
                            <div class="item-title">
                                <span class="item-name">{{item.type}}</span>
                            </div>
                            <ul>
                                <li v-for="des in item.describe">{{des}}</li>
                            </ul>
                        </div>
                    </div>
                </div>
                <div class="experience self-evaluation">
                    <div class="title">
                        <div class="title-name">Self Assessment</div>
                    </div>
                    <p class="eval-detail" v-for="item in resumeData.selfAssessment">{{item}}</p>
                </div>
            </section>
        </div>
        <div v-html="resStyleCode"></div>
    </div>
</template>

<script type="text/ecmascript-6">
    export default{
        data(){
            return{
                msg:'hello vue',
                ttc:80,
                resStyleCode:"",
                pfdSize:{
                    width:"",
                    height:""
                }
            }
        },
        props:{
            resumeData:{
                type:Object
            }
        },
        methods:{
            responseStyleCode: function (code) {
                this.resStyleCode = "<style>"+code+"</style>"
            }
        },
        components:{

        }
    }
</script>

<style>
    #show-resume{
        float: left;
        width: 67%;
        height: 100%;
        background: #ffffff;
        padding: 1rem 2rem;
        overflow: auto;
        box-sizing: border-box;
    }
    .resume-content{
        width: 100%;
        height: 99%;
        box-shadow: 0 4px 12px 0 rgba(0,0,0,0.5);
        overflow: auto;
        background: rgb(249,249,249);
    }
    .resume-content::-webkit-scrollbar {
         display: none;
     }
</style>

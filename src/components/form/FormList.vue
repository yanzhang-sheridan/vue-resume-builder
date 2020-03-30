<template>
    <div id="from_box">
        <div class="from-content">
            <div class="from-content-item">
                <div class="item">
                    <div class="item-head">ABOUT ME</div>
                    <div class="item-content clearfloat">
                        <div class="inp-short">Name:<input type="text" v-model="fromData.head.name"></div>
                        <div class="inp-short">Job Title<input type="text" v-model="fromData.head.intention"></div>
                        <div class="inp-short">Email<input type="text" v-model="fromData.head.email"></div>
                        <div class="inp-short">Phone<input type="text" v-model="fromData.head.tel"></div>
                        <div class="inp-short">Address<input type="text" v-model="fromData.head.address"></div>
                        <!-- <div class="inp-short">性别:<input type="text" v-model="fromData.head.sex"></div>
                        <div class="inp-short">年龄:<input type="text" v-model="fromData.head.age" placeholder="1770.8.23"></div> -->
                        <div class="inp-short">School:<input type="text" v-model="fromData.head.school"></div>
                        <div class="inp-short">Degree:<input type="text" v-model="fromData.head.graduation"></div>
                        <div class="inp-short">Period:<input type="text" v-model="fromData.head.graduationTime" placeholder="2012-9 to 2016-7"></div>
                        <div class="inp-short">Program:<input type="text" v-model="fromData.head.major" placeholder=""></div>
                        <div class="inp-short">Hornour:<input type="text" v-model="fromData.head.honor" placeholder="seperate by ,"></div>
                        <div class="inp-short">Skills:<input type="text" v-model="fromData.head.speciality" placeholder="seperated by ,"></div>
                        <div class="inp-short">Skill Abilities:<input type="text" v-model="fromData.head.specialityPer" placeholder="seperate by ,"></div>
                        <div class="inp-short">Hobbies:<input type="text" v-model="fromData.head.interest" placeholder="seperate by ,"></div>
                    </div>
                    <div class="item-footer"><i></i>&nbsp;&nbsp;&nbsp;</div>
                </div>
                <div class="item">
                    <div class="item-head">LINKS</div>
                    <div class="item-content">
                        <div class="inp-long">GitHub:<input type="text" placeholder="optional" v-model="fromData.blogLink.github"></div>
                        <div class="inp-long">Website:<input type="text" placeholder="optional" v-model="fromData.blogLink.blog"></div>
                    </div>
                    <div class="item-footer"><i></i>&nbsp;&nbsp;&nbsp;</div>
                </div>
                <div class="item">
                    <div class="item-head">
                        <span>EXPERIENCE</span>
                        <span class="item-head-time">:<input type="text" placeholder="2001-2 to Present" v-model="fromData.workExperience.time"></span>
                    </div>
                    <div class="item-content" v-if="workExperienceFlag>=0">
                        <div class="contt clearfloat">
                            <div class="inp-short">Company:<input type="text" placeholder="" v-model="fromData.workExperience.experience[0].name"></div>
                            <div class="inp-short">Job Title:<input type="text" placeholder="" v-model="fromData.workExperience.experience[0].skill"></div>
                            <div class="inp-short">Period:<input type="text" placeholder="2001-2 to Present" v-model="fromData.workExperience.experience[0].time"></div>
                        </div>
                        <div class="inp-long inp-long-more">Responsibilities:
                            <input type="text" placeholder="1." v-model="fromData.workExperience.experience[0].describe[0]" >
                            <input type="text" placeholder="2." v-model="fromData.workExperience.experience[0].describe[1]">
                            <input type="text" placeholder="3." v-model="fromData.workExperience.experience[0].describe[2]">
                        </div>
                    </div>
                    <div class="item-content" v-if="workExperienceFlag>=1">
                        <div class="contt clearfloat">
                            <div class="inp-short">Company:<input type="text" placeholder="" v-model="fromData.workExperience.experience[0].name"></div>
                            <div class="inp-short">Job Title:<input type="text" placeholder="" v-model="fromData.workExperience.experience[0].skill"></div>
                            <div class="inp-short">Period:<input type="text" placeholder="2001-2 xxxx-x" v-model="fromData.workExperience.experience[0].time"></div>
                        </div>
                        <div class="inp-long inp-long-more">Responsibilities:
                            <input type="text" placeholder="1." v-model="fromData.workExperience.experience[0].describe[0]" >
                            <input type="text" placeholder="2." v-model="fromData.workExperience.experience[0].describe[1]">
                            <input type="text" placeholder="3." v-model="fromData.workExperience.experience[0].describe[2]">
                        </div>
                    </div>
                      <div class="item-content" v-if="workExperienceFlag>=2">
                        <div class="contt clearfloat">
                            <div class="inp-short">Company:<input type="text" placeholder="" v-model="fromData.workExperience.experience[0].name"></div>
                            <div class="inp-short">Job Title:<input type="text" placeholder="" v-model="fromData.workExperience.experience[0].skill"></div>
                            <div class="inp-short">Period:<input type="text" placeholder="2001-2 xxxx-x" v-model="fromData.workExperience.experience[0].time"></div>
                        </div>
                        <div class="inp-long inp-long-more">Responsibilities:
                            <input type="text" placeholder="1." v-model="fromData.workExperience.experience[0].describe[0]" >
                            <input type="text" placeholder="2." v-model="fromData.workExperience.experience[0].describe[1]">
                            <input type="text" placeholder="3." v-model="fromData.workExperience.experience[0].describe[2]">
                        </div>
                    </div>
                    <div class="item-footer"><i class=" icon-plus-sign-alt icon-1x" @click="workIconClick" v-show="workExperienceFlag<2"></i>&nbsp;&nbsp;&nbsp;</div>
                </div>
                <div class="item">
                    <div class="item-head">
                        <span>Projects</span>
                        <span class="item-head-time">Period:<input type="text" placeholder="2001-2 Present" v-model="fromData.projectExperience.time"></span>
                    </div>
                    <div class="item-content" v-if="projectExperienceFlag>=0">
                        <div class="contt clearfloat">
                            <div class="inp-short">Project Name:<input type="text" placeholder="" v-model="fromData.projectExperience.experience[0].name"></div>
                            <div class="inp-short">Skills:<input type="text" placeholder="" v-model="fromData.projectExperience.experience[0].skill"></div>
                            <div class="inp-short">Project Time:<input type="text" placeholder="2001-2 to Present" v-model="fromData.projectExperience.experience[0].time"></div>
                        </div>
                        <div class="inp-long inp-long-more">Description:
                            <input type="text" placeholder="1." v-model="fromData.projectExperience.experience[0].describe[0]">
                            <input type="text" placeholder="2." v-model="fromData.projectExperience.experience[0].describe[1]">
                            <input type="text" placeholder="3." v-model="fromData.projectExperience.experience[0].describe[2]">
                        </div>
                    </div>
                    <div class="item-content" v-if="projectExperienceFlag>=1">
                        <div class="contt clearfloat">
                            <div class="inp-short">Project Name:<input type="text" placeholder="" v-model="fromData.projectExperience.experience[0].name"></div>
                            <div class="inp-short">Skills:<input type="text" placeholder="" v-model="fromData.projectExperience.experience[0].skill"></div>
                            <div class="inp-short">Project Time:<input type="text" placeholder="2001-2 to Present" v-model="fromData.projectExperience.experience[0].time"></div>
                        </div>
                        <div class="inp-long inp-long-more">Description:
                            <input type="text" placeholder="1." v-model="fromData.projectExperience.experience[0].describe[0]">
                            <input type="text" placeholder="2." v-model="fromData.projectExperience.experience[0].describe[1]">
                            <input type="text" placeholder="3." v-model="fromData.projectExperience.experience[0].describe[2]">
                        </div>
                    </div>
                    <div class="item-content" v-if="projectExperienceFlag>=2">
                        <div class="contt clearfloat">
                            <div class="inp-short">Project Name:<input type="text" placeholder="" v-model="fromData.projectExperience.experience[0].name"></div>
                            <div class="inp-short">Skills:<input type="text" placeholder="" v-model="fromData.projectExperience.experience[0].skill"></div>
                            <div class="inp-short">Time:<input type="text" placeholder="2001-2 to Present" v-model="fromData.projectExperience.experience[0].time"></div>
                        </div>
                        <div class="inp-long inp-long-more">Description:
                            <input type="text" placeholder="1." v-model="fromData.projectExperience.experience[0].describe[0]">
                            <input type="text" placeholder="2." v-model="fromData.projectExperience.experience[0].describe[1]">
                            <input type="text" placeholder="3." v-model="fromData.projectExperience.experience[0].describe[2]">
                        </div>
                    </div>
                    <div class="item-footer"><i class=" icon-plus-sign-alt icon-1x" @click="pojIconClick" v-show="projectExperienceFlag<2"></i>&nbsp;&nbsp;&nbsp;</div>
                </div>

                <div class="item">
                    <div class="item-head">Skill Sets</div>
                    <div class="item-content" v-if="skillFlag>=0">
                        <div class="contt clearfloat">
                            <div class="inp-short">Categories:<input type="text" placeholder="" v-model="fromData.skill[0].type"></div>
                        </div>
                        <div class="inp-long inp-long-more">Details:
                            <input type="text" placeholder="1." v-model="fromData.skill[0].describe[0]">
                            <input type="text" placeholder="2." v-model="fromData.skill[0].describe[1]">
                            <input type="text" placeholder="3." v-model="fromData.skill[0].describe[2]">
                        </div>
                    </div>
                    <div class="item-content" v-if="skillFlag>=1">
                        <div class="contt clearfloat">
                            <div class="inp-short">Categories:<input type="text" placeholder="" v-model="fromData.skill[0].type"></div>
                        </div>
                        <div class="inp-long inp-long-more">Details:
                            <input type="text" placeholder="1." v-model="fromData.skill[0].describe[0]">
                            <input type="text" placeholder="2." v-model="fromData.skill[0].describe[1]">
                            <input type="text" placeholder="3." v-model="fromData.skill[0].describe[2]">
                        </div>
                    </div>
                    <div class="item-content" v-if="skillFlag>=2">
                        <div class="contt clearfloat">
                            <div class="inp-short">Categories:<input type="text" placeholder="" v-model="fromData.skill[0].type"></div>
                        </div>
                        <div class="inp-long inp-long-more">Details:
                            <input type="text" placeholder="1." v-model="fromData.skill[0].describe[0]">
                            <input type="text" placeholder="2." v-model="fromData.skill[0].describe[1]">
                            <input type="text" placeholder="3." v-model="fromData.skill[0].describe[2]">
                        </div>
                    </div>
                    <div class="item-footer"><i class=" icon-plus-sign-alt icon-1x" @click="skillIconClick" v-show="skillFlag<2"></i>&nbsp;&nbsp;&nbsp;</div>
                </div>

                <div class="item last-item">
                    <div class="item-head">Self assetsment:</div>
                    <div class="item-content">
                        <div class="inp-long inp-long-more">Detaiils:
                            <input type="text" placeholder="1." v-model="fromData.selfAssessment[0]">
                            <input type="text" placeholder="2." v-model="fromData.selfAssessment[1]">
                            <input type="text" placeholder="3." v-model="fromData.selfAssessment[2]">
                        </div>
                    </div>
                    <div class="item-footer"><i class=" icon-plus-sign-alt icon-1x"></i>&nbsp;&nbsp;&nbsp;</div>
                </div>
            </div>
            <div class="xs"></div>
            <div class="xs2"></div>
            <div class="from-box-footer">
                <span class="butt" @click="createResClick">Generate Resume</span>
            </div>
        </div>
     </div>
</template>

<script type="text/ecmascript-6">
    export default{
        data(){
            return {
                msg: 'hello vue',
                workExperienceFlag:0,
                projectExperienceFlag:0,
                skillFlag:0,
                fromData:{
                    "head":{
                        "name":"",
                        "intention":"",
                        "tel":"",
                        "email":"",
                        "address":"",
                        // "age":"",
                        // "sex":"",
                        "school":"",
                        "graduationTime":"",
                        "graduation":"",
                        "major":"",
                        "honor":"",
                        "interest":"",
                        "speciality":"",
                        "specialityPer":""
                    },
                    "blogLink":{
                        "github":"",
                        "blog":""
                    },
                    "workExperience":{
                        "time":"",
                        "experience":[
                            {
                                "name":"",
                                "skill":"",
                                "time":"",
                                "describe":[
                                    //"","",""
                                ]
                            },
                            {
                                "name":"",
                                "skill":"",
                                "time":"",
                                "describe":[
                                    //"","",""
                                ]
                            },
                            {
                                "name":"",
                                "skill":"",
                                "time":"",
                                "describe":[
                                    "","",""
                                ]
                            }
                        ]
                    },
                    "projectExperience":{
                        "time":"",
                        "experience":[
                            {
                                "name":"",
                                "skill":"",
                                "time":"",
                                "describe":[
                                    "","",""
                                ]
                            },
                            {
                                "name":"",
                                "skill":"",
                                "time":"",
                                "describe":[
                                    "","",""
                                ]
                            },
                            {
                                "name":"",
                                "skill":"",
                                "time":"",
                                "describe":[
                                    "","",""
                                ]
                            }
                        ]
                    },
                    "skill":[
                        {
                            "type":"",
                            "describe":[
                                "","",""
                            ]
                        },
                        {
                            "type":"",
                            "describe":[
                                "","",""
                            ]
                        },
                        {
                            "type":"",
                            "describe":[
                                "","",""
                            ]
                        }
                    ],
                    "selfAssessment":[
                        "","",""
                    ]
                }
            }
        },
        props:{
            resumeData:{
                type:Object
            }
        },
        created(){
//            console.log(this.resumeData);
            if(this.resumeData.formFlag){
                this.fromData = this.resumeData
            }
        },
        watch:{
            "fromData": {
                handler: function (val, oldVal) {
                 //  pass to App.vue
                    this.$emit('listenFormList',{type:"fromData","fromData":this.fromData});
                },
                deep:true
            }
        },
        methods:{
            createResClick: function () {
                this.$emit('listenFormList',{type:"createResClick","showFlag":false});
            },
            workIconClick: function () {
                this.workExperienceFlag++;
            },
            pojIconClick: function () {
                this.projectExperienceFlag++;
            },
            skillIconClick: function () {
                this.skillFlag++;
            }
        },
        components: {}
    }
</script>

<style>
    #from_box {
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background: rgba(0, 0, 0, 0.2);
    }
    /* from-content
    -----------------------------------*/
    .from-content {
        position: fixed;
        top: 0;
        left: 2%;
        bottom: 0;
        margin: auto auto;
        width: 35%;
        max-width: 450px;
        min-width: 400px;
        height: 85%;
        padding: 1rem;
        box-sizing: border-box;
        background: #ffffff;
    }
    /* from-content  from-content-item
    -----------------------------------*/
    .from-content .from-content-item{
        width: 100%;
        height: 100%;
        overflow: auto;
    }
    .from-content-item::-webkit-scrollbar {
        display: none;
    }
    .from-content .item {
        color: #ffffff;
        font-size: 2rem;
        margin-bottom: 1.4rem;
        box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
    }
    .from-content .item-head {
        width: 100%;
        background: #42b983;
        padding: 0.8rem 0;
        text-indent: 1.4rem;
    }
    .item-head .item-head-time{
        display: inline-block;
        text-align: right;
        font-size: 1.6rem;
        float: right;
        margin-top: 4px;
        margin-right: 1rem;
    }
    .item-head-time input{
        background: #42b983;
        border-bottom: 2px solid #ffffff;
        text-indent: 1rem;
        color: #ffffff;
    }
    .from-content .item-content {
        color: #313131;
        font-size: 1.6rem;
        margin: 1rem 1rem;
        line-height: 1.5;
    }
    .from-content .item-footer {
        width: 100%;
        background: #42b983;
        text-align: right;
    }
    .from-content .inp-short {
        width: 50%;
        float: left;
    }
    .inp-short input[type='text'] {
        border-bottom: 2px solid #42b983;
        text-indent: 1rem;
    }
    .from-content .inp-long{
        width: 100%;
    }
    .from-content .inp-long-more{
        line-height: 1.6;
    }
    .inp-long input[type='text'] {
        border-bottom: 2px solid #42b983;
        text-indent: 1rem;
        width: 100%;
    }
    .from-content .last-item{
        margin-bottom: 4.5rem;
    }
    .from-content .xs{
        position: absolute;
        top: 0;
        right: 0;
        width: 0;
        height: 0;
        border-top: 4rem solid #3ca777;
        border-right: 4rem solid #3ca777;
        border-bottom: 4rem solid transparent;
        border-left: 4rem solid transparent;
    }
    .from-content .xs2{
        position: absolute;
        top: 0;
        right: 0;
        width: 0;
        height: 0;
        border-top: 2rem solid #ffffff;
        border-right: 2rem solid #ffffff;
        border-bottom: 2rem solid transparent;
        border-left: 2rem solid transparent;
    }
    /* from-content from-box-footer
    -----------------------------------*/
    .from-content .from-box-footer{
        position: absolute;
        bottom:8px;
        left: 5px;
        width: 100%;
        height: 4rem;
        background: #ebebeb;
        box-shadow: -4px 9px 8px 0 rgba(0, 0, 0, 0.2);
    }
    .from-box-footer .butt{
        display: inline-block;
        border-radius: 0.4rem;
        border: 1px solid #3ead7b;
        font-size: 2rem;
        color: #3ca777;
        float: right;
        padding: 0.2rem;
        margin: 0.5rem 1rem 0 0;
     }
    .from-box-footer .butt:hover{
        box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
        cursor: pointer;
    }
</style>

<template>
    <div class="fillcontain">
        <head-top></head-top>
        <div class="table_container">
            <el-tabs type="border-card">
                <el-tab-pane label="会员资料">
                    <el-row>
                        <el-col :span="15">
                            <div class="grid-content bg-purple clumOne">
                                <table class="member_count">
                                    <tr>
                                        <td>会员ID</td>
                                        <td>80001737</td>
                                        <td>采购数量</td>
                                        <td>79820</td>
                                    </tr>
                                    <tr>
                                        <td>用户名</td>
                                        <td>13678954132</td>
                                        <td>累计金额</td>
                                        <td>2326919.21</td>
                                    </tr>
                                    <tr>
                                        <td>等级</td>
                                        <td>批发会员</td>
                                        <td>真实姓名</td>
                                        <td>X</td>
                                    </tr>
                                    <tr>
                                        <td>积分</td>
                                        <td>81168</td>
                                        <td>性别</td>
                                        <td>女</td>
                                    </tr>
                                    <tr>
                                        <td>禁用</td>
                                        <td>否</td>
                                        <td>出生日期</td>
                                        <td>1990-11-23</td>
                                    </tr>
                                    <tr>
                                        <td>注册时间</td>
                                        <td>xxxx</td>
                                        <td>城市</td>
                                        <td>新加坡</td>
                                    </tr>
                                    <tr>
                                        <td>注册IP</td>
                                        <td>109.156.21.146</td>
                                        <td>E-mail</td>
                                        <td>eleonorachen@gmail.com</td>
                                    </tr>
                                    <tr>
                                        <td>注册时间</td>
                                        <td>xxxx</td>
                                        <td>城市</td>
                                        <td>新加坡</td>
                                    </tr>
                                    <tr>
                                        <td>注册IP</td>
                                        <td>109.156.21.146</td>
                                        <td>E-mail</td>
                                        <td>eleonorachen@gmail.com</td>
                                    </tr>
                                    <tr>
                                        <td>注册时间</td>
                                        <td>xxxx</td>
                                        <td>城市</td>
                                        <td>新加坡</td>
                                    </tr>
                                    <tr>
                                        <td>注册IP</td>
                                        <td>109.156.21.146</td>
                                        <td>E-mail</td>
                                        <td>eleonorachen@gmail.com</td>
                                    </tr>
                                </table>
                            </div>
                        </el-col>
                        <el-col :span="9">
                            <div class="grid-content bg-purple-light clumTwo">
                                <table class="member_sum">
                                    <!-- border="1" cellspacing="0" cellpadding="0" -->
                                    <tr>
                                        <td>交易排名</td>
                                        <td>100</td>
                                        <td>贡献值</td>
                                        <td>10000</td>
                                    </tr>
                                    <tr>
                                        <td>平均单量</td>
                                        <td>12件</td>
                                        <td>平均单价</td>
                                        <td>26.00</td>
                                    </tr>
                                    <tr>
                                        <td>30天订单数</td>
                                        <td>20</td>
                                        <td>30天交易额</td>
                                        <td>6000</td>
                                    </tr>
                                </table>
                                <br>
                                <div class="custmer_laber">
                                    <div class="custmer_laber_s"><span>客户标签</span></div>
                                    <div class="custmer_content1">
                                        <span>女装</span>
                                        <span>韩版</span>
                                        <span>好质量</span>
                                        <span>爽快</span>
                                        <span>老客户</span>
                                    </div>
                                </div>
                                <br>
                                <div class="custmer_experts">
                                    <div class="custmer_experts_s"><span>客户顾问：许顺</span></div>
                                    <div class="custmer_content2">备注信息</div>
                                </div>
                            </div>
                        </el-col>
                    </el-row>
                </el-tab-pane>
                <el-tab-pane label="余额(100000.00)">
                    <el-table :data="tableData" highlight-current-row style="width: 100%">
                        <el-table-column type="index" width="60">
                        </el-table-column>
                        <el-table-column label="操作类型" width="100" property="edit_type">
                        </el-table-column>
                        <el-table-column label="订单号" width="120" property="pursh_code">
                        </el-table-column>
                        <el-table-column label="存入" width="140" property="save_in">
                        </el-table-column>
                        <el-table-column label="支出" width="140" property="save_out">
                        </el-table-column>
                        <el-table-column label="余额" width="140" property="cost_count">
                        </el-table-column>
                        <el-table-column label="交易时间" width="130" property="sell_time">
                        </el-table-column>
                        <el-table-column label="操作人" width="100" property="edit_name">
                        </el-table-column>
                        <el-table-column label="备注" width="140" property="edit_exp">
                        </el-table-column>
                        <el-table-column label="查看" width="140">
                            <template scope="scope">
                                <el-button style="border:none;" size="small" @click="handleEdit">[订单]</el-button>
                            </template>
                        </el-table-column>
                    </el-table>
                </el-tab-pane>
                <el-tab-pane label="收藏">收藏</el-tab-pane>
                <el-tab-pane label="关注">关注</el-tab-pane>
                <el-tab-pane label="地址">地址</el-tab-pane>
            </el-tabs>
            <div class="return_button">
                <el-button>返回</el-button>
            </div>
        </div>
    </div>
</template>
<script>
import headTop from '../components/headTop'
export default {

    data() {
            return {
                tableData: [{
                    edit_type: '提现',
                    pursh_code: '900023',
                    save_in: '100',
                    save_out: '1200',
                    cost_count: '50',
                    sell_time: '2016-10-10',
                    edit_name: '管理员',
                    edit_exp: '补运费',

                }]
            }

        },
        components: {
            headTop,
        },
        methods: {
            // async initData(){
            //           // try{
            //           //     this.city = await cityGuess();
            //           //     const countData = await getResturantsCount();
            //           //     if (countData.status == 1) {
            //           //         this.count = countData.count;
            //           //     }else{
            //           //         throw new Error('获取数据失败');
            //           //     }
            //           //     this.getResturants();
            //           // }catch(err){
            //           //     console.log('获取数据失败', err);
            //           // }
            // }
            // 
            handleEdit() {
                this.$router.push({
                    path: '/member'
                });
            },

        },
}
</script>
<style lang="less">
@import '../style/mixin';
table {
    border-collapse: collapse;
}

table tr td {
    height: 50px;
    border-top: 1px solid #dedede;
    border-bottom: 1px solid #dedede;
    font-size: 15px;
    color: #656a69;
}

.table_container {
    position: relative;
}

.member_count {
    margin-left: 20px;
    width: 620px;
    height: 450px;
    // border:1px solid red;
}

.member_sum {
    width: 430px;
    height: 152px;
    // border:1px solid red;
}

.custmer_laber {
    padding-left: 5px;
    font-size: 15px;
    color: #656a69;
    width: 430px;
    height: 148px;
    border: 1px solid #dedede;
}

.custmer_laber .custmer_laber_s {
    margin-top: 8px;
    margin-bottom: 10px;
}

.custmer_laber .custmer_content1 {
    width: 230px;
    height: 90px;
}

.custmer_laber .custmer_content1 span {
    text-align: center;
    vertical-align: middle;
    margin: 5px;
    display: inline-block;
    width: 60px;
    height: 30px;
    line-height: 30px;
    border: 1px solid red;
    color: red;
}

.custmer_experts {
    font-size: 15px;
    color: #656a69;
    width: 430px;
    height: 255px;
    border: 1px solid #dedede;
}

.custmer_experts .custmer_experts_s {
    margin-top: 8px;
    margin-bottom: 10px;
    margin-left: 10px;
}

.custmer_experts .custmer_content2 {
    margin-left: 10px;
    width: 230px;
    height: 90px;
}

.return_button {
    position: absolute;
    top: 26px;
    right: 30px;
}

.return_button .el-button {
    display: inline-block;
    width: 95px;
    height: 30px;
    line-height: 1;
    vertical-align: middle;
    white-space: nowrap;
    cursor: pointer;
    background: #e6e6e6;
    border: 1px solid #c4c4c4;
    font-size: 17px;
    color: #000;
    margin: 0;
    padding: 5px 10px;
    border-radius: 4px;
}
</style>

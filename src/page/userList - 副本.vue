<template>
    <div class="fillcontain">
        <head-top></head-top>
        <div class="headAdv">
            <div class="listed">
                <span style="font:9px;color:#000;"><strong>会员列表</strong></span>
            </div>
            <div class="searched">
                <div class="searched_left">
                    <el-select v-model="myvalue1" filterable placeholder="请选择" @change="test">
                        <el-option v-for="item in options1" :key="item.value" :label="item.label" :value="item.value">
                        </el-option>
                    </el-select>
                </div>
                <div class="searched_right">
                    <el-input icon="search" v-model="input2">
                        <el-button slot="append">查询</el-button>
                    </el-input>
                </div>
                <div class="searched_middle">
                    <span>显示</span>&nbsp;
                    <el-select v-model="myvalue2" filterable style="margin-left:-30px;">
                        <el-option v-for="item in options2" :key="item.value" :label="item.label" :value="item.value"> </el-option>
                    </el-select>
                </div>
            </div>
            <div class="recorded">
                <span><strong style="font:8px;color:#000;">总记录数 {{count}}</strong></span>
            </div>
        </div>
        <!-- 以后需要从后台模拟数据出来 -->
        <div class="table_container">
            <el-table :data="tableData" highlight-current-row style="width: 100%">
                <el-table-column type="index" width="80">
                </el-table-column>
                <el-table-column property="levelname" label="等级" width="100">
                </el-table-column>
                <el-table-column property="username" label="用户名" width="100">
                </el-table-column>
                <el-table-column property="areaname" label="地区" width="100">
                </el-table-column>
                <el-table-column property="purshname" label="订单" width="100">
                </el-table-column>
                <el-table-column property="countname" label="数量" width="100">
                </el-table-column>
                <el-table-column property="pricename" label="金额" width="110">
                </el-table-column>
                <el-table-column property="costname" label="余额" width="110">
                </el-table-column>
                <el-table-column property="registe_time" label="注册时间" width="120">
                </el-table-column>
                <el-table-column property="editname" label="操作" width="80">
                    <template scope="scope">
                        <el-button style="border:none;" size="small" @click="handleEdit">[详情]</el-button>
                    </template>
                </el-table-column>
                <el-table-column property="statusname" label="状态" width="80">
                </el-table-column>
            </el-table>
            <div class="Pagination" style="text-align: center;margin-top: 10px;opacity:0">
                <el-pagination @size-change="handleSizeChange" @current-change="handleCurrentChange" :current-page="currentPage" :page-size="20" layout="total, prev, pager, next" :total="count">
                </el-pagination>
            </div>
        </div>
    </div>
</template>
<script>
import headTop from '../components/headTop'
import {
    getUserList,
    getUserCount
} from '@/api/getData'
export default {
    data() {
        return {
            tableData: [{
                levelname: '批发会员',
                areaname: '美国',
                purshname: '5566',
                username: '王小虎',
                countname: '10000',
                pricename: '1000',
                costname: '1000000',
                registe_time: '2016-10-10',
                statusname: '正常',

            }, {
                levelname: '批发会员',
                areaname: '美国',
                purshname: '5566',
                username: '王小虎',
                countname: '10000',
                pricename: '1000',
                costname: '1000000',
                registe_time: '2016-10-10',
                statusname: '正常',

            }, {
                levelname: '批发会员',
                areaname: '美国',
                purshname: '5566',
                username: '王小虎',
                countname: '10000',
                pricename: '1000',
                costname: '1000000',
                registe_time: '2016-10-10',
                statusname: '正常',

            }, {
                levelname: '批发会员',
                areaname: '美国',
                purshname: '5566',
                username: '王小虎',
                countname: '10000',
                pricename: '1000',
                costname: '1000000',
                registe_time: '2016-10-10',
                statusname: '正常',
            }, {
                levelname: '批发会员',
                areaname: '美国',
                purshname: '5566',
                username: '王小虎',
                countname: '10000',
                pricename: '1000',
                costname: '1000000',
                registe_time: '2016-10-10',
                statusname: '正常',
            }, {
                levelname: '批发会员',
                areaname: '美国',
                purshname: '5566',
                username: '王小虎',
                countname: '10000',
                pricename: '1000',
                costname: '1000000',
                registe_time: '2016-10-10',
                statusname: '正常',
            }, {
                levelname: '批发会员',
                areaname: '美国',
                purshname: '5566',
                username: '王小虎',
                countname: '10000',
                pricename: '1000',
                costname: '1000000',
                registe_time: '2016-10-10',
                statusname: '正常',
            }, {
                levelname: '批发会员',
                areaname: '美国',
                purshname: '5566',
                username: '王小虎',
                countname: '10000',
                pricename: '1000',
                costname: '1000000',
                registe_time: '2016-10-10',
                statusname: '正常',
            }, {
                levelname: '批发会员',
                areaname: '美国',
                purshname: '5566',
                username: '王小虎',
                countname: '10000',
                pricename: '1000',
                costname: '1000000',
                registe_time: '2016-10-10',
                statusname: '正常',
            }, {
                levelname: '批发会员',
                areaname: '美国',
                purshname: '5566',
                username: '王小虎',
                countname: '10000',
                pricename: '1000',
                costname: '1000000',
                registe_time: '2016-10-10',
                statusname: '正常',
            }, {
                levelname: 'VIP',
                areaname: '美国',
                purshname: '7788',
                username: '陈小曼',
                countname: '10000',
                pricename: '1000',
                costname: '1000000',
                registe_time: '2016-10-10',
                statusname: '正常',
            }, {
                levelname: 'VIP',
                areaname: '美国',
                purshname: '7788',
                username: '陈小曼',
                countname: '10000',
                pricename: '1000',
                costname: '1000000',
                registe_time: '2016-10-10',
                statusname: '正常',
            }, {
                levelname: 'VIP',
                areaname: '美国',
                purshname: '7788',
                username: '陈小曼',
                countname: '10000',
                pricename: '1000',
                costname: '1000000',
                registe_time: '2016-10-10',
                statusname: '正常',
            }, {
                levelname: 'VIP',
                areaname: '美国',
                purshname: '7788',
                username: '陈小曼',
                countname: '10000',
                pricename: '1000',
                costname: '1000000',
                registe_time: '2016-10-10',
                statusname: '正常',
            }, {
                levelname: 'VIP',
                areaname: '美国',
                purshname: '7788',
                username: '陈小曼',
                countname: '10000',
                pricename: '1000',
                costname: '1000000',
                registe_time: '2016-10-10',
                statusname: '正常',
            }, {
                levelname: 'VIP',
                areaname: '美国',
                purshname: '7788',
                username: '陈小曼',
                countname: '10000',
                pricename: '1000',
                costname: '1000000',
                registe_time: '2016-10-10',
                statusname: '正常',
            }, {
                levelname: 'VIP',
                areaname: '美国',
                purshname: '7788',
                username: '陈小曼',
                countname: '10000',
                pricename: '1000',
                costname: '1000000',
                registe_time: '2016-10-10',
                statusname: '正常',
            }, {
                levelname: 'VIP',
                areaname: '美国',
                purshname: '7788',
                username: '陈小曼',
                countname: '10000',
                pricename: '1000',
                costname: '1000000',
                registe_time: '2016-10-10',
                statusname: '正常',
            }, {
                levelname: 'VIP',
                areaname: '美国',
                purshname: '7788',
                username: '陈小曼',
                countname: '10000',
                pricename: '1000',
                costname: '1000000',
                registe_time: '2016-10-10',
                statusname: '正常',
            }, {
                levelname: 'VIP',
                areaname: '美国',
                purshname: '7788',
                username: '陈小曼',
                countname: '10000',
                pricename: '1000',
                costname: '1000000',
                registe_time: '2016-10-10',
                statusname: '正常',
            }, {
                levelname: '注册会员',
                areaname: '美国',
                purshname: '9900',
                username: '惠彬',
                countname: '10000',
                pricename: '1000',
                costname: '1000000',
                registe_time: '2016-10-10',
                statusname: '正常',
            }, {
                levelname: '注册会员',
                areaname: '美国',
                purshname: '9900',
                username: '惠彬',
                countname: '10000',
                pricename: '1000',
                costname: '1000000',
                registe_time: '2016-10-10',
                statusname: '正常',
            }, {
                levelname: '注册会员',
                areaname: '美国',
                purshname: '9900',
                username: '惠彬',
                countname: '10000',
                pricename: '1000',
                costname: '1000000',
                registe_time: '2016-10-10',
                statusname: '正常',
            }, {
                levelname: '注册会员',
                areaname: '美国',
                purshname: '9900',
                username: '惠彬',
                countname: '10000',
                pricename: '1000',
                costname: '1000000',
                registe_time: '2016-10-10',
                statusname: '正常',
            }, {
                levelname: '注册会员',
                areaname: '美国',
                purshname: '9900',
                username: '惠彬',
                countname: '10000',
                pricename: '1000',
                costname: '1000000',
                registe_time: '2016-10-10',
                statusname: '正常',
            }, {
                levelname: '注册会员',
                areaname: '美国',
                purshname: '9900',
                username: '惠彬',
                countname: '10000',
                pricename: '1000',
                costname: '1000000',
                registe_time: '2016-10-10',
                statusname: '正常',
            }, {
                levelname: '注册会员',
                areaname: '美国',
                purshname: '9900',
                username: '惠彬',
                countname: '10000',
                pricename: '1000',
                costname: '1000000',
                registe_time: '2016-10-10',
                statusname: '正常',
            }, {
                levelname: '注册会员',
                areaname: '美国',
                purshname: '9900',
                username: '惠彬',
                countname: '10000',
                pricename: '1000',
                costname: '1000000',
                registe_time: '2016-10-10',
                statusname: '正常',
            }, {
                levelname: '注册会员',
                areaname: '美国',
                purshname: '9900',
                username: '惠彬',
                countname: '10000',
                pricename: '1000',
                costname: '1000000',
                registe_time: '2016-10-10',
                statusname: '正常',
            }, {
                levelname: '注册会员',
                areaname: '美国',
                purshname: '9900',
                username: '惠彬',
                countname: '10000',
                pricename: '1000',
                costname: '1000000',
                registe_time: '2016-10-10',
                statusname: '正常',
            }, {
                levelname: '注册会员',
                areaname: '美国',
                purshname: '9900',
                username: '惠彬',
                countname: '10000',
                pricename: '1000',
                costname: '1000000',
                registe_time: '2016-10-10',
                statusname: '正常',

            }, {
                levelname: '注册会员',
                areaname: '美国',
                purshname: '9900',
                username: '惠彬',
                countname: '10000',
                pricename: '1000',
                costname: '1000000',
                registe_time: '2016-10-10',
                statusname: '正常',

            }, {
                levelname: '注册会员',
                areaname: '美国',
                purshname: '9900',
                username: '惠彬',
                countname: '10000',
                pricename: '1000',
                costname: '1000000',
                registe_time: '2016-10-10',
                statusname: '正常',

            }, {
                levelname: '注册会员',
                areaname: '美国',
                purshname: '1086',
                username: '小红',
                countname: '10000',
                pricename: '1000',
                costname: '1000000',
                registe_time: '2016-10-10',
                statusname: '正常',

            }, {
                levelname: '注册会员',
                areaname: '美国',
                purshname: '1086',
                username: '小红',
                countname: '10000',
                pricename: '1000',
                costname: '1000000',
                registe_time: '2016-10-10',
                statusname: '正常',

            }, {
                levelname: '注册会员',
                areaname: '美国',
                purshname: '1086',
                username: '小红',
                countname: '10000',
                pricename: '1000',
                costname: '1000000',
                registe_time: '2016-10-10',
                statusname: '正常',

            }, {
                levelname: '注册会员',
                areaname: '美国',
                purshname: '1086',
                username: '小红',
                countname: '10000',
                pricename: '1000',
                costname: '1000000',
                registe_time: '2016-10-10',
                statusname: '正常',

            }, {
                levelname: '注册会员',
                areaname: '美国',
                purshname: '1086',
                username: '小红',
                countname: '10000',
                pricename: '1000',
                costname: '1000000',
                registe_time: '2016-10-10',
                statusname: '正常',

            }],
            options1: [{
                value: '所有等级',
                label: '所有等级'
            }, {
                value: 'VIP',
                label: 'VIP'
            }, {
                value: '批发会员',
                label: '批发会员'
            }, {
                value: '选项4',
                label: '注册会员'
            }],
            options2: [{
                value: '选项1',
                label: '30'
            }, {
                value: '选项2',
                label: '60'
            }, {
                value: '选项3',
                label: '90'
            }, {
                value: '选项4',
                label: '120'
            }],
            input1: '',
            input2: '',
            myvalue1: '所有等级',
            myvalue2: '30',
            currentRow: null,
            offset: 0,
            limit: 20,
            count: 0,
            currentPage: 1,
        }
    },
    components: {
        headTop,
    },
    computed: {
        // tableFilter() {
        //     return this.myvalue1.length ? this.tableData.filter(item => item.statusopt.indexof(this.myvalue1) > -1) : this.tableData;
        // }
    },

    // 创建后的钩子函数

    // 注意这个循环逻辑

    // this.tableData.forEach((e, i) => {
    //     if (e.statusopt == myvalue1) {
    //         tablearray.push(this.tableData[i]);
    //     }
    //     // console.log(tablearray);
    //     this.tableData = tablearray;
    // })

    created() {
        this.initData();
    },
    methods: {
        test(myvalue1) {
            console.log(myvalue1);
            let tablearray = [];
            if (myvalue1 !== '') {
                tablearray = this.tableData.filter(item => {
                    return item.levelname !== null && item.levelname == myvalue1
                });
                this.tableData = tablearray;

            } else {
                // this.tableData = [];

            }
        },
        async initData() {
            try {
                const countData = await getUserCount();
                if (countData.status == 1) {
                    this.count = countData.count;
                } else {
                    throw new Error('获取数据失败');
                }
                this.getUsers();
            } catch (err) {
                console.log('获取数据失败', err);
            }
        },
        handleSizeChange(val) {
            console.log(`每页 ${val} 条`);
        },
        handleCurrentChange(val) {
            this.currentPage = val;
            this.offset = (val - 1) * this.limit;
            this.getUsers()
        },
        handleEdit() {
            this.$router.push({
                path: '/memberDetail'
            });
        },
        // async getUsers() {
        //     const Users = await getUserList({ offset: this.offset, limit: this.limit });
        //     this.tableData = [];
        //     Users.forEach(item => {
        //         const tableData = {};
        //         tableData.username = item.username;
        //         tableData.registe_time = item.registe_time;
        //         tableData.city = item.city;
        //         this.tableData.push(tableData);
        //     })
        // },

    },
}

</script>
<style lang="less">
@import '../style/mixin';
.qf {
    *zoom: 1;
}

.qf:after {
    content: '';
    display: table;
    clear: both;
}

.fl {
    float: left;
}

.fr {
    float: right;
}

.table_container {
    padding: 20px;
}

.fillcontain .headAdv {
    display: flex;
    justify-content: space-between;
    height: 45px;
    line-height: 45px;
}

.headAdv .listed {
    display: inline-block;
    padding-left: 22px;
}

.headAdv .searched {
    display: inline-block;
    text-align: center;
    width: 550px;
    height: 45px;
}

.headAdv .el-input__inner {
    -webkit-appearance: none;
    -moz-appearance: none;
    appearance: none;
    background-color: #fff;
    background-image: none;
    border-radius: 50px;
    border-top-right-radius: 0;
    border-bottom-right-radius: 0;
    border: 1px solid #bfcbd9;
    box-sizing: border-box;
    color: #1f2d3d;
    font-size: inherit;
    height: 32px;
    line-height: 1;
    outline: 0;
    padding: 3px 10px;
    transition: border-color .2s cubic-bezier(.645, .045, .355, 1);
}

.headAdv .searched .searched_left .el-input__inner {
    border-radius: 5px;
}

.headAdv .searched .searched_middle .el-input__inner {
    width: 50px;
    border-radius: 5px;
}

.headAdv .searched .el-select .el-input {
    width: 112px;
    height: 45px;
    border-radius: 50px;
}

.headAdv .searched .searched_left {
    display: inline-block;
    position: relative;
    left: 0px;
}

.headAdv .searched .searched_right {
    display: inline-block;
    position: relative;
    left: 5px;
}

.headAdv .searched .searched_middle {
    display: inline-block;
    position: relative;
    top: 0px;
    left: 40px;
}

.headAdv .recorded {
    display: inline-block;
    width: 170px;
    height: 50px;
}

.el-table th {
    white-space: nowrap;
    overflow: hidden;
    background-color: #50606a;
    text-align: left;
}

.el-table th>.cell {
    background-color: #4f616a;
}

.el-table__footer-wrapper thead div,
.el-table__header-wrapper thead div {
    background-color: #eef1f6;
    color: #1f2d3d;
    color: white;
}

.el-input-group__append {
    background-color: rgb(0, 209, 186);
    color: #fff;
    vertical-align: middle;
    display: table-cell;
    position: relative;
    border-radius: 50px;
    border-top-left-radius: 0;
    border-bottom-left-radius: 0;
    border: 1px solid #bfcbd9;
    padding: 0 10px;
    width: 1px;
    white-space: nowrap;
}

.el-input-group__prepend {}

.el-input__icon {
    position: absolute;
    width: 35px;
    height: 100%;
    left: 2px;
    top: 2px;
    text-align: center;
    color: #bfcbd9;
    transition: all .3s;
}

.el-select .el-input .el-input__icon {
    color: #bfcbd9;
    font-size: 12px;
    transition: transform .3s;
    -ms-transform: translateY(-50%) rotate(180deg);
    transform: translateY(-50%) rotateZ(180deg);
    line-height: 16px;
    left: 80px;
    top: 52%;
    cursor: pointer;
}

.searched_middle .el-select .el-input .el-input__icon {
    left: 50px;
}

</style>

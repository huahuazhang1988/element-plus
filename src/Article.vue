<template>
    <el-form :inline="true" :model="formInline" class="demo-form-inline">

        <el-form-item label="Activity zone">
            <el-select v-model="formInline.region" placeholder="please choose" clearable>
                <el-option label="nature" value="nature" />
                <el-option label="universal" value="universal" />
            </el-select>
        </el-form-item>
        <el-form-item label="Activity zone">
            <el-select v-model="formInline.region" placeholder="please choose" clearable>
                <el-option label="true" value="true" />
                <el-option label="false" value="false" />
            </el-select>
        </el-form-item>

        <el-form-item>
            <el-button type="primary" @click="onSubmit">search</el-button>
        </el-form-item>
        <el-form-item>
            <el-button type="default" @click="onSubmit">reset</el-button>
        </el-form-item>
    </el-form>
    <br>
    <el-table :data="tableData" style="width: 1200px;">
        <el-table-column prop="title" label="title" />
        <el-table-column prop="category" label="category" />
        <el-table-column prop="createTime" label="createTime" />
        <el-table-column prop="state" label="state" />
        <el-table-column label="operation" width="150">
            <el-button type="primary" :icon="Edit" circle />
            <el-button type="danger" :icon="Delete" circle />
        </el-table-column>
    </el-table> <br>

    <div class="demo-pagination-block">
        <div class="demonstration">All combined</div>
        <el-pagination v-model:current-page="currentPage4" v-model:page-size="pageSize4" :page-sizes="[5, 10, 20, 30]"
            :size="size" :disabled="disabled" :background="background" layout="total, sizes, prev, pager, next, jumper"
            :total="40" @size-change="handleSizeChange" @current-change="handleCurrentChange" />
    </div>
</template>

<script lang="ts" setup>
import {Delete,Edit} from '@element-plus/icons-vue'
import { ref,reactive } from 'vue'
import  { ComponentSize } from 'element-plus'
//form
const formInline = reactive({
    user: '',
    region: '',
    date: '',
})

const onSubmit = () => {
    console.log('submit!')
}
//分页条
const currentPage4 = ref(1)

const pageSize4 = ref(10)

const background = ref(false)
const disabled = ref(false)

const handleSizeChange = (val: number) => {
    console.log(`${val} items per page`)
}
const handleCurrentChange = (val: number) => {
    console.log(`current page: ${val}`)
}
//table
const tableData = [
    {
        title: '2016-05-03',
        category:"natue",
        createTime: '2001-01-02',
        state: 'true'
    },
    {
        title: '2016-05-03',
        category: "natue",
        createTime: '2001-01-02',
        state: 'true'
    },
    {
        title: '2016-05-03',
        category: "natue",
        createTime: '2001-01-02',
        state: 'true'
    },
    {
        title: '2016-05-03',
        category: "natue",
        createTime: '2001-01-02',
        state: 'true'
    }
]
</script>
<style scoped>
.demo-form-inline .el-select {
    --el-select-width: 220px;
}
</style>

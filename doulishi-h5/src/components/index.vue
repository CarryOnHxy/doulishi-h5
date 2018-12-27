<template>
    <div class="container">
        <index-con/>
    </div>
</template>
<script>
import indexCon from './common/index-con.vue'
export default {
    components:{indexCon}
}
</script>
<style lang="less" scoped>
    @import (less) '../assets/less/tool.less';
    .container{
        .wh(100vw,100vh)
    }
</style>


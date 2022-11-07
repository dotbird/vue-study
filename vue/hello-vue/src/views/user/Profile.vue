<template>
    <div>
      <h1>个人信息</h1>
      <!--{{$router.params.id}}-->
      {{id}}
    </div>
</template>

<script>
    export default {
        props: ['id'],
        name: "UserProfile",
        //钩子函数 过滤器
        beforeRouteEnter: ((to, from, next) => {
          console.log("准备 进入 个人信息页");
          next(vm => {
            //进入路由之前执行getData方法
            vm.getData()
          });
        }),
        beforeRouteLeave: ((to, from, next) => {
          console.log("准备 离开 个人信息页");
          next();
        }),
        //axios
        methods: {
          getData: function () {
            this.axios({
              method: 'get',
              url: 'http://localhost:8080/static/mock/data.json'
            }).then(function (response) {
              console.log(response)
            })
          }
        }
    }
</script>

<style scoped>

</style>

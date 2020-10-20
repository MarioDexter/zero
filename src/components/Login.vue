<template>
    <div class="login_content">
        <div class="login_box">
            <div class="avatar_box">
                <img src="../assets/logo.png" alt="">
            </div>
        </div>
    </div>
</template>

<script>
export default {}
</script>
<style lang="scss" scope>
    .login_content {
        background-color: #2b4b6b;
        height: 100%;
        .login_box {
            width: 450px;
            height: 300px;
            background-color: aliceblue;
            border-radius: 5px;
            position: absolute;
            left: 50%;
            top: 50%;
            transform: translate(-50%,-50%);
            .avatar_box{
                width: 130px;
                height: 130px;
                border-radius: 50%;
                border: 1px solid #eee;
                padding: 10px;
                position: absolute;
                left: 50%;
                transform: translate(-50%,-50%);
                background-color: #fff;
                img{
                    width: 100%;
                    height: 100%;
                    border-radius: 50%;
                    background-color: #eee;
                }
            }
        }
    }
</style>

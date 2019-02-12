<template>
<nav>
    <ul>
        <li><span><a href="#">HOME</a></span></li>
        <li><span><a href="#">APP</a></span></li>
        <li><span><a href="#">LOGIN</a></span></li>
        <li><span><a href="#">ABOUT</a></span></li>
    </ul>
</nav>
</template>
<script> 
</script>
<style scoped>
nav{
    background-clip : border-box;
    background-color: #f6f6f8;
    height: 70px;
    padding-right: 30px;
    margin:0px 0px;
    border-bottom: 1px solid gainsboro;
   
}
a:hover{
    text-decoration: none;
    color: blueviolet
}
a{
    text-decoration: none;
    color: black;
}
ul{
    font-size : 1.2rem;
    font-weight: 900;
    margin-top: 25px;
    list-style-type: none;
    color:black;
    float:right;
}
li{
    display: inline-block;
    margin-left: 50px;
}
</style>
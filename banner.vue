<template>
    <div id="main-banner">
        <h1>Luísa´s Closet</h1>
    </div>
</template>


<script>
export default{
name: "banner"
}
</script>

<style scoped>
#main-banner{
    background-image: url('/public/img/burger.jpg') ;
    background-position: 0% - 250px;
    background-size: cover;
    height: 750px;
    width: 1350px;
    display: flex ;
    align-items: center;
    justify-content: flex-start;
}

#main-banner h1{
    color: #97227e;
    text-align: center;
    font-size: 60px;
    background-color:rgb(220, 189, 221);
    padding: 20px 40px;
}
</style>

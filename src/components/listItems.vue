<template>
  
    <div class="card">
        <img :src="item.links[0].href" alt="">
        <div class="container">
            <h4>{{ item.data[0].title }}</h4>
            <p>{{ item.data[0].description }}</p>
            <div class="tags">
                <div class="tagItem" v-for="tag in item.data[0]?.keywords?.slice(0,3)" :key="tag" >{{tag}}</div>
            </div>
        </div>
    </div>
</template>
<script>
export default {
    name: 'listItem',
    props: ['item']
}
</script>
<style scoped>
.card {
    border: 1px solid red;
    box-shadow: 1px 3px 3px 1px;
    width: 250px;
    height: 100%;
    border-radius: 10px;
    transition: all 0.5s;
    padding: 5px 10px;
}
.card img {
    width: 100%;
    height: 150px;
    object-fit: fill;
    border-radius: 10px;
}
.card:hover {
    transform: scale(1.05);
}
h4 {
    color: darkred;
    font-size: 22px;
    font-weight: 400;
}
p {
    overflow: hidden;
    text-overflow: ellipsis;
    display: -webkit-box;
    -webkit-line-clamp: 1;
    -webkit-box-orient: vertical;
    font-size: 17px;

}
.tags{
    margin-bottom: 15px;
    display: flex;
    gap: 15px;
    flex-wrap: wrap;
    cursor: pointer;
}
.tagItem {
    background-color: beige;
    color: indigo;
    border-radius: 8px;
    padding: 4px;
    font-size: 13px;


}

    
</style>
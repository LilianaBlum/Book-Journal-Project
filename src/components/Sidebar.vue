<!-- eslint-disable vue/multi-word-component-names -->
<template>
    <div>
        <img src="@/images/blank-profile-picture.jpg" style="width:80%; padding: 20px; border-radius: 50%;">
        <p id="user-name">{{ username }}</p>
        <p id="sign-out">Sign out</p>
    </div>
</template>

<script>
export default {
    data() {
        return {
            username: 'User 1',
        }
    }}
</script>

<style>

#user-name{
    text-align: center;
    margin:10px;
    padding: 10px 5px 10px 5px;
    background-color: #FFB5A4;
    color: #fff;
    text-transform: uppercase;
    font-size: large;
    border-radius: 50px;
}

#sign-out {
    text-align: center;
    margin:10px 15px;
    bottom: 2%;
    width: 80%;
    position: absolute;
    padding: 10px 5px 10px 5px;
    background-color: #f8f0f0;
    color: #6e6464;
    text-transform: uppercase;
    font-size: large;
    border-radius: 50px;
}
</style>
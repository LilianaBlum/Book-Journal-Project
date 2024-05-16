<template>
    <div>
        <h1>BOOKS</h1>
        <div id="folder-list">
            <div v-for="(item, index) in folderList" :key=index @click="changeSelectedFolder(item)" >
                {{ item }}
            </div>
        </div>
        <div style="display: flex; width: 100%; margin: 15px 0px;">
            <div id="chosen-folder">
                <h5 style="padding-left: 10px; margin: 15px 0px 10px 5px;">{{ chosenFolder }}</h5>
            </div>
            <div id="books-folders" style="width: 100%;float: right; margin-top: 0px">
                <button>Add Book</button>
                <button>Add Folder</button>
            </div>
        </div>
    </div>
</template>

<script>
export default{
    data() {
        return {
            folderList: ['All', 'folder2', 'folder3', 'folder4'],
            chosenFolder: 'All'
        }
    },
    methods: {
        changeSelectedFolder(title){
            this.chosenFolder = title;
        }
    }
}
</script>

<style>

#folder-list{
    display: flex;
    margin-top: 10px;
    padding: 10px 0px 10px 1%;
    margin-right:2%;
    border-top: 1px solid rgb(162, 156, 156);
    border-bottom: 1px solid rgb(162, 156, 156);
}

#folder-list div {
    margin-right:7%;
    text-transform: uppercase;
    padding:5px;
    font-weight: bold;
}

#folder-list div:hover {
    color: #FFB5A4;
    cursor: pointer;
}

#books-folders {
    display: flex;
    justify-content: right;
    margin-right:2%;
    margin-top: 35px;
}

button {
    margin-left:1%;
    text-transform: uppercase;
    background-color: #FFB5A4;
    border-radius: 50px;
    color: #fff;
    border: 2px grey solid;
    padding: 10px 20px 10px 20px;
    font-weight:700;
    font-size: 15px;
}

button:hover {
    background-color: rgb(184, 179, 179);
    cursor: pointer;
}

#chosen-folder{
    font-size: 25px;
    text-transform: uppercase;
    font-weight: normal;
}

</style>
<template>
    <div style="display:flex" v-if="isVisible" id="userBookInfo">
        <p style="width:25%; padding-left: 20px;">Title: {{ bookTitle}}</p>
        <p style="width:25%">Author: {{ bookAuthor }}</p>
        <div style="width:50%">
        <img id="bookImage" :src="bookImage" alt="Cover image of book">
        </div>
        <div>
            Rating: {{ bookRating }}
        </div>
    </div>
</template>

<script>
import json from '@/json/books.json'
export default {
    props: {
        isVisible: {
            type: Boolean,
            default: false,
        },
        bookTitle: {
            type: String
        },
        bookAuthor: {
            type: String
        },
        bookImage: {
            type: String
        },
        bookId: {
            type: String
        }
    },
    data() {
        return {
            ratings: json.ratings
        }
    },
    mounted() {
        this.processBookData();
    },
    methods: {
        processBookData(){
            console.log(this.ratings)
            const rating = this.ratings.find(r => r.id == this.bookId);
            this.bookRating = rating ? rating.rating : 'No rating';
        }
    }
}

</script>

<style>
#userBookInfo{
    padding: 20px;
    width: 100%;
    height: 100%;
    font-size: 20px;
}

#bookImage {
    border: 5px solid #c2bcbc !important;
    height: 450px !important;
    margin-top: 20px;
    margin-right: 20px;
    float: right;
}

#bookImage:hover{
    border: 5px solid #c2bcbc !important;
    height: 450px !important;
    cursor:default !important;  
}
</style>
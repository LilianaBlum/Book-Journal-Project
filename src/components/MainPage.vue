<template>
    <div>
        <div id="book-list">
            <li v-for="book in books" :key=book.id>
                <img @click="openBookInfo(book)" :src="book.image" alt="Cover image of book">
                <h5>{{ book.title }}</h5>
            </li>
            
            <Teleport to="body">
                <div style="
                    position: fixed;
                    width: 100%;
                    height: 100%;
                    left: 0;
                    top: 0;
                    cursor:pointer" v-if="isVisible"
                    @click="isVisible = false">
                    <PersonalBookInfo :bookId = this.chosenBookId :bookImage = this.chosenImage :bookAuthor=this.chosenAuthor :isVisible = isVisible :bookTitle = this.chosenTitle id="userBookInfo" @click.stop/>
                    <button @click="isVisible=false" v-if="isVisible" id="closeBookInfo">
                        Close book info
                    </button>
                </div>
            </Teleport>
        </div>
        <button @click="topFunction" id="myBtn" v-show="isButtonVisible" title="Go to top">Top</button>
    </div>
</template>

<script>
import json from '@/json/books.json'
import PersonalBookInfo from '@/components/PersonalBookInfo.vue'
export default{
    props: ['chosenFolder'],
    components: {
        PersonalBookInfo,
    },
    data() {
        return {
            books: json.books,
            isButtonVisible: false,
            isVisible: false,
            chosenTitle: '',
            chosenAuthor: '',
            chosenImage: '',
            chosenBookId: ''
        }
    },
    methods:{
        topFunction() {
            window.scrollTo({ top: 0, behavior: 'smooth' });
        },
        scrollFunction() {
            const scrollPosition = window.scrollY || document.documentElement.scrollTop;
            this.isButtonVisible = scrollPosition > 20;
        },
        openBookInfo(book){
            this.chosenTitle = book.title;
            this.chosenAuthor = book.author;
            this.chosenImage = book.image;
            this.chosenBookId = book.id;
            this.isVisible = true;
            console.log(this.chosenBookId)
            this.$emit('formBookInfo', book);
        },
        closeBookInfo(){
            if(this.isVisible === true){
                this.isVisible = false;
            }
            console.log('test')
            
        },
    mounted() {
    // Adding the scroll event listener when the component mounts
        window.addEventListener('scroll', this.scrollFunction);
    },
    beforeUnmount() {
        // Removing the scroll event listener before the component is destroyed
        window.removeEventListener('scroll', this.scrollFunction);
    }
    }}
</script>

<style>

#book-list {
    display: flex;
    max-height: 10%;
    list-style: none;
    padding-left: 0px;
    flex-wrap: wrap;
}

#book-list li{
    padding: 10px;
    height: fit-content;
    justify-content: center;
    width: 300px;
}

#book-list h5 {
    text-align: center;
    font-size: 30px;
    border-radius: 50px;
    background-color: #AAC9Ce;
    margin-top: 15px;
    font-weight: 200;
    padding: 5px;
}

#book-list img {
    height: 450px;
}

#book-list img:hover {
    border: 5px solid #FFB5A4;
    height: 440px;
    cursor: pointer;
}

#myBtn {
  position: fixed;
  bottom: 1%;
  right: 11%;
  z-index: 99;
  font-size: 18px;
  border: none;
  outline: none;
  background-color: #FFB5A4;
  color: white;
  cursor: pointer;
  padding: 25px;
  border-radius: 4px;
}

#myBtn:hover {
  background-color: #555;
}

#userBookInfo {
    position: fixed; /* Use fixed positioning to take the div out of document flow */
    width: 52%;     /* Span the full width of the viewport */
    height: 55%;    /* Span the full height of the viewport */
    margin-left: 30%;
    margin-top:14%;
    display: flex;   /* Enables the use of flexbox to center the content */
    background-color: rgba(0, 0, 0, 0.5); /* Optional: semi-transparent background */
    z-index: 1000;   /* Ensure it's on top of other content */
    background-color: #fff;
    cursor: default;
}

#closeBookInfo{
    position: fixed; /* Use fixed positioning to take the div out of document flow */
    left: 10;
    right: 21%;
    bottom: 300px;
    margin-left: 55%;
    display: flex;   /* Enables the use of flexbox to center the content */
    background-color: rgba(0, 0, 0, 0.5); /* Optional: semi-transparent background */
    z-index: 1000;   /* Ensure it's on top of other content */
}

</style>
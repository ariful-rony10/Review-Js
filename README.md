# Review Js
 A review section using js.

In APP.JS
At first declared an array named reviewes which is an object with reviewers info.
```
const reviews = [
    {
        id: 1,
        name: "Jon Doe",
        profession: "Web Developer",
        img: "https://images.unsplash.com/flagged/photo-1570612861542-284f4c12e75f?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1170&q=80",
        review: "Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specime"
    },
    {
        id: 2,
        name: "Jon Doe 2",
        profession: "Web Designer",
        img: "https://images.unsplash.com/photo-1547425260-76bcadfb4f2c?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1170&q=80",
        review: "Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s"
    },
    {
        id: 3,
        name: "Jon Doe 3",
        profession: "UI/UX Designer",
        img: "https://images.unsplash.com/photo-1544005313-94ddf0286df2?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=688&q=80",
        review: "Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages, and more recently with desktop publishing software like Aldus PageMaker including versions of Lorem Ipsum."
    },
]
```
Then selected all the element from dom
```
// Select elements from DOM
const name = document.getElementById("review-author");
const profession = document.getElementById("review-profession");
const image = document.getElementById("review-person-img");
const text = document.getElementById("review-txt");
const previousButton = document.querySelector("#review-button-left")
const nextButton = document.querySelector("#review-button-right")
const randomButton = document.querySelector("#review-random-button")
```
Declared a currentList 
```
// Items
let currentItems = 0;
```
Declared a showReview function which will display reviews
```
// Show review function 
const showReview = (review) => {
    const item  = reviews[review];
    name.textContent = item.name;
    profession.textContent = item.textContent;
    image.src = item.img;
    text.textContent = item.review;
}
```
Initializing on load to display defaults
```
// Load initial item (on start it load)
window.addEventListener("DOMContentLoaded", ()=>{
    showReview(currentItems);
})
```
Add eventListeners on previous and next button to update the currentList
```
// next button 
nextButton.addEventListener("click", () => {
    currentItems++;
    if(currentItems > reviews.length - 1){
        currentItems = 0;
    }
    showReview(currentItems);
})
// Previous button 
previousButton.addEventListener("click", () => {
    currentItems--;
    if(currentItems < 0){
        currentItems = reviews.length - 1;
    }
    showReview(currentItems);
})
```
In random button at first generate a random number between reviews array then update the currentlist to display.
```
// Random Button 
randomButton.addEventListener("click", () =>{
    const randomNumber = Math.floor(Math.random() * reviews.length );
    currentItems = randomNumber;
    showReview(currentItems);
})
```
# Coad-Alpha_task1 - Image Gallery

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Image Gallery</title>
    <style>
      *{
    margin:0;
    padding:0;
    box-sizing:border-box;
}

body{
    font-family:Arial;
    background:hwb(0 96% 4% / 0.651);
    text-align:center;
}

h1{
    margin:3%;
    font-size: 60px;
    font-family: Georgia, 'Times New Roman', Times, serif;

}

.buttons{
    margin:20px;
    
}

.buttons button{
    padding:10px 30px;
    margin:10px;
    border:none;
    background:#007bff;
    color:white;
    cursor:pointer;
    border-radius:5px;
    transition:.3s;
    font-size: 20px;
}

.buttons button:hover{
    background:#0056b3;
}

.gallery{
    width:90%;
    margin:auto;
    display:grid;
    grid-template-columns:repeat(auto-fit,minmax(250px,1fr));
    gap:20px;
    position: absolute;
    bottom: 11%;
    left: 5%;
}

.image{
    overflow:hidden;
    box-shadow: 0 4px 8px rgba(0,0,0,0.2);
    transition: transform .3s; 
    box-shadow: .3s;
}

.image img{
    width:100%;
    height:250px;
    object-fit:cover;
    border-radius:10px;
    cursor:pointer;
    transition:.4s;
}
.image.show img {
  height: 550px;   
  
}

.image img:hover{
    transform:scale(1.08);
    filter:brightness(80%);
}

#lightbox{
    position:fixed;
    top:0;
    left:0;
    width:100%;
    height:100%;
    background:rgba(0,0,0,.9);
    display:none;
    justify-content:center;
    align-items:center;
}

#lightbox img{
    width:50%;
    height:80%;
    border-radius:10px;
}

.close{
    position:absolute;
    top:20px;
    right:40px;
    color:white;
    font-size:40px;
    cursor:pointer;
}

.prev,.next{
    position:absolute;
    top:50%;
    transform:translateY(-50%);
    background:white;
    border:none;
    font-size:25px;
    padding:15px;
    cursor:pointer;
}

.prev{
    left:40px;
}

.next{
    right:40px;
}

@media(max-width:768px){

#lightbox img{
    width:90%;
}

.prev,.next{
    font-size:20px;
    padding:10px;
}

}
    </style>
</head>
<body>

    <h1>Image Gallery</h1>

    <!-- Filter Buttons -->
    <div class="buttons">
        <button onclick="filterImages('all')">All</button>
        <button onclick="filterImages('nature')">Nature</button>
        <button onclick="filterImages('animals')">Animals</button>
        <button onclick="filterImages('bird')">Bird</button>
        <button onclick="filterImages('city')">City</button>
        <button onclick="filterImages('flower')">flower</button>
        <button onclick="filterImages('moon')">Moon</button>
    </div>

    <!-- Gallery -->
    <div class="gallery">

        <div class="image nature">
            <img src="https://images.openai.com/static-rsc-4/uQMsBy4qoySmu0Md49-V4aygcs-U_lL6QzXmgKtjwh3LAURq5Vwit9yV27U0x7WpVMKcVhDKJas0r2ClcGISf-_Nj3hwWw7jxPWwcE3jho-3VHTseY88T0hospZFlCiAKiUZhOM-q5aAElwBeGLiDjRWR3xzitq-SG6VXrZJWNMpWbOSnWgRY-ZNPZRfNFly?purpose=fullsize" onclick="openLightbox(0)">
        </div>

         <div class="image bird">
            <img src="https://images.unsplash.com/photo-1480044965905-02098d419e96?q=80&w=1170&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D" onclick="openLightbox(1)">
        </div>

        <div class="image nature">
            <img src="https://images.pexels.com/photos/38688449/pexels-photo-38688449.jpeg" onclick="openLightbox(1)">
        </div>

        <div class="image animals">
            <img src="https://images.unsplash.com/photo-1504006833117-8886a355efbf?q=80&w=1170&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D" onclick="openLightbox(3)">
        </div>

        <div class="image city">
            <img src="https://images.openai.com/static-rsc-4/JM31LyTrQ40NicjWWDfJ32EwFKEVthqIsrxf1ypMwTyxDphPEAjnWluh65aAFFtBTaifNywkcA9bMvG-XnKSGth4_fj_7vDLiFls_vC9KXk9nYIXfUZoXjhTF3ehhMEx4LHPR-_mLX99Tus9ZsDJ5dNmaQ0aBQqGHCvEktAbEUuzXGtBGn6g8wrAlZL9O7-z?purpose=fullsize" onclick="openLightbox(4)">
        </div>

        <div class="image flower">
            <img src="https://images.unsplash.com/photo-1785293130707-ae6dce76474a?w=600&auto=format&fit=crop&q=60&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxmZWF0dXJlZC1waG90b3MtZmVlZHwxOXx8fGVufDB8fHx8fA%3D%3D" onclick="openLightbox(6)">

        </div>

        <div class="image city">
            <img src="https://images.openai.com/static-rsc-4/X9NvLzIg3n2-qcCuyiOil87vvWh8tJ8JKtcIHRjsh4Pjd5KbJiT7b8hAIVXP9IJ246TB540phxSzbedt1ZP610OVRZpRficlDrKBZDpSmPBuPUfiY9iSSGg7vkDVSu-JuuhTGC1CjGRTZyBCoaFS7cImsXbwJK8_ebWR-SjAPjasp0vArI5kSBdjWXtR2RSg?purpose=fullsize" onclick="openLightbox(5)">
        </div>

         <div class="image moon">
            <img src="https://plus.unsplash.com/premium_photo-1767615278643-3bc025bf74cb?q=80&w=713&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D" onclick="openLightbox(8)">
        </div>

        <div class="image flower">
            <img src="https://plus.unsplash.com/premium_photo-1676475964992-6404b8db0b53?w=600&auto=format&fit=crop&q=60&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxzZWFyY2h8OXx8Zmxvd2VyfGVufDB8fDB8fHww"  onclick="openLightbox(7)">

        </div>

        <div class="image moon">
            <img src="https://images.unsplash.com/photo-1514897575457-c4db467cf78e?q=80&w=1170&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D" onclick="openLightbox(9)">
        </div>

         <div class="image bird">
            <img src="https://images.unsplash.com/photo-1606567595334-d39972c85dbe?w=600&auto=format&fit=crop&q=60&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxzZWFyY2h8Nnx8YmlyZHN8ZW58MHx8MHx8fDA%3D" onclick="openLightbox(10)">
        </div>

         <div class="image animals">
            <img src="https://images.openai.com/static-rsc-4/vsZgS73CCRPdtvsgHqcczFV1A0LCIH4Xa2vVWf5S1SSnoMFHX5w8MjvyeGGDbc2qPGo1hkCP-SY2XDp_rRW2N-Ce0qNPG5pEzTBP6WZfIithIFmVMhBWPx-3983SNH30DhpJPN2O5aGbgO3qh6DJhw9aBc-D5HLHN8um_4FcV0QciwGUI7WlH5WChYeHuISK?purpose=fullsize" onclick="openLightbox(2)">
        </div>
 
        

    </div>


    <div id="lightbox">

        <span class="close" onclick="closeLightbox()">&times;</span>

        <button class="prev" onclick="previousImage()">&#10094;</button>

        <img id="lightbox-img">

        <button class="next" onclick="nextImage()">&#10095;</button>

    </div>

   <script>
let images = [
  "https://images.openai.com/static-rsc-4/uQMsBy4qoySmu0Md49-V4aygcs-U_lL6QzXmgKtjwh3LAURq5Vwit9yV27U0x7WpVMKcVhDKJas0r2ClcGISf-_Nj3hwWw7jxPWwcE3jho-3VHTseY88T0hospZFlCiAKiUZhOM-q5aAElwBeGLiDjRWR3xzitq-SG6VXrZJWNMpWbOSnWgRY-ZNPZRfNFly?purpose=fullsize",
  "https://images.pexels.com/photos/38688449/pexels-photo-38688449.jpeg",
  "https://images.openai.com/static-rsc-4/vsZgS73CCRPdtvsgHqcczFV1A0LCIH4Xa2vVWf5S1SSnoMFHX5w8MjvyeGGDbc2qPGo1hkCP-SY2XDp_rRW2N-Ce0qNPG5pEzTBP6WZfIithIFmVMhBWPx-3983SNH30DhpJPN2O5aGbgO3qh6DJhw9aBc-D5HLHN8um_4FcV0QciwGUI7WlH5WChYeHuISK?purpose=fullsize",
  "https://images.unsplash.com/photo-1504006833117-8886a355efbf?q=80&w=1170&auto=format&fit=crop&ixlib=rb-4.1.0",
  "https://images.openai.com/static-rsc-4/JM31LyTrQ40NicjWWDfJ32EwFKEVthqIsrxf1ypMwTyxDphPEAjnWluh65aAFFtBTaifNywkcA9bMvG-XnKSGth4_fj_7vDLiFls_vC9KXk9nYIXfUZoXjhTF3ehhMEx4LHPR-_mLX99Tus9ZsDJ5dNmaQ0aBQqGHCvEktAbEUuzXGtBGn6g8wrAlZL9O7-z?purpose=fullsize",
  "https://images.openai.com/static-rsc-4/X9NvLzIg3n2-qcCuyiOil87vvWh8tJ8JKtcIHRjsh4Pjd5KbJiT7b8hAIVXP9IJ246TB540phxSzbedt1ZP610OVRZpRficlDrKBZDpSmPBuPUfiY9iSSGg7vkDVSu-JuuhTGC1CjGRTZyBCoaFS7cImsXbwJK8_ebWR-SjAPjasp0vArI5kSBdjWXtR2RSg?purpose=fullsize",
  "https://images.unsplash.com/photo-1785293130707-ae6dce76474a?w=600&auto=format&fit=crop&q=60&ixlib=rb-4.1.0",
  "https://plus.unsplash.com/premium_photo-1676475964992-6404b8db0b53?w=600&auto=format&fit=crop&q=60&ixlib=rb-4.1.0",
  "https://plus.unsplash.com/premium_photo-1767615278643-3bc025bf74cb?q=80&w=713&auto=format&fit=crop&ixlib=rb-4.1.0",
  "https://images.unsplash.com/photo-1514897575457-c4db467cf78e?q=80&w=1170&auto=format&fit=crop&ixlib=rb-4.1.0",
  "https://images.unsplash.com/photo-1606567595334-d39972c85dbe?w=600&auto=format&fit=crop&q=60&ixlib=rb-4.1.0",
  "https://images.unsplash.com/photo-1480044965905-02098d419e96?q=80&w=1170&auto=format&fit=crop&ixlib=rb-4.1.0"
];

let current = 0; 
let selectedCategories = [];

function openLightbox(index) {
  current = index;
  document.getElementById("lightbox").style.display = "flex";
  document.getElementById("lightbox-img").src = images[current];
}

function closeLightbox() {
  document.getElementById("lightbox").style.display = "none";
}

function nextImage() {
  current++;
  if (current >= images.length) {
    current = 0;
  }
  document.getElementById("lightbox-img").src = images[current];
}

function previousImage() {
  current--;
  if (current < 0) {
    current = images.length - 1;
  }
  document.getElementById("lightbox-img").src = images[current];
}

function filterImages(category) {
  let items = document.querySelectorAll(".image");

  items.forEach(function(item) {
    // remove old "show" class
    item.classList.remove("show");

    if (category === "all") {
      item.style.display = "block";
    } else if (item.classList.contains(category)) {
      item.style.display = "block";
      item.classList.add("show");   
    } else {
      item.style.display = "none";
    }
  });
}


</script>


</body>
</html>

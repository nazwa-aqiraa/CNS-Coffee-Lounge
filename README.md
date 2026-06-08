<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>CNS Coffee Lounge</title>

<meta name="description" content="CNS Coffee Lounge - Premium Coffee Experience">

<link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.1/css/all.min.css" rel="stylesheet">

<style>

*{
margin:0;
padding:0;
box-sizing:border-box;
scroll-behavior:smooth;
font-family:'Segoe UI',sans-serif;
}

body{
background:#0f0f0f;
color:white;
}

.navbar{
position:fixed;
top:0;
width:100%;
background:rgba(0,0,0,.9);
backdrop-filter:blur(15px);
display:flex;
justify-content:space-between;
align-items:center;
padding:15px 50px;
z-index:999;
}

.logo{
display:flex;
align-items:center;
gap:10px;
}

.logo img{
width:55px;
height:55px;
border-radius:50%;
}

.nav-links{
display:flex;
gap:30px;
}

.nav-links a{
color:white;
text-decoration:none;
font-weight:600;
transition:.3s;
}

.nav-links a:hover{
color:#b58863;
}

.hero{
height:100vh;
background:
linear-gradient(rgba(0,0,0,.7),rgba(0,0,0,.7)),
url("IMG-20260526-WA0018.jpg");
background-size:cover;
background-position:center;
display:flex;
align-items:center;
justify-content:center;
text-align:center;
}

.hero-content h1{
font-size:70px;
}

.hero-content p{
margin-top:15px;
font-size:20px;
}

.btn{
background:#8B5E3C;
padding:15px 30px;
border:none;
border-radius:30px;
color:white;
margin-top:20px;
cursor:pointer;
}

.section{
padding:100px 8%;
}

.title{
font-size:40px;
margin-bottom:30px;
color:#c89f72;
}

.search-box{
width:100%;
padding:15px;
border:none;
border-radius:10px;
margin-bottom:30px;
}

.category{
margin-bottom:60px;
}

.menu-grid{
display:grid;
grid-template-columns:repeat(auto-fit,minmax(250px,1fr));
gap:20px;
}

.menu-card{
background:#1b1b1b;
padding:20px;
border-radius:20px;
transition:.3s;
}

.menu-card:hover{
transform:translateY(-8px);
}

.menu-card h3{
margin-bottom:10px;
}

.price{
color:#c89f72;
font-size:20px;
font-weight:bold;
}

.add-btn{
width:100%;
padding:10px;
margin-top:15px;
background:#8B5E3C;
color:white;
border:none;
border-radius:10px;
cursor:pointer;
}

.gallery{
display:grid;
grid-template-columns:repeat(auto-fit,minmax(300px,1fr));
gap:20px;
}

.gallery img{
width:100%;
height:350px;
object-fit:cover;
border-radius:20px;
}

.review{
background:#1b1b1b;
padding:20px;
border-radius:15px;
margin-bottom:15px;
}

.cart-btn{
position:fixed;
right:20px;
bottom:20px;
width:65px;
height:65px;
border-radius:50%;
background:#8B5E3C;
display:flex;
align-items:center;
justify-content:center;
font-size:24px;
cursor:pointer;
z-index:1000;
}

.cart-popup{
position:fixed;
right:-100%;
top:0;
width:400px;
height:100%;
background:#151515;
padding:25px;
transition:.5s;
overflow:auto;
z-index:9999;
}

.cart-popup.active{
right:0;
}

.cart-item{
display:flex;
justify-content:space-between;
margin-bottom:10px;
}

.remove-btn{
background:red;
color:white;
border:none;
padding:5px 10px;
}

.whatsapp-btn{
width:100%;
padding:15px;
background:#25D366;
border:none;
color:white;
font-size:18px;
margin-top:20px;
}

.back-btn{
width:100%;
padding:15px;
background:#555;
border:none;
color:white;
margin-top:10px;
}

footer{
padding:30px;
text-align:center;
background:#000;
}

@media(max-width:768px){

.hero-content h1{
font-size:40px;
}

.nav-links{
display:none;
}

.cart-popup{
width:100%;
}

}


.gallery-manager{
background:#1b1b1b;
padding:20px;
border-radius:20px;
margin-bottom:25px;
}
.gallery-manager input,.gallery-manager button{
padding:10px;
margin:5px;
border-radius:10px;
border:none;
}

</style>
</head>
<body>

<nav class="navbar">

<div class="logo">
<img id="logoImage" src="logo cns REV2-01.jpg">
<input type="file" id="logoUpload" style="display:none" accept="image/*">
<h2>CNS Coffee Lounge</h2>
</div>

<div class="nav-links">
<a href="#home">Home</a>
<a href="#about">About</a>
<a href="#menu">Menu</a>
<a href="#gallery">Gallery</a>
<a href="#contact">Contact</a>
</div>

</nav>

<section class="hero" id="home">
<div class="hero-content">
<h1>CNS Coffee Lounge</h1>
<p>Coffee • Nail Studio • Salon</p>
<a href="#menu">
<button class="btn">Lihat Menu</button>
</a>
</div>
</section>

<section class="section" id="about">
<h2 class="title">Tentang CNS</h2>
<p>
Tempat nongkrong modern dengan konsep coffee lounge yang nyaman,
menu premium, interior estetik dan pelayanan terbaik.
</p>
</section>

<section class="section" id="menu">

<h2 class="title">Menu CNS</h2>

<input
type="text"
id="search"
class="search-box"
placeholder="Cari menu..."
onkeyup="searchMenu()">

<div id="menu-container"></div>

</section>

<section class="section" id="gallery">

<h2 class="title">Gallery</h2>


<div class="gallery-manager">
<h3 style="margin-bottom:15px;">Kelola Gambar Gallery</h3>
<input type="file" id="imageUpload" accept="image/*">
<input type="text" id="imageUrl" placeholder="Atau masukkan URL gambar">
<button onclick="addImage()">Tambah Gambar</button><button onclick="saveGallery()">Simpan Permanen</button>
</div>

<div class="gallery" id="galleryContainer">

<img src="IMG-20260526-WA0018.jpg">
<img src="IMG-20260526-WA0019(3).jpg">
<img src="IMG-20260530-WA0009.jpg">
<img src="hambach.jpeg">
<img src="pintu depan.jpeg">
<img src="logo cns REV2-01.jpg">

</div>

</section>

<section class="section">

<h2 class="title">Review Pelanggan</h2>

<div class="review">
⭐⭐⭐⭐⭐ Tempat nyaman, kopi enak dan harga terjangkau.
</div>

<div class="review">
⭐⭐⭐⭐⭐ Interior estetik dan cocok untuk kerja maupun nongkrong.
</div>

<div class="review">
⭐⭐⭐⭐⭐ Matcha Latte favorit saya.
</div>

</section>


<section class="section" id="contact">

<h2 class="title">Contact CNS Coffee Lounge</h2>
<p><strong>Instagram:</strong> @coffeenailsalon</p>
<p><strong>TikTok:</strong> @coffeenailsalon</p>
<p><strong>WhatsApp:</strong> 0811286865</p>
<br>

<h2 class="title">Kritik & Saran</h2>
<form action="mailto:cnscoffeelounge@gmail.com?subject=Kritik%20dan%20Saran%20CNS" method="post" enctype="text/plain">
<input type="text" name="Nama" placeholder="Nama" style="width:100%;padding:15px;border-radius:15px;margin-bottom:10px;">
<textarea name="Pesan" style="width:100%;height:150px;padding:15px;border-radius:15px;" placeholder="Tulis kritik dan saran Anda..."></textarea>
<br><br>
<button class="btn" type="submit">Kirim ke Email CNS</button>
</form>

<br><br>

<h2 class="title">Lokasi CNS</h2>

<iframe
src="https://maps.google.com/maps?q=CNS%20Coffee%20Lounge&t=&z=13&ie=UTF8&iwloc=&output=embed"
width="100%"
height="400"
style="border-radius:20px;border:none;">
</iframe>

</section>


<div class="cart-btn" onclick="openCart()">
🛒
</div>

<div class="cart-popup" id="cart">

<h2>Keranjang</h2>

<div id="cartItems"></div>

<h3>Total: Rp <span id="total">0</span></h3>

<button class="whatsapp-btn" onclick="checkout()">
Checkout WhatsApp
</button>

<button class="back-btn" onclick="closeCart()">
Kembali ke Menu
</button>

</div>

<footer>
© 2025 CNS Coffee Lounge
</footer>

<script>


const menu = [
["Americano",23000,"Coffee"],
["Latte",25000,"Coffee"],
["Cappuccino",25000,"Coffee"],
["Espresso",14000,"Coffee"],
["Long Black",16000,"Coffee"],
["Van Java",25000,"Coffee"],
["Butterscotch",29000,"Coffee"],
["Cheese Bomb",28000,"Coffee"],
["Hazel Alpen",28000,"Coffee"],
["Rose Amer",28000,"Coffee"],
["Salted Caramel",28000,"Coffee"],
["Caramel Macchiato",30000,"Coffee"],
["Pistachio Latte",28000,"Coffee"],
["CNS Creamy Coffee",35000,"Coffee"],
["Fraga Tea",27000,"Non Coffee"],
["Lemon Tea",22000,"Non Coffee"],
["Lychee Tea",25000,"Non Coffee"],
["Yakult Lychee Tea",26000,"Non Coffee"],
["Matcha Latte",27000,"Non Coffee"],
["Red Velvet",25000,"Non Coffee"],
["Taro Creamcheese",25000,"Non Coffee"],
["Matcha Strawberry",29000,"Non Coffee"],
["Dark Choco",26000,"Non Coffee"],
["Chicken Buttermilk",34000,"Food"],
["Chicken Salted Egg",34000,"Food"],
["Chicken Matah",34000,"Food"],
["Nasgor CNS",28000,"Food"],
["Nasgor Kampoeng",30000,"Food"],
["Mie Goreng",18000,"Food"],
["Mie Nyemek",25000,"Food"],
["Spaghetti Bolognese",20000,"Food"],
["Spaghetti Carbonara",20000,"Food"],
["Cinnamon Roll",18000,"Food"],
["Cireng",22000,"Food"],
["French Fries",25000,"Food"],
["Gyoza",20000,"Food"],
["Mix Platter",35000,"Food"],
["Pisang Goreng Ori",20000,"Food"],
["Add Coklat Keju",5000,"Addon"],
["Puding Caramel",16000,"Food"],
["Risol Mayo",28000,"Food"],
["Risol Ayam",27000,"Food"]
];


let cart=[];

function renderMenu(data=menu){

let html='';

data.forEach(item=>{

html+=`
<div class="menu-card">
<h3>${item[0]}</h3>
<p>${item[2]}</p>
<p class="price">Rp ${item[1].toLocaleString()}</p>

<button class="add-btn"
onclick="addCart('${item[0]}',${item[1]})">

Tambah ke Keranjang

</button>
</div>
`;

});

document.getElementById("menu-container").innerHTML=
`<div class="menu-grid">${html}</div>`;
}

renderMenu();

function searchMenu(){

let keyword=
document.getElementById("search").value.toLowerCase();

let filtered=
menu.filter(x =>
x[0].toLowerCase().includes(keyword)
);

renderMenu(filtered);

}

function addCart(name,price){

cart.push({name,price});

renderCart();

}

function renderCart(){

let html='';
let total=0;

cart.forEach((item,index)=>{

total+=item.price;

html+=`
<div class="cart-item">

${item.name}

<button
class="remove-btn"
onclick="removeItem(${index})">

X

</button>

</div>
`;

});

document.getElementById("cartItems").innerHTML=html;
document.getElementById("total").innerText=
total.toLocaleString();

}

function removeItem(index){

cart.splice(index,1);

renderCart();

}

function openCart(){

document.getElementById("cart")
.classList.add("active");

}

function closeCart(){

document.getElementById("cart")
.classList.remove("active");

window.location.href="#menu";

}

function checkout(){

let message="Halo CNS Coffee Lounge%0A%0ASaya ingin memesan:%0A";

cart.forEach(item=>{
message += "- "+item.name+"%0A";
});

window.open(
"https://wa.me/62811286865?text="+message,
"_blank"
);

}


function addImage(){

const gallery=document.getElementById('galleryContainer');

const fileInput=document.getElementById('imageUpload');
const urlInput=document.getElementById('imageUrl');

if(urlInput.value.trim()!==''){
const img=document.createElement('img');
img.src=urlInput.value.trim();
img.title='Klik 2x untuk ganti gambar';
img.ondblclick=function(){
let newUrl=prompt('Masukkan URL gambar baru:',img.src);
if(newUrl) img.src=newUrl;
};
gallery.appendChild(img);
urlInput.value='';
return;
}

if(fileInput.files.length>0){
const reader=new FileReader();
reader.onload=function(e){
const img=document.createElement('img');
img.src=e.target.result;
img.title='Klik 2x untuk ganti gambar';
img.ondblclick=function(){
let newUrl=prompt('Masukkan URL gambar baru:',img.src);
if(newUrl) img.src=newUrl;
};
gallery.appendChild(img);
};
reader.readAsDataURL(fileInput.files[0]);
fileInput.value='';
}
}


// Penyimpanan permanen gallery & logo menggunakan localStorage
function saveGallery(){
 const imgs=[...document.querySelectorAll('#galleryContainer img')].map(i=>i.src);
 localStorage.setItem('cns_gallery',JSON.stringify(imgs));
 alert('Gallery berhasil disimpan permanen');
}

window.addEventListener('load',()=>{
 const savedGallery=localStorage.getItem('cns_gallery');
 if(savedGallery){
   const gallery=document.getElementById('galleryContainer');
   gallery.innerHTML='';
   JSON.parse(savedGallery).forEach(src=>{
      const img=document.createElement('img');
      img.src=src;
      gallery.appendChild(img);
   });
 }

 const savedLogo=localStorage.getItem('cns_logo');
 if(savedLogo){
   document.getElementById('logoImage').src=savedLogo;
 }

 const uploader=document.getElementById('logoUpload');
 document.getElementById('logoImage').ondblclick=()=>uploader.click();

 uploader.addEventListener('change',e=>{
   const file=e.target.files[0];
   if(!file) return;
   const reader=new FileReader();
   reader.onload=function(ev){
      document.getElementById('logoImage').src=ev.target.result;
      localStorage.setItem('cns_logo',ev.target.result);
      alert('Logo CNS berhasil diperbarui');
   };
   reader.readAsDataURL(file);
 });
});

</script>

</body>
</html>

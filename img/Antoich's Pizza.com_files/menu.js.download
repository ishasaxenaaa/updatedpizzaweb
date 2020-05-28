let carts=document.querySelectorAll('.btnn');
let products=[
    {
        name:'Paneer Chilli Pizza',
        tag:'paneerchillli',
        price:10,
        inCart:0
    },
    {
        name:'Paneer Capsicum Pizza',
        tag:'paneercaosicum',
        price:11,
        inCart:0
    },
    {
        name:'Mashroom Pizza',
        tag:'mashroompizza',
        price:9,
        inCart:0
    },
    {
        name:'Tomato Chilli Pizza',
        tag:'tomatochili',
        price:10,
        inCart:0
    },
    {
        name:'Mixed Veg Pizza',
        tag:'mixvegetable',
        price:12,
        inCart:0
    },
    {
        name:'Paneer Mashroom Pizza',
        tag:'paneermashroom',
        price:9,
        inCart:0
    },
    {
        name:'Chicken Fiest Pizza',
        tag:'chickennudget',
        price:12,
        inCart:0
    },
    {
        name:'Chicken Dominator',
        tag:'chicken3',
        price:10,
        inCart:0
    },
    {
        name:'Chicken Golden Delight',
        tag:'chicken4',
        price:11,
        inCart:0
    },
    {
        name:'Bakers Pizza Special',
        tag:'bakerspizzaspcl',
        price:10,
        inCart:0
    },
    {
        name:'Cheese Balls',
        tag:'cheeseball',
        price:6,
        inCart:0
    },
    {
        name:'Cheese Dip',
        tag:'cheesedip',
        price:4,
        inCart:0
    },
    {
        name:'Choco Lava Cake',
        tag:'chocolava',
        price:12,
        inCart:0
    },
    {
        name:'Coke/Sprite',
        tag:'beverage',
        price:5,
        inCart:0
    },
];
for (let i=0;i<carts.length;i++){
    carts[i].addEventListener('click',()=>{
        cartNumbers(products[i]);
        totalCost(products[i])
    })
}
function onloadCartNumbers(){
    let productNumbers=localStorage.getItem('cartNumbers');
    if(productNumbers){
        document.querySelector('.cart span').textContent=productNumbers;

    }
}
function cartNumbers(product) {
    let productNumbers=localStorage.getItem('cartNumbers');
    productNumbers=parseInt(productNumbers);
    if(productNumbers){
        localStorage.setItem('cartNumbers',productNumbers + 1);
        document.querySelector('.cart span').textContent=productNumbers + 1;
    } else{
        localStorage.setItem('cartNumbers',1);
        document.querySelector('.cart span').textContent=1;
    }
    setItems(product);
 }
 function setItems(product){
     let cartItems=localStorage.getItem('productsInCart');
     cartItems=JSON.parse(cartItems);
     if(cartItems !=null){
         if(cartItems[product.tag]==undefined){
             cartItems={
                 ...cartItems,
                 [product.tag]:product
             }
         }
         cartItems[product.tag].inCart +=1;
     } else{
        product.inCart=1;
        cartItems={
            [product.tag]:product
        }
     }
     localStorage.setItem("productsInCart",JSON.stringify(cartItems))
 }
 function totalCost(product){
     //console.log("fghhjjj",product.price);
     let cartCost =localStorage.getItem('totalCost');

     if(cartCost!=null){
        cartCost=parseInt(cartCost);
        localStorage.setItem("totalCost",cartCost + product.price);
     } else{
        localStorage.setItem("totalCost",product.price);
     }
 }
 function displayCart(){
     let cartItems=localStorage.getItem("productsInCart");
     cartItems=JSON.parse(cartItems);
     let productContainer=document.querySelector(".products");
     let cartCost=localStorage.getItem('totalCost');
     if (cartItems && productContainer){
        productContainer.innerHTML='';
        Object.values(cartItems).map(item =>{
           productContainer.innerHTML += `
            <div class="products-container"> 
                <div class="product-title">
                    <img src="./img/${item.tag}.png" width="120" height="120">
                    <h5>${item.name}</h5>
                </div>
                <div class="price">$${item.price},00</div>   
                <div class="quantity">
                    <ion-icon class="decrease" name="arrow-dropleft-circle"></ion-icon>
                    <span>${item.inCart}</span>
                    <ion-icon class="decrease" name="arrow-dropright-circle"></ion-icon>
                </div>
                <div class="total">
                    $${item.inCart*item.price},00
                </div>

            `
        });
        productContainer.innerHTML +=`
            <div class="basketTotalContainer">
                <h2 class="basketTotalTitle">
                    Basket Total
                </h2>
                <h2 class="basketTotal">
                    $${cartCost},00
                </h2>
        
        `;
     }
    }

 onloadCartNumbers();
 displayCart();
Index.html 
<!DOCTYPE html> 
<html lang="en"> 
<head> 
    <meta charset="UTF-8"> 
    <meta name="viewport" content="width=device-width, initial-scale=1.0"> 
    <title>Online Shop</title> 
    <link rel="stylesheet" href="style.css"> 
</head> 
<body> 
 
<div class="container"> 
    <!-- Navigation Bar --> 
    <nav> 
        <ul> 
            <li><a href="#" onclick="showSection('home')">Home</a></li> 
            <li><a href="#" onclick="showSection('registration')">Register</a></li> 
            <li><a href="#" onclick="showSection('items')">Items</a></li> 
            <li><a href="#" onclick="showSection('cart')">Cart</a></li> 
            <li><a href="#" onclick="showSection('contact')">Contact Us</a></li> 
        </ul> 
    </nav> 
 
    <!-- Sections for different pages --> 
    <div id="home-section" class="section">Welcome to Our Online Store!</div>  
    <div id="registration-section" class="section" style="display:none;"> 
        <h2>Register</h2> 
        <form id="registration-form"> 
            <label for="username">Username:</label> 
            <input type="text" id="username" required><br> 
            <label for="email">Email:</label> 
            <input type="email" id="email" required><br> 
            <label for="password">Password:</label> 
            <input type="password" id="password" required><br> 
            <button type="submit">Register</button> 
        </form> 
    </div> 
 
    <div id="items-section" class="section" style="display:none;"> 
        <h2>Items for Sale</h2> 
        <div id="items"></div> 
    </div> 
 
    <div id="cart-section" class="section" style="display:none;"> 
        <h2>Your Cart</h2> 
        <div id="cart-items"></div> 
        <p id="total"></p> 
        <button id="checkout">Checkout</button> 
        <div id="payment-options" style="display:none;"> 
            <button id="mpesa">Pay with M-Pesa</button> 
            <button id="card">Pay with Card</button> 
            <button onclick="orderThroughWhatsApp()">Order through 
WhatsApp</button> 
        </div>     </div> 
 
    <!-- Contact Us Section --> 
    <div id="contact-section" class="section" style="display:none;"> 
        <h2>Contact Us</h2> 
        <p>If you have any questions or need help, feel free to reach out to us!</p> 
        <ul> 
            <li><strong>WhatsApp:</strong> <a href="https://wa.me/254758096913" target="_blank">+254758096913</a></li>             <li><strong>Email:</strong> <a href="mailto:mulwam2022@gmail.com">mulwam2022@gmail.com</a></li> 
            <li><strong>Telephone:</strong> +254790167576</li> 
        </ul> 
    </div> 
 
    <!-- Footer with Copyright --> 
    <footer> 
        <p>&copy; 2024 Online Shop. All rights reserved.</p> 
    </footer> </div> 
 
<script src="script.js"></script> 
 
</body> </html> 
 
 
Script.js 
var items = [ 
    { id: 1, name: "pimp Hip Red", price: 1500.00, image: 
"data:image/jpeg;base64,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
/wCs9S+iA8Eaaqt0RbYfCzxOlUREBERAREQf/9k="}, 
{ id: 2, name: "Africa Women Dress", price: 2000.00, image: 
"data:image/jpeg;base64,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" }, 
    { id: 3, name: "Turkey Dress", price: 3500.00, image: "https://encryptedtbn2.gstatic.com/shopping?q=tbn:ANd9GcRIsYckyGwsD3Dvn160yBvunNfSx_tJ7j3lDc3rGTbgh KQ2u5_0MX6pmQtTJ4NTDb7Q2HIcAmWi9I7EcUA-
XBMwcWJRrnJqtR_8r0Hpr2d0xVhjM91ZCvbGjiND8F3BOI1SXYZ9tW1CSbc&usqp=CAc" },     { id: 4, name: "Bohemian Dress", price: 1600.00, image: "https://encryptedtbn2.gstatic.com/shopping?q=tbn:ANd9GcQJY3vIFNS-
Ok5YAl0qQqRdUmBFsMXR7i4veYm7L53Rc21d1VxyrNauvRbaGB_xyuSisti_yDdvG7X4KgshJoF03G438 f_vuZLutZ8iohtdPg0w7jRj4icSknuem4VmtTl9Q2yTfuE&usqp=CAc"}, 
    { id: 3, name: "Mid Dress", price: 4500.00, image: "https://encryptedtbn1.gstatic.com/shopping?q=tbn:ANd9GcQRhCGlr0HQIZwfw_zAtPrtNFDdbf4cLdoWtgPUQshrH SCWEQmg8e82Y4y4x5C5a_I3j57ph-5fVkE2UyLBFjhFZzLgrOXcKajAIvVA9Ht5lryHYMvkqGOv6QNzoIJ2fx4vogPNusxlg&usqp=CAc" }, 
    { id: 3, name: "LeStyle Parfait Dress", price: 1900.00, image: 
"https://encrypted-
tbn0.gstatic.com/shopping?q=tbn:ANd9GcS5HVrGDUVKxP3s35rwp9PMDi8IWF9T8a6n-m9-
IhQOsipY-VzetFfVIB65leZL4Gaw1Zq0GSXAVrbtQHWrS4WeIHmavfbOh9IDOAPop-qHv8_MLcKMs0-
HMs3tYrSJ_0lBEfSckjI94w&usqp=CAc" }, 
    { id: 3, name: "Short Purf sleeve", price: 3000.00, image: 
"https://encrypted-tbn1.gstatic.com/shopping?q=tbn:ANd9GcRkxEM7L-
1t33QFgPmX6HypoWb7aM3ahfiHZtYdLC6jjlZbRCnmg5VoPdFxSJlGv9VJbXcC6nGlXTulHB4S2KMI8uo
CdWFGrWIy0bnPgPE5RGv6ojGpWsvAVb7mR8271g&usqp=CAc" }, 
    { id: 3, name: "Color Lace-up", price: 1200.00, image: "https://encryptedtbn1.gstatic.com/shopping?q=tbn:ANd9GcTbf1dl2vgNTcslqXZrZMLfAPs7moRBhXM1e0TpDe_Ps s2b_KEdaNLkMSuZMaUg3NSBh1w3MkRpTCfJn8ke1sftWUvNPUw06x74-
WYtXUGb7z_0c4l2WGdGnqnxZcwfLdtjeY9P4eE&usqp=CAc" }, 
    { id: 3, name: "Flare Sleeve Dress", price: 50.00, image: "https://encryptedtbn3.gstatic.com/shopping?q=tbn:ANd9GcTfd5CLDu6vG-w4EXHYcC1U6f7AT7yWR3HyOxnayACEbcgU7HVERxoq2CjoLpIDwTPdkco4t7sqCaitFap43BTnTrr2nVlrwU7reYkyBlFYFYE3fMta09&usqp=CAc" }, 
    { id: 3, name: "Short Puff Dress", price: 3500.00, image: "https://encryptedtbn0.gstatic.com/shopping?q=tbn:ANd9GcQVMNScmKP5zxFm9GMk7Y_uGhlVqWKuFBEKCPStm_L7d

jZgWX2ac1L1zxHkD0k3oxVWVVsRupwnw0ekFaJS2pmwXNdD5rcgcO1ZJ6cOC86UPu7uLYBwOvnP&usqp= CAc" }, 
    { id: 3, name: "Boho Floro dress", price: 1250.00, image: "https://encryptedtbn2.gstatic.com/shopping?q=tbn:ANd9GcQ-HkoDGOtHmNVbOef2DRfkkab_I_xsor5UbG1n92yAvZnl-
KaPNwaAt99exJHHz60Gdcelr57vs1dvotjV_vQ7qYt2_K9BBt32OcqCfy71zL3Af3tI0RsnuL7TL1c&us qp=CAc"}, 
    { id: 3, name: "Swing Dress", price: 5500.0, image: "https://encryptedtbn3.gstatic.com/shopping?q=tbn:ANd9GcSigpJ6BqPqyqkI16aIZEVQs2mDQcednJ1RWyRFE2fCebf1QlJaoMhvdlYXeOfb1jSqAUQhegM3jwReZx4-fHhkAscSvnBy23L-vEeocsV8lz579KqFBwgABBQK4MSoKdstWFJXDOg-U&usqp=CAc"}, 
    { id: 3, name: "plus size", price: 2500.00, image: "https://encryptedtbn0.gstatic.com/shopping?q=tbn:ANd9GcSgPI4S-D_V5MA6zT9m7VYl62MYNMI2eETIp-
UIgHQcyXmznSsZLkZCQEOV5YX4nQ7RM_xbiUvKDmKJAfzlqssRaJdy9AHH4qv5hwTG4TpVig06aoKK2MO J&usqp=CAc" }, 
    { id: 3, name: "Neck Big dress", price: 1299.00, image: "https://encryptedtbn3.gstatic.com/shopping?q=tbn:ANd9GcSSWgqtjOMHBdQ113dfFAl3xpk9y7WxziAmN78lrJLar CPjttmshBCsjZeorGP8kdcW1DUjlrA4DI0A4EGaYEZ7iEh-f-XGGOT7NyLvJj36mB2YXXhkkSBhA&usqp=CAc" }, 
    { id: 3, name: "Neck Wrap Dress", price: 4300.00, image: 
"https://www.topboho.com/cdn/shop/files/S5edeb5af17da48c7928fa9bfc2e78fa5X.jpg?v=
1698701472&width=360" }, 
];  var cart = []; var total = 0; 
 document.addEventListener("DOMContentLoaded", () => {     displayItems();     document.getElementById("registration-form").addEventListener("submit", handleRegistration);     document.getElementById("checkout").addEventListener("click", showPaymentOptions); 
    document.getElementById("mpesa").addEventListener("click", handleMpesaPayment);     document.getElementById("card").addEventListener("click", handleCardPayment); });  function displayItems() {     var itemsDiv = document.getElementById("items");     items.forEach(item => {         var itemDiv = document.createElement("div");         itemDiv.innerHTML = ` 
            <img src="${item.image}" alt="${item.name}"> 
            <h3>${item.name}</h3> 
 

<!DOCTYPE html>
<html lang="nl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Beglitterde Rozen</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <header>
        <img src="https://i.ibb.co/dmLbh1k/roses-logo.png" alt="Logo van Beglitterde Rozen" class="logo">
        <h1>Welkom bij Beglitterde Rozen</h1>
        <nav>
            <ul>
                <li><a href="#home">Home</a></li>
                <li><a href="#roses">Onze Rozen</a></li>
                <li><a href="#quiz">Rozen Quiz</a></li>
                <li><a href="#contact">Contact</a></li>
                <li><a href="#shop">Winkel</a></li>
                <li><a href="#cart">Winkelmandje</a></li>
            </ul>
        </nav>
    </header>
    
    <section id="home">
        <h2>Home</h2>
        <p>Wij zijn Magical Roses (leerlingen van 6H). We verkopen niet zomaar rozen, maar beglitterde rozen. Dit doen we voor twee redenen: we willen iedereen een kans geven om een zeer speciale bloem te geven aan zijn/haar geliefde op een gewone dag. Daarnaast willen we de kosten onderdrukken voor het eindejaars reis.</p>
    </section>
    
    <section id="roses">
        <h2>Onze Rozen</h2>
        <p>Bekijk onze prachtige beglitterde rozen.</p>
        <img src="images/rozen_foto.jpg" alt="Prachtige beglitterde rozen">
    </section>
    
    <section id="quiz">
        <h2>Rozen Quiz</h2>
        <form id="quizForm">
            <div class="question">
                <label for="question1">Hou je van rozen?</label><br>
                <input type="radio" id="yes1" name="question1" value="yes">
                <label for="yes1">Ja</label><br>
                <input type="radio" id="no1" name="question1" value="no">
                <label for="no1">Nee</label><br><br>
            </div>
            <div class="question">
                <label for="question2">Vind je het leuk om bloemen te ontvangen?</label><br>
                <input type="radio" id="yes2" name="question2" value="yes">
                <label for="yes2">Ja</label><br>
                <input type="radio" id="no2" name="question2" value="no">
                <label for="no2">Nee</label><br><br>
            </div>
            <div class="question">
                <label for="question3">Geef je vaak bloemen cadeau?</label><br>
                <input type="radio" id="yes3" name="question3" value="yes">
                <label for="yes3">Ja</label><br>
                <input type="radio" id="no3" name="question3" value="no">
                <label for="no3">Nee</label><br><br>
            </div>
            <div class="question">
                <label for="question4">Hou je van glitter op rozen?</label><br>
                <input type="radio" id="yes4" name="question4" value="yes">
                <label for="yes4">Ja</label><br>
                <input type="radio" id="no4" name="question4" value="no">
                <label for="no4">Nee</label><br><br>
            </div>
            <div class="question">
                <label for="question5">Vind je rozen romantisch?</label><br>
                <input type="radio" id="yes5" name="question5" value="yes">
                <label for="yes5">Ja</label><br>
                <input type="radio" id="no5" name="question5" value="no">
                <label for="no5">Nee</label><br><br>
            </div>
            <input type="submit" value="Verstuur">
        </form>
        <div id="result"></div>
    </section>
    
    <section id="contact">
        <h2>Contact</h2>
        <p>Neem contact met ons op via info@beglitterderozen.nl</p>
    </section>
    
    <section id="shop">
        <h2>Winkel</h2>
        <div class="product">
            <img src="images/rozen_foto.jpg" alt="Prachtige beglitterde rozen">
            <h3>Beglitterde Roos</h3>
            <p class="price">€10</p>
            <button class="add-to-cart">Voeg toe aan winkelmandje</button>
        </div>
    </section>
    
    <section id="cart">
        <h2>Winkelmandje</h2>
        <ul id="cart-items"></ul>
        <p id="cart-total">Totaal: €0</p>
        <button id="checkout">Afrekenen</button>
    </section>

    <script>
        // Winkelmandje functionaliteit
        const addToCartButtons = document.querySelectorAll('.add-to-cart');
        const cartItems = document.getElementById('cart-items');
        const cartTotal = document.getElementById('cart-total');
        const checkoutButton = document.getElementById('checkout');
        let total = 0;

        addToCartButtons.forEach(button => {
            button.addEventListener('click', () => {
                const product = button.parentNode;
                const productName = product.querySelector('h3').innerText;
                const productPrice = parseFloat(product.querySelector('.price').innerText.replace('€', ''));
                total += productPrice;

                const listItem = document.createElement('li');
                listItem.classList.add('cart-item');
                listItem.innerText = `${productName} - €${productPrice.toFixed(2)}`;
                cartItems.appendChild(listItem);

                cartTotal.innerText = `Totaal: €${total.toFixed(2)}`;
            });
        });

        checkoutButton.addEventListener('click', () => {
            window.location.href = 'checkout.html';
        });
    </script>
</body>
</html>
<!DOCTYPE html>
<html lang="nl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Afrekenen - Beglitterde Rozen</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <header>
        <img src="https://i.ibb.co/dmLbh1k/roses-logo.png" alt="Logo van Beglitterde Rozen" class="logo">
        <h1>Afrekenen</h1>
    </header>

    <section id="checkout-form">
        <h2>Betaalgegevens</h2>
        <form action="verwerk_betaling.php" method="POST">
            <div class="form-group">
                <label for="name">Naam:</label>
                <input type="text" id="name" name="name" required>
            </div>
            <div class="form-group">
                <label for="address">Adres:</label>
                <input type="text" id="address" name="address" required>
            </div>
            <div class="form-group">
                <label for="city">Stad:</label>
                <input type="text" id="city" name="city" required>
            </div>
            <div class="form-group">
                <label for="zip">Postcode:</label>
                <input type="text" id="zip" name="zip" required>
            </div>
            <div class="form-group">
                <label for="country">Land:</label>
                <input type="text" id="country" name="country" required>
            </div>
            <div class="form-group">
                <label for="card">Creditcardnummer:</label>
                <input type="text" id="card" name="card" required>
            </div>
            <div class="form-group">
                <label for="expiry">Vervaldatum:</label>
                <input type="text" id="expiry" name="expiry" required>
            </div>
            <div class="form-group">
                <label for="cvv">CVV:</label>
                <input type="text" id="cvv" name="cvv" required>
            </div>
            <input type="submit" value="Betalen">
        </form>
    </section>
</body>
</html>
*CSS
body {
    font-family: Arial, sans-serif;
    margin: 0;
    padding: 0;
    background-color: #FADADD; /* Baby roze achtergrondkleur */
    color: #333;
}

header {
    background-color: rgba(0, 0, 0, 0.5); /* Transparante achtergrond voor betere leesbaarheid */
    padding: 20px;
    text-align: center;
    position: relative;
}

.logo {
    width: 200px; /* Pas de grootte van het logo aan */
    height: auto; /* Zorgt ervoor dat de verhouding van het logo behouden blijft */
}

nav ul {
    list-style-type: none;
    padding: 0;
    margin: 0;
    display: flex;
    justify-content: center;
    margin-top: 50px; /* Zorg dat het menu onder het logo komt */
}

nav ul li {
    margin: 0 15px;
}

nav ul li a {
    text-decoration: none;
    color: #fff; /* Maak de links wit */
}

section {
    background-color: rgba(0, 0, 0, 0.1); /* Transparante achtergrond voor betere leesbaarheid */
    padding: 20px;
    margin: 20px;
    border-radius: 10px; /* Ronde hoeken voor een zachtere uitstraling */
}

#roses img, .product img {
    width: 25%;
    height: auto;
    border-radius: 10px; /* Ronde hoeken voor de afbeelding */
}

#quizForm {
    margin-top: 20px;
}

#result {
    margin-top: 20px;
    font-weight: bold;
}

#shop {
    text-align: center;
}

.product {
    display: inline-block;
    margin: 20px;
    padding: 10px;
    border: 1px solid #ccc;
    border-radius: 5px;
    background-color: #f9f9f9;
}

.product h3 {
    margin-top: 10px;
}

.price {
    font-weight: bold;
}

.add-to-cart {
    background-color: #4CAF50;
    color: white;
    padding: 8px 14px;
    border: none;
    border-radius: 5px;
    cursor: pointer;
}

#cart {
    margin-top: 20px;
    border: 1px solid #ccc;
    border-radius: 5px;
    padding: 10px;
}

#cart h2 {
    margin-bottom: 10px;
}

#cart-items {
    list-style-type: none;
    padding: 0;
}

.cart-item {
    margin-bottom: 5px;
}

#cart-total {
    font-weight: bold;
}

#checkout {
    background-color: #FF5733;
    color: white;
    padding: 10px 20px;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    margin-top: 10px;
}


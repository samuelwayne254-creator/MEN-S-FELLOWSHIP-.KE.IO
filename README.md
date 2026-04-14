# MEN-S-FELLOWSHIP-.KE.IO
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Cadets Men Fellowship</title>

<style>
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: Arial, sans-serif;
    scroll-behavior: smooth;
}

body {
    line-height: 1.6;
}

/* NAVBAR */
header {
    background: rgba(0,0,0,0.85);
    color: #fff;
    padding: 15px 40px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    position: sticky;
    top: 0;
}

nav a {
    color: #fff;
    margin-left: 20px;
    text-decoration: none;
}

/* HERO */
.hero {
    height: 100vh;
    background: linear-gradient(rgba(0,0,0,0.6), rgba(0,0,0,0.6)),
                url('https://images.unsplash.com/photo-1529070538774-1843cb3265df');
    background-size: cover;
    background-position: center;
    color: white;
    display: flex;
    justify-content: center;
    align-items: center;
    text-align: center;
}

.hero h2 {
    font-size: 48px;
    animation: fadeInDown 1.5s ease;
}

.hero p {
    margin: 20px 0;
    animation: fadeInUp 1.5s ease;
}

.btn {
    background: #f4a261;
    color: white;
    padding: 12px 25px;
    border: none;
    border-radius: 5px;
    cursor: pointer;
}

.btn:hover {
    transform: scale(1.1);
}

/* FEATURES */
.features {
    padding: 60px 20px;
    text-align: center;
}

.feature-box {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
}

.card {
    background: #f4f4f4;
    margin: 15px;
    padding: 20px;
    width: 250px;
    border-radius: 10px;
    opacity: 0;
    transform: translateY(40px);
    transition: 0.4s;
}

.card.show {
    opacity: 1;
    transform: translateY(0);
}

/* SIGNUP */
.signup {
    padding: 60px 20px;
    text-align: center;
    background: #f9f9f9;
}

.signup form {
    max-width: 400px;
    margin: auto;
    display: flex;
    flex-direction: column;
}

.signup input {
    padding: 12px;
    margin: 10px 0;
}

#successMsg {
    color: green;
    display: none;
}

/* WHATSAPP */
.whatsapp-btn {
    position: fixed;
    bottom: 20px;
    right: 20px;
    background: #25D366;
    color: white;
    font-size: 24px;
    padding: 15px;
    border-radius: 50%;
    text-decoration: none;
}

/* FOOTER */
footer {
    background: #111;
    color: white;
    text-align: center;
    padding: 20px;
}

/* ANIMATIONS */
@keyframes fadeInDown {
    from {opacity: 0; transform: translateY(-50px);}
    to {opacity: 1;}
}

@keyframes fadeInUp {
    from {opacity: 0; transform: translateY(50px);}
    to {opacity: 1;}
}

/* RESPONSIVE */
@media (max-width: 768px) {
    header {
        flex-direction: column;
    }

    .hero h2 {
        font-size: 30px;
    }
}
</style>
</head>

<body>

<header>
    <h1>Cadets Men Fellowship</h1>
    <nav>
        <a href="#">Home</a>
        <a href="#features">Mission</a>
        <a href="#signup">Join</a>
    </nav>
</header>

<section class="hero">
    <div>
        <h2>Building Strong Men of Purpose</h2>
        <p>Faith • Discipline • Brotherhood</p>
        <button class="btn">Join Us</button>
    </div>
</section>

<section class="features" id="features">
    <h3>Our Mission</h3>
    <div class="feature-box">
        <div class="card"><h4>Brotherhood</h4></div>
        <div class="card"><h4>Discipline</h4></div>
        <div class="card"><h4>Faith</h4></div>
    </div>
</section>

<!-- SIGNUP -->
<section class="signup" id="signup">
    <h3>Join Cadets Men Fellowship</h3>

    <form id="signupForm">
        <input type="text" id="name" placeholder="Full Name" required>
        <input type="email" id="email" placeholder="Email" required>
        <input type="tel" id="phone" placeholder="Phone" required>
        <button type="submit" class="btn">Sign Up</button>
    </form>

    <p id="successMsg">✅ Successfully joined!</p>
</section>

<!-- LOGIN -->
<section class="signup">
    <h3>Member Login</h3>

    <form id="loginForm">
        <input type="email" id="loginEmail" placeholder="Email" required>
        <input type="password" id="loginPassword" placeholder="Password" required>
        <button class="btn">Login</button>
    </form>

    <p id="loginMsg"></p>
</section>

<footer>
    <p>© 2026 Cadets Men Fellowship</p>
</footer>

<!-- WhatsApp Button -->
<a href="https://wa.me/254782141192" class="whatsapp-btn" target="_blank">💬</a>

<script>
// SCROLL ANIMATION
const cards = document.querySelectorAll('.card');
window.addEventListener('scroll', () => {
    cards.forEach(card => {
        if (card.getBoundingClientRect().top < window.innerHeight - 50) {
            card.classList.add('show');
        }
    });
});

// SIGNUP → GOOGLE SHEETS
document.getElementById("signupForm").addEventListener("submit", async function(e) {
    e.preventDefault();

    let name = name.value;
    let email = email.value;
    let phone = phone.value;

    try {
        await fetch("YOUR_GOOGLE_SCRIPT_URL_HERE", {
            method: "POST",
            body: JSON.stringify({ name, email, phone })
        });

        document.getElementById("successMsg").style.display = "block";
        signupForm.reset();

    } catch {
        alert("Error submitting form");
    }
});

// LOGIN (DEMO)
document.getElementById("loginForm").addEventListener("submit", function(e) {
    e.preventDefault();

    let email = loginEmail.value;
    let password = loginPassword.value;

    let msg = document.getElementById("loginMsg");

    if (email === "admin@cadets.com" && password === "1234") {
        msg.innerText = "✅ Login successful";
        msg.style.color = "green";
    } else {
        msg.innerText = "❌ Invalid details";
        msg.style.color = "red";
    }
});
</script>

</body>
</html>

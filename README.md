 <!DOCTYPE html><html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Romen Jerseys - Premium Custom Jerseys</title>
  <meta name="description" content="Order premium retro, full sleeves and collar jerseys via WhatsApp from Romen Jerseys. Fast delivery, great quality." />
  <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;600&display=swap" rel="stylesheet" />
  <link rel="icon" href="romenlogo.png" type="image/png">
  <style>
    * { margin: 0; padding: 0; box-sizing: border-box; font-family: 'Poppins', sans-serif; }
    body { background-color: #f5f5f5; color: #333; scroll-behavior: smooth; }
    header { background-color: #111; padding: 1rem 2rem; display: flex; align-items: center; justify-content: space-between; }
    .logo { height: 50px; border-radius: 50%; border: 2px solid white; }
    .title { color: #fff; font-size: 1.5rem; font-weight: 600; }
    .collections, .jersey-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(250px, 1fr)); gap: 2rem; padding: 2rem; }
    .collection-card, .jersey-card { background-color: #fff; border-radius: 10px; overflow: hidden; box-shadow: 0 4px 10px rgba(0,0,0,0.1); text-align: center; text-decoration: none; color: inherit; cursor: pointer; transition: transform 0.3s ease; }
    .collection-card:hover, .jersey-card:hover { transform: translateY(-5px); }
    .collection-card img, .jersey-card img { width: 100%; height: 200px; object-fit: cover; }
    .collection-card h3, .jersey-card h3 { padding: 1rem; font-size: 1.2rem; background-color: #eee; margin: 0; }
    .hidden { display: none; }
    .status { display: inline-block; padding: 0.4rem 0.8rem; margin-top: 1rem; border-radius: 20px; font-size: 0.9rem; font-weight: 500; }
    .restocked { background-color: #d4edda; color: #155724; }
    .out { background-color: #f8d7da; color: #721c24; }
    .order-btn { margin: 1rem 0; padding: 0.6rem 1.2rem; background-color: #111; color: #fff; border: none; border-radius: 5px; font-size: 0.95rem; cursor: pointer; }
    .jersey-card[data-status="out"] .order-btn { display: none; }
    form { max-width: 600px; margin: 2rem auto; background: #fff; padding: 2rem; border-radius: 10px; box-shadow: 0 4px 10px rgba(0,0,0,0.1); }
    form h2 { text-align: center; margin-bottom: 1.5rem; }
    label { display: block; margin: 0.5rem 0 0.2rem; font-weight: 500; }
    input, textarea { width: 100%; padding: 0.8rem; border: 1px solid #ccc; border-radius: 5px; margin-bottom: 1rem; font-size: 1rem; }
    .nav-btn { position: fixed; top: 1rem; right: 1rem; background: #333; color: white; border: none; padding: 0.6rem 1rem; border-radius: 5px; cursor: pointer; z-index: 999; display: none; }
    #success-message { display: none; text-align: center; margin-top: 1rem; color: green; font-weight: 600; }
    .footer { background: #111; color: white; text-align: center; padding: 1rem; font-size: 0.9rem; }
    .footer a { color: #ccc; text-decoration: none; }
    .floating-instagram { position: fixed; bottom: 1rem; left: 1rem; background: #E4405F; color: white; border-radius: 50%; padding: 0.8rem; text-align: center; font-size: 1.2rem; z-index: 999; text-decoration: none; }
    .testimonial { background: white; padding: 1rem; border-radius: 8px; margin: 1rem auto; max-width: 600px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); }
    .testimonial h4 { margin-bottom: 0.5rem; font-weight: 600; }
    .top-btn { position: fixed; bottom: 1rem; right: 1rem; background: #111; color: white; border-radius: 50%; padding: 0.8rem 1rem; cursor: pointer; z-index: 999; font-size: 1.2rem; }
  </style>
</head>
<body>
  <header>
    <img src="romenlogo.png" alt="Romen Jerseys Logo" class="logo" />
    <div class="title">ROMEN JERSEYS</div>
  </header>

  <section id="home">
    <div class="collections">
      <div class="collection-card" onclick="showJerseyCollection('retro')">
        <img src="retro.png" alt="Retro Collection" />
        <h3>Retro Collection</h3>
      </div>
      <div class="collection-card" onclick="showJerseyCollection('fullsleeves')">
        <img src="sleeves.png" alt="Full Sleeves" />
        <h3>Full Sleeves</h3>
      </div>
      <div class="collection-card" onclick="showJerseyCollection('collar')">
        <img src="collar.png" alt="Collar Jersey" />
        <h3>Collar Jersey</h3>
      </div>
    </div>
  </section>

  <section id="jerseys" class="hidden">
    <h2 style="text-align:center; margin-top:2rem;">Jersey Collection</h2>
    <button class="nav-btn" onclick="showPage('home')">🏠 Home</button>
    <div class="jersey-grid" id="jerseyGrid"></div>
  </section>

  <section id="order" class="hidden">
    <button class="nav-btn" onclick="showPage('jerseys')">← Back to Jerseys</button>
    <form id="orderForm">
      <h2>Order Your Jersey</h2>
      <p><strong>Selected Jersey:</strong> <span id="jersey-name"></span></p>
      <label for="name">Name</label>
      <input type="text" id="name" name="name" required />

      <label for="phone">Phone Number</label>
      <input type="tel" id="phone" name="phone" required />

      <label for="address">Address</label>
      <textarea id="address" name="address" rows="3" required></textarea>

      <label for="pincode">Pincode</label>
      <input type="text" id="pincode" name="pincode" required />

      <label for="request">Any Special Request (Optional)</label>
      <textarea id="request" name="request" rows="2"></textarea>

      <div style="font-size: 0.9rem; color: #555; margin-bottom: 1rem;">⏳ Estimated Delivery: 7–9 working days</div>

      <button type="submit" class="order-btn">Submit Order</button>
    </form>
    <div id="success-message">✅ Your order has been placed! You’ll receive details via WhatsApp.</div>
  </section>

  <section class="testimonial">
    <h4>⭐ Customer Reviews</h4>
    <p>"Amazing quality and fast delivery! Highly recommend."</p>
    <p>"Customer service is excellent. Will order again."</p>
    <p>"Got my jersey in 8 days. Looks premium and fits well."</p>
  </section>

  <div class="footer">
    &copy; 2025 Romen Jerseys | <a href="mailto:support.romenjerseys@gmail.com">support.romenjerseys@gmail.com</a>
  </div>

  <a href="https://instagram.com/romen_jerseys?igsh=a3drem1naHpiNGwx" class="floating-instagram" target="_blank">📸</a>
  <div class="top-btn" onclick="window.scrollTo({top: 0, behavior: 'smooth'})">↑</div>

  <script>
    const jerseyData = {
      retro: [
        {filename: "jerseyretro1.png", name: "Retro Jersey 1", status: "restocked"},
        {filename: "jerseyretro2.png", name: "Retro Jersey 2", status: "restocked"},
        {filename: "jerseyretro3.png", name: "Retro Jersey 3", status: "out"},
      ],
      fullsleeves: [
        {filename: "jerseyfullsleeves1.png", name: "Full Sleeves Jersey 1", status: "restocked"},
        {filename: "jerseyfullsleeves2.png", name: "Full Sleeves Jersey 2", status: "restocked"},
        {filename: "jerseyfullsleeves3.png", name: "Full Sleeves Jersey 3", status: "out"},
      ],
      collar: [
        {filename: "collarjersey1.png", name: "Collar Jersey 1", status: "restocked"},
        {filename: "collarjersey2.png", name: "Collar Jersey 2", status: "restocked"},
        {filename: "collarjersey3.png", name: "Collar Jersey 3", status: "out"},
      ]
    };

    function showPage(pageId) {
      document.getElementById("home").classList.add("hidden");
      document.getElementById("jerseys").classList.add("hidden");
      document.getElementById("order").classList.add("hidden");
      document.querySelectorAll(".nav-btn").forEach(btn => btn.style.display = "none");
      document.getElementById(pageId).classList.remove("hidden");
      if (pageId === "jerseys" || pageId === "order") {
        document.querySelector(".nav-btn").style.display = "block";
      }
      window.scrollTo(0, 0);
    }

    function showJerseyCollection(type) {
      const container = document.getElementById("jerseyGrid");
      container.innerHTML = "";

      jerseyData[type].forEach(jersey => {
        const card = document.createElement("div");
        card.className = "jersey-card";
        card.setAttribute("data-status", jersey.status);

        let stockLabel = jersey.status === "restocked"
          ? `<span class="status restocked">Restocked</span>`
          : `<span class="status out">Out of Stock</span>`;

        let orderBtn = jersey.status === "restocked"
          ? `<button class="order-btn">Order Now</button>`
          : "";

        card.innerHTML = `
          <img src="${jersey.filename}" alt="${jersey.name}">
          <h3>${jersey.name}</h3>
          ${stockLabel}
          ${orderBtn}
        `;

        if (jersey.status === "restocked") {
          card.querySelector("button").addEventListener("click", () => {
            showOrderForm(jersey.filename);
          });
        }

        container.appendChild(card);
      });
      showPage("jerseys");
    }

    function showOrderForm(jerseyFilename) {
      document.getElementById("jersey-name").textContent = jerseyFilename;
      document.getElementById("success-message").style.display = "none";
      showPage("order");
    }

    document.getElementById("orderForm").addEventListener("submit", function(e) {
      e.preventDefault();

      const jersey = document.getElementById("jersey-name").textContent || "Not specified";
      const name = document.getElementById("name").value.trim();
      const phone = document.getElementById("phone").value.trim();
      const address = document.getElementById("address").value.trim();
      const pincode = document.getElementById("pincode").value.trim();
      const request = document.getElementById("request").value.trim();
      const whatsappNumber = "917418825345";
      const orderId = "ROMEN" + Math.floor(Math.random() * 90000 + 10000);

      const message =
`🧾 *Romen Jerseys Order*

📦 Order ID: ${orderId}
👕 Jersey: ${jersey}
👤 Name: ${name}
📞 Phone: ${phone}
🏠 Address: ${address}
📮 Pincode: ${pincode}
📝 Special Request: ${request || 'None'}

⏳ Delivery: 7–9 working days.`;

      document.getElementById("success-message").style.display = "block";

      setTimeout(() => {
        const url = `https://wa.me/${whatsappNumber}?text=${encodeURIComponent(message)}`;
        window.open(url, "_blank");
      }, 2000);
    });

    showPage("home");
  </script>
</body>
</html>

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Romen Jerseys</title>
  <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;600&display=swap" rel="stylesheet" />
  <style>
    * {
      margin: 0; padding: 0; box-sizing: border-box;
      font-family: 'Poppins', sans-serif;
    }

    body {
      background-color: #f5f5f5;
      color: #333;
      padding: 0;
    }

    header {
      background-color: #111;
      padding: 1rem 2rem;
      display: flex;
      align-items: center;
      justify-content: space-between;
    }

    .logo {
      height: 50px;
    }

    .title {
      color: #fff;
      font-size: 1.5rem;
      font-weight: 600;
    }

    .collections, .jersey-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
      gap: 2rem;
      padding: 2rem;
    }

    .collection-card, .jersey-card {
      background-color: #fff;
      border-radius: 10px;
      overflow: hidden;
      box-shadow: 0 4px 10px rgba(0,0,0,0.1);
      text-align: center;
      text-decoration: none;
      color: inherit;
      cursor: pointer;
      transition: transform 0.3s ease;
      user-select: none;
    }

    .collection-card:hover, .jersey-card:hover {
      transform: translateY(-5px);
    }

    .collection-card img, .jersey-card img {
      width: 100%;
      height: 200px;
      object-fit: cover;
    }

    .collection-card h3, .jersey-card h3 {
      padding: 1rem;
      font-size: 1.2rem;
      background-color: #eee;
      margin: 0;
    }

    .hidden {
      display: none;
    }

    .status {
      display: inline-block;
      padding: 0.4rem 0.8rem;
      margin-top: 1rem;
      border-radius: 20px;
      font-size: 0.9rem;
      font-weight: 500;
    }

    .restocked {
      background-color: #d4edda;
      color: #155724;
    }

    .out {
      background-color: #f8d7da;
      color: #721c24;
    }

    .order-btn {
      margin: 1rem 0;
      padding: 0.6rem 1.2rem;
      background-color: #111;
      color: #fff;
      border: none;
      border-radius: 5px;
      font-size: 0.95rem;
      cursor: pointer;
      text-decoration: none;
      display: inline-block;
    }

    .jersey-card[data-status="out"] .order-btn {
      display: none;
    }

    form {
      max-width: 600px;
      margin: 2rem auto;
      background: #fff;
      padding: 2rem;
      border-radius: 10px;
      box-shadow: 0 4px 10px rgba(0,0,0,0.1);
    }

    form h2 {
      text-align: center;
      margin-bottom: 1.5rem;
    }

    label {
      display: block;
      margin: 0.5rem 0 0.2rem;
      font-weight: 500;
    }

    input, textarea {
      width: 100%;
      padding: 0.8rem;
      border: 1px solid #ccc;
      border-radius: 5px;
      margin-bottom: 1rem;
      font-size: 1rem;
      resize: vertical;
    }

    .nav-btn {
      position: fixed;
      top: 1rem;
      right: 1rem;
      background: #333;
      color: white;
      border: none;
      padding: 0.6rem 1rem;
      border-radius: 5px;
      cursor: pointer;
      z-index: 999;
      display: none;
    }
  </style>
</head>
<body>

  <!-- HEADER -->
  <header>
    <img src="romenlogo.png" alt="Romen Jerseys Logo" class="logo" />
    <div class="title">ROMEN JERSEYS</div>
  </header>

  <!-- HOME PAGE -->
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

  <!-- JERSEY COLLECTION PAGE -->
  <section id="jerseys" class="hidden">
    <h2 style="text-align:center; margin-top:2rem;">Jersey Collection</h2>
    <button class="nav-btn" onclick="showPage('home')">🏠 Home</button>
    <div class="jersey-grid" id="jerseyGrid">
      <!-- Jerseys inserted by JS -->
    </div>
  </section>

  <!-- ORDER FORM PAGE -->
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

      <button type="submit" class="order-btn">Submit Order</button>
    </form>
  </section>

  <script>
    // Data for jerseys
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

    // Show page and hide others
    function showPage(pageId) {
      document.getElementById("home").classList.add("hidden");
      document.getElementById("jerseys").classList.add("hidden");
      document.getElementById("order").classList.add("hidden");
      document.querySelectorAll(".nav-btn").forEach(btn => btn.style.display = "none");

      document.getElementById(pageId).classList.remove("hidden");

      // Show nav buttons conditionally
      if(pageId === "jerseys" || pageId === "order") {
        document.querySelector(".nav-btn").style.display = "block";
      }
      window.scrollTo(0,0);
    }

    // Show jersey collection by type
    function showJerseyCollection(type) {
      const container = document.getElementById("jerseyGrid");
      container.innerHTML = ""; // clear

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

        if(jersey.status === "restocked") {
          card.querySelector("button").addEventListener("click", () => {
            showOrderForm(jersey.filename);
          });
        }
        container.appendChild(card);
      });

      showPage("jerseys");
    }

    // Show order form with selected jersey filename
    function showOrderForm(jerseyFilename) {
      document.getElementById("jersey-name").textContent = jerseyFilename;
      showPage("order");
    }

    // WhatsApp order submission
    document.getElementById("orderForm").addEventListener("submit", function(e) {
      e.preventDefault();

      const jersey = document.getElementById("jersey-name").textContent || "Not specified";
      const name = document.getElementById("name").value.trim();
      const phone = document.getElementById("phone").value.trim();
      const address = document.getElementById("address").value.trim();
      const pincode = document.getElementById("pincode").value.trim();
      const request = document.getElementById("request").value.trim();

      const whatsappNumber = "917418825345";

      const message =
`New Jersey Order:
Jersey: ${jersey}
Name: ${name}
Phone: ${phone}
Address: ${address}
Pincode: ${pincode}
Special Request: ${request || 'None'}`;

      const url = `https://wa.me/${whatsappNumber}?text=${encodeURIComponent(message)}`;
      window.open(url, "_blank");
    });

    // Initially show home page
    showPage("home");
  </script>

</body>
</html>

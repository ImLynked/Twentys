<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Twenty's Auto Body</title>
  <style>
    /* BASIC RESET */
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    /* PAGE BACKGROUND */
    body {
      font-family: Arial, sans-serif;
      background-color: #f0f3f9; /* Light grayish background from screenshot */
      color: #000;
    }

    /* TOP HEADER BAR */
    header {
      background-color: #10182b; /* Dark navy bar at top */
      padding: 20px;
      text-align: center;
    }
    header h1 {
      color: #fff;
      font-size: 24px;
    }

    /* MAIN WRAPPER FOR COLUMNS */
    .columns-container {
      display: flex;
      justify-content: space-around;
      align-items: flex-start;
      padding: 20px 40px;
      gap: 20px; /* space between columns */
    }

    /* COLUMN STYLES */
    .column {
      background-color: #fff;
      border: 1px solid #ccc;
      border-radius: 5px;
      padding: 15px;
      min-width: 250px;
    }
    .column h2 {
      text-align: center;
      margin-bottom: 10px;
      font-size: 1.2rem;
    }

    /* COSMETICS GRID (left column) */
    .cosmetics-grid {
      display: grid;
      grid-template-columns: repeat(3, 1fr); /* 3 columns of cosmetic buttons */
      gap: 10px;
    }

    /* PERFORMANCE GRID (center column):
       We'll create sections for each category: Turbo, Armor, etc. */
    .performance-section {
      margin-bottom: 20px;
    }
    .performance-section h3 {
      text-align: center;
      margin-bottom: 8px;
      font-size: 1rem;
    }
    .levels {
      display: grid;
      grid-template-columns: repeat(4, 1fr); /* 4 level buttons */
      gap: 5px;
    }

    /* RESPRAY GRID (right column) */
    .respray-grid {
      display: grid;
      grid-template-columns: 1fr;
      gap: 10px;
    }

    /* BUTTON STYLES */
    .upgrade-btn {
      background-color: #e3e9f2;
      border: 1px solid #ccc;
      border-radius: 3px;
      padding: 8px;
      text-align: center;
      cursor: pointer;
      font-size: 0.85rem;
      transition: background 0.3s;
    }
    .upgrade-btn:hover {
      background-color: #d1d8e2;
    }

    /* SELECTED UPGRADES & TOTAL (centered under Performance column) */
    #selected-upgrades-container {
      text-align: center;
      margin-top: 20px;
      margin-bottom: 20px;
    }
    #selected-upgrades {
      list-style: none;
      margin: 10px auto;
      padding-left: 0;
      max-width: 500px;
      max-height: 150px;
      overflow-y: auto;
    }
    #selected-upgrades li {
      background-color: #e3e9f2;
      margin: 5px 0;
      padding: 5px;
      border-radius: 3px;
      cursor: pointer;
    }
    #selected-upgrades li:hover {
      background-color: #d1d8e2;
    }
    #total-price {
      font-weight: bold;
      color: #000;
      font-size: 1.1rem;
    }
    .reset-btn {
      margin-top: 10px;
      padding: 8px 16px;
      background: #ccc;
      border: none;
      border-radius: 3px;
      cursor: pointer;
    }
    .reset-btn:hover {
      background: #bbb;
    }

    /* CUSTOMER FORM & SUMMARY */
    .form-section {
      text-align: center;
      margin-bottom: 20px;
    }
    .form-row {
      margin: 10px 0;
    }
    .form-row label {
      display: inline-block;
      width: 150px;
      text-align: right;
      margin-right: 5px;
    }
    .form-row input {
      width: 200px;
      padding: 5px;
      border: 1px solid #999;
      border-radius: 3px;
    }
    .generate-btn {
      margin-top: 10px;
      padding: 8px 16px;
      background: #007bff;
      border: none;
      border-radius: 3px;
      cursor: pointer;
      color: #fff;
      font-size: 1rem;
    }
    .generate-btn:hover {
      background: #0056c1;
    }
    #summaryOutput {
      margin: 15px auto 0;
      background-color: #e3e9f2;
      padding: 10px;
      border-radius: 5px;
      border: 1px solid #ccc;
      max-width: 500px;
      text-align: left;
      white-space: pre-wrap;
    }
  </style>
</head>
<body>

  <header>
    <h1>Twenty's Auto Body</h1>
  </header>

  <!-- 3-COLUMN LAYOUT -->
  <div class="columns-container">

    <!-- LEFT COLUMN: COSMETICS -->
    <div class="column">
      <h2>Cosmetics</h2>
      <!-- Example set of cosmetics, each $500 -->
      <div class="cosmetics-grid">
        <button class="upgrade-btn" onclick="addUpgrade('Aerial', 500)">Aerial<br>$500</button>
        <button class="upgrade-btn" onclick="addUpgrade('Air Filter', 500)">Air Filter<br>$500</button>
        <button class="upgrade-btn" onclick="addUpgrade('Door Speaker', 500)">Door Speaker<br>$500</button>
        <button class="upgrade-btn" onclick="addUpgrade('Custom Trim', 500)">Custom Trim<br>$500</button>
        <button class="upgrade-btn" onclick="addUpgrade('Dashboard', 500)">Dashboard<br>$500</button>

        <button class="upgrade-btn" onclick="addUpgrade('Engine Block', 500)">Engine Block<br>$500</button>
        <button class="upgrade-btn" onclick="addUpgrade('Exhaust', 500)">Exhaust<br>$500</button>
        <button class="upgrade-btn" onclick="addUpgrade('Grille', 500)">Grille<br>$500</button>
        <button class="upgrade-btn" onclick="addUpgrade('Hood', 500)">Hood<br>$500</button>
        <button class="upgrade-btn" onclick="addUpgrade('Horn', 500)">Horn<br>$500</button>

        <button class="upgrade-btn" onclick="addUpgrade('Lights', 500)">Lights<br>$500</button>
        <button class="upgrade-btn" onclick="addUpgrade('Livery', 500)">Livery<br>$500</button>
        <button class="upgrade-btn" onclick="addUpgrade('Mirrors', 500)">Mirrors<br>$500</button>
        <button class="upgrade-btn" onclick="addUpgrade('Ornaments', 500)">Ornaments<br>$500</button>
        <button class="upgrade-btn" onclick="addUpgrade('Plate', 500)">Plate<br>$500</button>

        <button class="upgrade-btn" onclick="addUpgrade('Rear Bumper', 500)">Rear Bumper<br>$500</button>
        <button class="upgrade-btn" onclick="addUpgrade('Roof', 500)">Roof<br>$500</button>
        <button class="upgrade-btn" onclick="addUpgrade('Seat', 500)">Seat<br>$500</button>
        <button class="upgrade-btn" onclick="addUpgrade('Shift Knob', 500)">Shift Knob<br>$500</button>
        <button class="upgrade-btn" onclick="addUpgrade('Speaker', 500)">Speaker<br>$500</button>

        <button class="upgrade-btn" onclick="addUpgrade('Spoiler', 500)">Spoiler<br>$500</button>
        <button class="upgrade-btn" onclick="addUpgrade('Sun Strip', 500)">Sun Strip<br>$500</button>
        <button class="upgrade-btn" onclick="addUpgrade('Vanity Plate', 500)">Vanity Plate<br>$500</button>
        <button class="upgrade-btn" onclick="addUpgrade('Window Tints', 500)">Window Tints<br>$500</button>
        <button class="upgrade-btn" onclick="addUpgrade('Side Skirts', 500)">Side Skirts<br>$500</button>
        <!-- Add or remove cosmetics as needed -->
      </div>
    </div>

    <!-- MIDDLE COLUMN: PERFORMANCE -->
    <div class="column">
      <h2>Performance</h2>

      <!-- Each category with 4 levels (example pricing from your screenshot) -->
      <div class="performance-section">
        <h3>Turbo</h3>
        <div class="levels">
          <button class="upgrade-btn" onclick="addUpgrade('Turbo Level 1', 1000)">Level 1<br>$1,000</button>
          <button class="upgrade-btn" onclick="addUpgrade('Turbo Level 2', 3500)">Level 2<br>$3,500</button>
          <button class="upgrade-btn" onclick="addUpgrade('Turbo Level 3', 6500)">Level 3<br>$6,500</button>
          <button class="upgrade-btn" onclick="addUpgrade('Turbo Level 4', 10450)">Level 4<br>$10,450</button>
        </div>
      </div>

      <div class="performance-section">
        <h3>Armor</h3>
        <div class="levels">
          <button class="upgrade-btn" onclick="addUpgrade('Armor Level 1', 2000)">Level 1<br>$2,000</button>
          <button class="upgrade-btn" onclick="addUpgrade('Armor Level 2', 6500)">Level 2<br>$6,500</button>
          <button class="upgrade-btn" onclick="addUpgrade('Armor Level 3', 10450)">Level 3<br>$10,450</button>
          <button class="upgrade-btn" onclick="addUpgrade('Armor Level 4', 19500)">Level 4<br>$19,500</button>
        </div>
      </div>

      <div class="performance-section">
        <h3>Brakes</h3>
        <div class="levels">
          <button class="upgrade-btn" onclick="addUpgrade('Brakes Level 1', 1000)">Level 1<br>$1,000</button>
          <button class="upgrade-btn" onclick="addUpgrade('Brakes Level 2', 3500)">Level 2<br>$3,500</button>
          <button class="upgrade-btn" onclick="addUpgrade('Brakes Level 3', 6500)">Level 3<br>$6,500</button>
          <button class="upgrade-btn" onclick="addUpgrade('Brakes Level 4', 10450)">Level 4<br>$10,450</button>
        </div>
      </div>

      <div class="performance-section">
        <h3>Engine</h3>
        <div class="levels">
          <button class="upgrade-btn" onclick="addUpgrade('Engine Level 1', 1000)">Level 1<br>$1,000</button>
          <button class="upgrade-btn" onclick="addUpgrade('Engine Level 2', 3500)">Level 2<br>$3,500</button>
          <button class="upgrade-btn" onclick="addUpgrade('Engine Level 3', 6500)">Level 3<br>$6,500</button>
          <button class="upgrade-btn" onclick="addUpgrade('Engine Level 4', 19500)">Level 4<br>$19,500</button>
        </div>
      </div>

      <div class="performance-section">
        <h3>Suspension</h3>
        <div class="levels">
          <button class="upgrade-btn" onclick="addUpgrade('Suspension Level 1', 1000)">Level 1<br>$1,000</button>
          <button class="upgrade-btn" onclick="addUpgrade('Suspension Level 2', 3500)">Level 2<br>$3,500</button>
          <button class="upgrade-btn" onclick="addUpgrade('Suspension Level 3', 6500)">Level 3<br>$6,500</button>
          <button class="upgrade-btn" onclick="addUpgrade('Suspension Level 4', 10450)">Level 4<br>$10,450</button>
        </div>
      </div>

      <div class="performance-section">
        <h3>Transmission</h3>
        <div class="levels">
          <button class="upgrade-btn" onclick="addUpgrade('Transmission Level 1', 1000)">Level 1<br>$1,000</button>
          <button class="upgrade-btn" onclick="addUpgrade('Transmission Level 2', 3500)">Level 2<br>$3,500</button>
          <button class="upgrade-btn" onclick="addUpgrade('Transmission Level 3', 6500)">Level 3<br>$6,500</button>
          <button class="upgrade-btn" onclick="addUpgrade('Transmission Level 4', 14250)">Level 4<br>$14,250</button>
        </div>
      </div>
    </div><!-- end PERFORMANCE column -->

    <!-- RIGHT COLUMN: RESPRAY -->
    <div class="column">
      <h2>Respray</h2>
      <div class="respray-grid">
        <button class="upgrade-btn" onclick="addUpgrade('Primary Respray', 1100)">Primary<br>$1,100</button>
        <button class="upgrade-btn" onclick="addUpgrade('Secondary Respray', 1100)">Secondary<br>$1,100</button>
        <button class="upgrade-btn" onclick="addUpgrade('Pearlescent Respray', 600)">Pearlescent<br>$600</button>
        <button class="upgrade-btn" onclick="addUpgrade('Interior Respray', 200)">Interior<br>$200</button>
        <button class="upgrade-btn" onclick="addUpgrade('Dashboard Color', 100)">Dashboard<br>$100</button>
      </div>
    </div><!-- end RESPRAY column -->
  </div><!-- end columns-container -->

  <!-- SELECTED UPGRADES & TOTAL (centered) -->
  <div id="selected-upgrades-container">
    <h2>Selected Upgrades</h2>
    <ul id="selected-upgrades"></ul>
    <h3>Total Price: $<span id="total-price">0</span></h3>
    <button class="reset-btn" onclick="resetUpgrades()">Reset All</button>
  </div>

  <!-- CUSTOMER FORM & SUMMARY -->
  <div class="form-section">
    <h2>Customer Details</h2>
    <div class="form-row">
      <label for="customerName">Customer Name:</label>
      <input type="text" id="customerName" placeholder="Enter Customer Name" />
    </div>
    <div class="form-row">
      <label for="vehicle">Vehicle [Make/Model]:</label>
      <input type="text" id="vehicle" placeholder="Enter Make/Model" />
    </div>
    <div class="form-row">
      <label for="plate">Plate:</label>
      <input type="text" id="plate" placeholder="Enter Plate" />
    </div>

    <button class="generate-btn" onclick="generateSummary()">Generate Summary</button>
    <div id="summaryOutput"></div>
  </div>

  <script>
    let total = 0;
    let upgrades = [];

    // Add an upgrade to the list
    function addUpgrade(name, price) {
      upgrades.push({ name, price });
      total += price;
      renderUpgrades();
    }

    // Render the selected upgrades list + total
    function renderUpgrades() {
      const upgradesList = document.getElementById('selected-upgrades');
      upgradesList.innerHTML = '';

      upgrades.forEach((upgrade, index) => {
        const li = document.createElement('li');
        li.textContent = `${upgrade.name} - $${upgrade.price}`;
        // Click to remove
        li.addEventListener('click', () => removeUpgrade(index));
        upgradesList.appendChild(li);
      });

      document.getElementById('total-price').textContent = total;
    }

    // Remove an upgrade
    function removeUpgrade(index) {
      total -= upgrades[index].price;
      upgrades.splice(index, 1);
      renderUpgrades();
    }

    // Reset all
    function resetUpgrades() {
      total = 0;
      upgrades = [];
      renderUpgrades();
    }

    // Generate final summary
    function generateSummary() {
      const name = document.getElementById('customerName').value || "N/A";
      const vehicle = document.getElementById('vehicle').value || "N/A";
      const plate = document.getElementById('plate').value || "N/A";
      const upgradesPurchased = upgrades.map(u => u.name).join(', ') || "None";

      const summary =
`Customer Name: ${name}
Vehicle | [Make/Model]: ${vehicle}
Plate: ${plate}
Upgrades Purchased: ${upgradesPurchased}
Price Charged: $${total}
SHOP: Twenty's`;

      document.getElementById('summaryOutput').textContent = summary;
    }
  </script>

</body>
</html>

  <!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Green School Audit – Class 8-L</title>
  <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;600&display=swap" rel="stylesheet">
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }
    body {
      font-family: 'Poppins', sans-serif;
      background: linear-gradient(to right, #d0f0c0, #f0fff4);
      color: #2e7d32;
      padding: 20px;
    }
    nav {
      background: #2e7d32;
      color: white;
      padding: 15px;
      text-align: center;
      font-size: 20px;
      border-radius: 10px;
      margin-bottom: 20px;
    }
    section {
      margin-bottom: 30px;
      background: white;
      padding: 20px;
      border-radius: 12px;
      box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
    }
    h1, h2 {
      color: #1b5e20;
    }
    table, th, td {
      border: 1px solid #a5d6a7;
      border-collapse: collapse;
      padding: 10px;
      text-align: center;
    }
    table {
      width: 100%;
      margin-top: 10px;
    }
    input[type="text"], input[type="number"] {
      width: 100%;
      padding: 5px;
      border-radius: 5px;
    }
    input[type="checkbox"] {
      transform: scale(1.2);
    }
    .result {
      background: #c8e6c9;
      padding: 15px;
      border: 2px solid #66bb6a;
      border-radius: 10px;
      margin-top: 20px;
    }
    button {
      background-color: #388e3c;
      color: white;
      padding: 10px 20px;
      font-size: 16px;
      border: none;
      border-radius: 8px;
      cursor: pointer;
      box-shadow: 2px 2px 5px #81c784;
    }
    button:hover {
      background-color: #2e7d32;
    }
    footer {
      text-align: center;
      padding: 10px;
      margin-top: 30px;
      font-size: 14px;
      color: #4caf50;
    }
  </style>
</head>
<body>
  <nav>🌱 Green School Project – Class 8-L</nav>

  <section>
    <h1>Welcome to Our Eco-Friendly School Audit</h1>
    <p>We are Class 8-L and we are working to make our school more energy-efficient and eco-smart. This site helps us track and improve how resources are used in different areas of the school.</p>
  </section>

  <section>
    <h2>📋 Observation Entry</h2>
    <table id="observationTable">
      <tr>
        <th>Area</th>
        <th>Lights On?</th>
        <th>Fans On?</th>
        <th>AC On?</th>
        <th>Temperature (°C)</th>
        <th>Number of People</th>
        <th>Hours of Use</th>
        <th>In Use?</th>
        <th>Can Be Off?</th>
      </tr>
      <tr>
        <td><input type="text" value="Classroom 8A"></td>
        <td><input type="checkbox"></td>
        <td><input type="checkbox"></td>
        <td><input type="checkbox"></td>
        <td><input type="number" value="22"></td>
        <td><input type="number" value="30"></td>
        <td><input type="number" value="5"></td>
        <td><input type="checkbox"></td>
        <td><input type="checkbox"></td>
      </tr>
      <tr>
        <td><input type="text" value="Canteen"></td>
        <td><input type="checkbox"></td>
        <td><input type="checkbox"></td>
        <td><input type="checkbox"></td>
        <td><input type="number" value="25"></td>
        <td><input type="number" value="15"></td>
        <td><input type="number" value="4"></td>
        <td><input type="checkbox"></td>
        <td><input type="checkbox"></td>
      </tr>
      <tr>
        <td><input type="text" value="Library"></td>
        <td><input type="checkbox"></td>
        <td><input type="checkbox"></td>
        <td><input type="checkbox"></td>
        <td><input type="number" value="23"></td>
        <td><input type="number" value="10"></td>
        <td><input type="number" value="6"></td>
        <td><input type="checkbox"></td>
        <td><input type="checkbox"></td>
      </tr>
    </table>
    <button onclick="calculateAudit()">🔍 Calculate Energy Waste</button>
    <div class="result" id="summary"></div>
  </section>

  <section>
    <h2>📊 What We Learned</h2>
    <p>By checking each area, we learned where we waste electricity and how we can fix it by switching off unused fans and lights.</p>
    <ul>
      <li>💡 Use motion sensors in hallways</li>
      <li>🚿 Report leaky taps to reduce water waste</li>
      <li>📣 Create posters to remind everyone to save energy</li>
    </ul>
  </section>

  <footer>
    Made with 💚 by Class 8-L • Let's Make Our School Greener!
  </footer>

  <script>
    function calculateAudit() {
      const rows = document.querySelectorAll("#observationTable tr");
      let totalAreas = 0, unusedWithLights = 0, unusedWithAC = 0;

      rows.forEach((row, index) => {
        if (index === 0) return; // Skip header
        const cells = row.querySelectorAll("td input");
        if (cells.length !== 9) return;

        const lights = cells[1].checked;
        const fans = cells[2].checked;
        const ac = cells[3].checked;
        const inUse = cells[7].checked;

        totalAreas++;
        if ((lights || fans || ac) && !inUse) {
          unusedWithLights++;
        }

        if (ac && !inUse) {
          unusedWithAC++;
        }
      });

      const percentWasted = totalAreas ? ((unusedWithLights / totalAreas) * 100).toFixed(2) : 0;
      const percentACWaste = totalAreas ? ((unusedWithAC / totalAreas) * 100).toFixed(2) : 0;
      document.getElementById("summary").innerHTML =
        `<strong>Total Areas Checked:</strong> ${totalAreas}<br>
         <strong>Lights/Fans/AC On Without Use:</strong> ${unusedWithLights}<br>
         <strong>AC Wastage Rate:</strong> ${percentACWaste}%<br>
         <strong>Overall Energy Wastage Rate:</strong> ${percentWasted}%`;
    }
  </script>
</body>
</html>

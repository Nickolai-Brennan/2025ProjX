Here is a **Markdown version** of the full HTML/CSS UI design system, with fenced code blocks for clean formatting on GitHub, Notion, or project documentation.

---

# 🎨 UI Style Guide (Markdown Version)

## 🧱 Global CSS

```css
@import url('https://fonts.googleapis.com/css2?family=Barlow+Condensed:wght@600&family=Inter&display=swap');

body {
  background: #121212;
  color: #ffffff;
  font-family: 'Inter', sans-serif;
  font-size: 14px;
  line-height: 1.6;
  margin: 0;
  padding: 0;
}

h1, h2, h3 {
  font-family: 'Barlow Condensed', sans-serif;
  color: #f6b003;
  margin-bottom: 0.5em;
}

a {
  color: #03a9f4;
  text-decoration: none;
}

a:hover {
  text-decoration: underline;
}
```

---

## 📊 Table CSS

```css
.custom-table {
  width: 100%;
  border-collapse: collapse;
  background-color: #1f1f1f;
  color: #ffffff;
  font-size: 14px;
  border-radius: 12px;
  overflow: hidden;
  box-shadow: 0px 5px 15px rgba(0,0,0,0.4);
}

.custom-table thead {
  background-color: #f6b003;
  color: #121212;
  font-family: 'Barlow Condensed', sans-serif;
  text-transform: uppercase;
}

.custom-table th, .custom-table td {
  padding: 12px 16px;
  text-align: left;
}

.custom-table tr:nth-child(even) {
  background-color: #222222;
}

.custom-table tr:hover {
  background-color: #2e2e2e;
  cursor: pointer;
}
```

---

## 🃏 Card CSS

```css
.card {
  background: #1f1f1f;
  border-radius: 18px;
  padding: 20px;
  box-shadow: 0 10px 25px rgba(0, 0, 0, 0.5);
  transition: all 0.3s ease;
}

.card:hover {
  box-shadow: 0 14px 35px rgba(0, 0, 0, 0.6);
  background: #2a2a2a;
}
```

---

## 🟨 Badge Styles

```css
.badge {
  display: inline-block;
  font-weight: 600;
  padding: 4px 10px;
  border-radius: 999px;
  font-size: 12px;
  text-transform: uppercase;
  letter-spacing: 0.04em;
}

.badge-top5 {
  border: 2px solid gold;
  background: #2e2e2e;
  color: gold;
}

.badge-elite {
  background: #00c853;
  color: #121212;
}

.badge-injury {
  background: #ff5252;
  color: #fff;
}

.badge-prospect {
  background: #264d2c;
  color: #8be58d;
}

.badge-trade {
  background: #555;
  color: #ccc;
}
```

---

## 🔘 Button Styles

```css
.button {
  background: #f6b003;
  color: #121212;
  border: none;
  border-radius: 8px;
  padding: 10px 18px;
  font-weight: 600;
  font-family: 'Inter', sans-serif;
  text-transform: uppercase;
  cursor: pointer;
  box-shadow: 0px 4px 12px rgba(0,0,0,0.4);
  transition: all 0.25s ease-in-out;
}

.button:hover {
  background: #ffd95a;
  box-shadow: 0px 6px 20px rgba(0,0,0,0.5);
}
```

---

## 📦 Card Grid Layout

```css
.card-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
  gap: 24px;
  margin: 40px 0;
}
```

---

## 📍 Tooltip CSS

```css
.tooltip {
  position: relative;
  display: inline-block;
  cursor: help;
}

.tooltip .tooltiptext {
  visibility: hidden;
  width: 160px;
  background-color: #333;
  color: #fff;
  text-align: center;
  border-radius: 6px;
  padding: 6px;
  position: absolute;
  z-index: 1;
  bottom: 125%;
  left: 50%;
  margin-left: -80px;
  opacity: 0;
  transition: opacity 0.3s;
}

.tooltip:hover .tooltiptext {
  visibility: visible;
  opacity: 1;
}
```

---

## 📊 RRI Table HTML Template

```html
<table class="custom-table">
  <thead>
    <tr>
      <th>RRI Score</th>
      <th>Player</th>
      <th>Team</th>
      <th>Role</th>
      <th>CSW%</th>
      <th>Stuff+</th>
      <th>Badge</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>92.4</td>
      <td><a href="#">Devin Williams</a></td>
      <td><img src="https://upload.wikimedia.org/wikipedia/en/thumb/1/11/Milwaukee_Brewers.svg/28px-Milwaukee_Brewers.svg.png" alt="MIL"></td>
      <td>Closer</td>
      <td>38.2%</td>
      <td>132</td>
      <td><span class="badge badge-top5">Top 5%</span></td>
    </tr>
  </tbody>
</table>
```

---

## 🃏 Player Card HTML Template

```html
<div class="card-grid">
  <div class="card">
    <h2>Josh Hader</h2>
    <p><strong>Team:</strong> <img src="https://upload.wikimedia.org/wikipedia/en/thumb/2/25/San_Diego_Padres_logo.svg/28px-San_Diego_Padres_logo.svg.png" alt="SDP"> San Diego Padres</p>
    <p><strong>Role:</strong> Closer</p>
    <p><strong>CSW%:</strong> 39.1%</p>
    <p><strong>Stuff+:</strong> 140</p>
    <p><strong>Pitching+:</strong> 133</p>
    <p><span class="badge badge-top5">Top 5%</span> <span class="badge badge-elite">Elite</span></p>
    <button class="button">View Profile</button>
  </div>
</div>
```

---

## 🧪 Tooltip Example

```html
<p>
  <span class="tooltip">Stuff+ 
    <span class="tooltiptext">Measures pitch quality vs league average. 100 = Avg.</span>
  </span>: 132
</p>
```

---

Would you like this packaged as a downloadable `.md` file or added into your GitHub project `README` or `STYLEGUIDE.md`?

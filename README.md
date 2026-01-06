<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>e-Nagrik</title>
  <style>
    * { margin: 0; padding: 0; box-sizing: border-box; }

    body {
      font-family: 'Segoe UI', Arial, sans-serif;
      background: linear-gradient(135deg, #0F172A 0%, #1a1f3a 50%, #0F172A 100%);
      color: #E0E7FF;
      min-height: 100vh;
    }

    /* Navbar */
    nav {
      background: #1E3A8A;
      color: #fff;
      padding: 15px 30px;
      display: flex;
      justify-content: space-between;
      align-items: center;
    }
    nav .logo {
      display: flex;
      align-items: center;
    }
    nav .logo img {
      height: 40px;
      margin-right: 10px;
    }
    nav .logo span {
      font-size: 1.5em;
      font-weight: bold;
      color: #F97316;
    }
    nav ul {
      list-style: none;
      display: flex;
      margin-right: auto;
    }
    nav ul li {
      margin-left: 20px;
    }
    nav ul li a {
      color: #fff;
      text-decoration: none;
      transition: color 0.3s;
    }
    nav ul li a:hover {
      color: #06B6D4;
    }
    nav button {
      background: #F97316;
      border: none;
      padding: 8px 15px;
      border-radius: 4px;
      color: #fff;
      cursor: pointer;
      margin-left: 10px;
      transition: background 0.3s;
    }
    nav button:hover {
      background: #fb923c;
    }

    /* Hero Section */
    .hero {
      background: linear-gradient(to right, #1E3A8A, #06B6D4);
      color: #fff;
      text-align: center;
      padding: 80px 20px;
    }
    .hero h1 {
      font-size: 2.8em;
      margin-bottom: 20px;
    }
    .hero p {
      font-size: 1.2em;
      margin-bottom: 30px;
    }
    .hero a {
      background: #F97316;
      color: #fff;
      padding: 12px 25px;
      text-decoration: none;
      border-radius: 5px;
      font-weight: bold;
      transition: background 0.3s;
    }
    .hero a:hover {
      background: #fb923c;
    }

    /* Services Section */
    .services {
      display: flex;
      justify-content: space-around;
      padding: 70px 20px;
      background: linear-gradient(135deg, #0F172A 0%, #1E293B 100%);
      margin: 50px 0;
      align-items: center;
      flex-wrap: wrap;
      gap: 30px;
    }
    .card {
      background: rgba(255, 255, 255, 0.03);
      padding: 40px 30px;
      width: 35%;
      border-radius: 15px;
      border: 1px solid rgba(6, 182, 212, 0.3);
      text-align: center;
      transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
      backdrop-filter: blur(10px);
      min-width: 280px;
      cursor: pointer;
    }
    .card:hover {
      transform: translateY(-10px);
      border-color: rgba(6, 182, 212, 0.7);
      box-shadow: 0 20px 50px rgba(6, 182, 212, 0.25), inset 0 1px 0 rgba(255, 255, 255, 0.1);
      background: rgba(6, 182, 212, 0.08);
    }
    .card h3 {
      margin-bottom: 15px;
      background: linear-gradient(135deg, #06B6D4, #0EA5E9);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      background-clip: text;
      font-size: 1.5em;
      font-weight: 700;
      letter-spacing: -0.5px;
    }
    .card p {
      color: #CBD5E1;
      line-height: 1.6;
      font-size: 0.95em;
    }

    /* Footer */
    footer {
      background: #1E3A8A;
      color: #fff;
      text-align: center;
      padding: 15px;
      margin-top: 30px;
    }
    footer p {
      color: #06B6D4;
    }

    /* Modal Popup */
    .modal {
      display: none;
      position: fixed;
      z-index: 1;
      left: 0; top: 0;
      width: 100%; height: 100%;
      background-color: rgba(0,0,0,0.5);
    }
    .modal-content {
      background: #fff;
      margin: 5% auto;
      padding: 20px;
      border-radius: 8px;
      width: 350px;
      text-align: center;
    }
    .modal-content h2 {
      color: #1E3A8A;
      margin-bottom: 15px;
    }
    .modal-content input, .modal-content select {
      width: 90%;
      padding: 8px;
      margin: 8px 0;
      border: 1px solid #ccc;
      border-radius: 4px;
    }
    .modal-content button {
      background: #1E3A8A;
      color: #fff;
      border: none;
      padding: 10px;
      border-radius: 4px;
      cursor: pointer;
      transition: background 0.3s;
    }
    .modal-content button:hover {
      background: #06B6D4;
    }
    .close {
      float: right;
      font-size: 24px;
      cursor: pointer;
      color: #aaa;
    }
    .close:hover {
      color: #000;
    }

    /* FAQ Section */
    .faq {
      padding: 70px 20px;
      max-width: 1000px;
      margin: 0 auto;
      background: linear-gradient(135deg, #0F172A 0%, #1E293B 100%);
      border-radius: 20px;
      margin: 50px auto;
    }
    .faq h2 {
      text-align: center;
      background: linear-gradient(135deg, #06B6D4, #0EA5E9);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      background-clip: text;
      margin-bottom: 50px;
      font-size: 2.5em;
      font-weight: 700;
      letter-spacing: -0.5px;
    }
    .faq-item {
      background: rgba(255, 255, 255, 0.03);
      margin-bottom: 20px;
      border-radius: 12px;
      border: 1px solid rgba(6, 182, 212, 0.2);
      overflow: hidden;
      transition: all 0.3s ease;
      backdrop-filter: blur(10px);
    }
    .faq-item:hover {
      border-color: rgba(6, 182, 212, 0.5);
      box-shadow: 0 8px 32px rgba(6, 182, 212, 0.15);
      transform: translateY(-2px);
    }
    .faq-question {
      background: linear-gradient(90deg, rgba(6, 182, 212, 0.1), rgba(14, 165, 233, 0.05));
      padding: 20px 25px;
      cursor: pointer;
      display: flex;
      justify-content: space-between;
      align-items: center;
      font-weight: 600;
      color: #E0F2FE;
      transition: all 0.3s ease;
      font-size: 1.05em;
      letter-spacing: 0.3px;
    }
    .faq-question:hover {
      background: linear-gradient(90deg, rgba(6, 182, 212, 0.2), rgba(14, 165, 233, 0.1));
      color: #06B6D4;
      padding-left: 30px;
    }
    .faq-question .toggle-icon {
      font-size: 1.5em;
      transition: transform 0.4s cubic-bezier(0.4, 0, 0.2, 1);
      color: #06B6D4;
    }
    .faq-question.active .toggle-icon {
      transform: rotate(180deg);
      color: #0EA5E9;
    }
    .faq-answer {
      padding: 0 25px;
      max-height: 0;
      overflow: hidden;
      transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
      color: #CBD5E1;
      line-height: 1.7;
      font-size: 0.95em;
    }
    .faq-answer.active {
      padding: 25px;
      max-height: 600px;
    }
    .faq-answer p {
      color: #CBD5E1;
    }
  </style>
</head>
<body>

  <!-- Navbar -->
  <nav>
    <div class="logo">
      <img src="C:\Users\Garvi\Downloads\e-nagrik-removebg-preview.png" alt="e-Nagrik Logo">
      <span>e-Nagrik</span>
    </div>
    <ul>
      <li><a href="#">Home</a></li>
      <li><a href="#">Services</a></li>
      <li><a href="#">About</a></li>
      <li><a href="#">Contact</a></li>
    </ul>
    <!-- Buttons -->
    <button id="loginBtn">Login</button>
    <button id="registerBtn">Register</button>
  </nav>

  <!-- Hero Section -->
  <section class="hero">
    <h1>Empowering Citizens with Digital Access</h1>
    <p>Your gateway to government services, simplified.</p>
    <a href="#services">Get Started</a>
  </section>

  <!-- Services Section -->
  <section id="services" class="services">
    <div class="card">
      <h3>Pay Bills</h3>
      <p>Secure and easy payment options for utilities.</p>
    </div>
    <div class="card">
      <h3>Track Requests</h3>
      <p>Stay updated on your application status.</p>
    </div>
  </section>

  <!-- FAQ Section -->
  <section class="faq">
    <h2>Frequently Asked Questions</h2>
    <div class="faq-item">
      <div class="faq-question">
        <span>How do I register on e-Nagrik?</span>
        <span class="toggle-icon">▼</span>
      </div>
      <div class="faq-answer">
        <p>Click the "Register" button on the top right, fill in your details including your Aadhaar number, select your state and city, and submit the form. You'll receive a confirmation via email or SMS.</p>
      </div>
    </div>

    <div class="faq-item">
      <div class="faq-question">
        <span>Is my personal information secure?</span>
        <span class="toggle-icon">▼</span>
      </div>
      <div class="faq-answer">
        <p>Yes, we use industry-standard encryption and security protocols to protect your data. Your Aadhaar and personal information are never shared with third parties without your consent.</p>
      </div>
    </div>

    <div class="faq-item">
      <div class="faq-question">
        <span>How can I track my application status?</span>
        <span class="toggle-icon">▼</span>
      </div>
      <div class="faq-answer">
        <p>After logging in, navigate to "Track Requests" from the main menu. Enter your application ID or reference number to view real-time updates on your application status.</p>
      </div>
    </div>

    <div class="faq-item">
      <div class="faq-question">
        <span>What payment methods do you accept?</span>
        <span class="toggle-icon">▼</span>
      </div>
      <div class="faq-answer">
        <p>We accept multiple payment methods including credit cards, debit cards, net banking, UPI, and digital wallets. All payments are processed securely through authorized payment gateways.</p>
      </div>
    </div>

    <div class="faq-item">
      <div class="faq-question">
        <span>Can I update my profile information?</span>
        <span class="toggle-icon">▼</span>
      </div>
      <div class="faq-answer">
        <p>Yes, you can update your profile information after logging in. Go to "Account Settings" and modify your details. Some information like Aadhaar number cannot be changed for security reasons.</p>
      </div>
    </div>

    <div class="faq-item">
      <div class="faq-question">
        <span>What should I do if I forget my password?</span>
        <span class="toggle-icon">▼</span>
      </div>
      <div class="faq-answer">
        <p>Click on "Forgot Password" on the login page. Enter your registered mobile number or email, and you'll receive an OTP or password reset link. Follow the instructions to create a new password.</p>
      </div>
    </div>

    <div class="faq-item">
      <div class="faq-question">
        <span>Is the e-Nagrik platform available 24/7?</span>
        <span class="toggle-icon">▼</span>
      </div>
      <div class="faq-answer">
        <p>Yes, our platform is available 24/7. However, some government services may have specific office hours. For technical support, contact us during business hours or submit your query through the help center.</p>
      </div>
    </div>
  </section>

  <!-- Footer -->
  <footer>
    <p>&copy; 2025 e-Nagrik | All Rights Reserved</p>
  </footer>

  <!-- ✅ Login Modal -->
  <div id="loginModal" class="modal">
    <div class="modal-content">
      <span class="close">&times;</span>
      <h2>Login</h2>
      <div id="loginError" style="color: #ef4444; margin-bottom: 15px; font-weight: bold; display: none;"></div>
      <form id="loginForm">
        <input type="text" id="username" placeholder="Enter Username" required>
        <input type="password" id="password" placeholder="Enter Password" required>
        <button type="submit">Login</button>
      </form>
    </div>
  </div>

  <!-- ✅ Register Modal -->
  <div id="registerModal" class="modal">
    <div class="modal-content">
      <span class="close">&times;</span>
      <h2>Register</h2>
      <form id="registerForm">
        <input type="text" placeholder="Full Name" required>
        <input type="email" placeholder="Email" required>
        <input type="password" placeholder="Password" required>
        <label for="dob">Date of Birth:</label>
      <input type="date" id="dob" name="dob" required>

<label for="aadhaar">Aadhaar Number:</label>
      <input type="text" id="aadhaar" name="aadhaar" 
             placeholder="Enter 12-digit Aadhaar" 
             pattern="\d{12}" maxlength="12" required>


        <label for="stateSelect">State:</label>
        <select id="stateSelect" required>
          <option value="">-- Choose State --</option>
          <option value="Andaman and Nicobar Islands">Andaman and Nicobar Islands</option>
          <option value="Andhra Pradesh">Andhra Pradesh</option>
          <option value="Arunachal Pradesh">Arunachal Pradesh</option>
          <option value="Assam">Assam</option>
          <option value="Bihar">Bihar</option>
          <option value="Chandigarh">Chandigarh</option>
          <option value="Chhattisgarh">Chhattisgarh</option>
          <option value="Dadra and Nagar Haveli and Daman and Diu">Dadra and Nagar Haveli and Daman and Diu</option>
          <option value="Delhi">Delhi</option>
          <option value="Goa">Goa</option>
          <option value="Gujarat">Gujarat</option>
          <option value="Haryana">Haryana</option>
          <option value="Himachal Pradesh">Himachal Pradesh</option>
          <option value="Jammu and Kashmir">Jammu and Kashmir</option>
          <option value="Jharkhand">Jharkhand</option>
          <option value="Karnataka">Karnataka</option>
          <option value="Kerala">Kerala</option>
          <option value="Ladakh">Ladakh</option>
          <option value="Lakshadweep">Lakshadweep</option>
          <option value="Madhya Pradesh">Madhya Pradesh</option>
          <option value="Maharashtra">Maharashtra</option>
          <option value="Manipur">Manipur</option>
          <option value="Meghalaya">Meghalaya</option>
          <option value="Nagaland">Nagaland</option>
          <option value="Odisha">Odisha</option>
          <option value="Puducherry">Puducherry</option>
          <option value="Punjab">Punjab</option>
          <option value="Rajasthan">Rajasthan</option>
          <option value="Sikkim">Sikkim</option>
          <option value="Tamil Nadu">Tamil Nadu</option>
          <option value="Telangana">Telangana</option>
          <option value="Tripura">Tripura</option>
          <option value="Uttar Pradesh">Uttar Pradesh</option>
          <option value="Uttarakhand">Uttarakhand</option>
          <option value="West Bengal">West Bengal</option>
        </select>

        <label for="citySelect">City:</label>
        <select id="citySelect" required>
          <option value="">-- Choose City --</option>
        </select>

        <button type="submit">Register</button>
      </form>
    </div>
  </div>

  <script>
    // State → Cities mapping (Alphabetically sorted)
    const statesAndCities = {
  "Andaman and Nicobar Islands": [
    "Car Nicobar", "Havelock Island", "Little Andaman", "Neil Island", "Port Blair"
  ],
  "Andhra Pradesh": [
    "Anantapur", "Banganapalle", "Bhimavaram", "Chittoor", "Guntur", "Hindupur",
    "Jammalamadugu", "Kadapa", "Kurnool", "Machilipatnam", "Nandyal", "Nellore",
    "Ongole", "Palakollu", "Proddatur", "Rajamundry", "Srikakulam", "Tirupati",
    "Vijayawada", "Visakhapatnam"
  ],
  "Arunachal Pradesh": [
    "Anini", "Bomdila", "Changlang", "Daporijo", "Hayuliang", "Itanagar",
    "Khonsa", "Naharlagun", "Namsai", "Pasighat", "Roing", "Seppa",
    "Tawang", "Yingkiong", "Ziro"
  ],
  "Assam": [
    "Barpeta", "Bilasipara", "Bongaigaon", "Chabua", "Dhemaji", "Dhubri",
    "Diphu", "Dibrugarh", "Duliajan", "Goalpara", "Guwahati", "Haflong",
    "Hojai", "Jorhat", "Karimganj", "Kokrajhar", "Lumding", "Mangaldoi",
    "Margherita", "Nagaon", "North Lakhimpur", "Rangia", "Sarupathar",
    "Silchar", "Sivasagar", "Sualkuchi", "Tezpur", "Tinsukia"
  ],
  "Bihar": [
    "Araria", "Arrah", "Aurangabad", "Begusarai", "Bhagalpur", "Bihar Sharif",
    "Buxar", "Chapra", "Darbhanga", "Gaya", "Gopalganj", "Jamapur",
    "Jehanabad", "Katihar", "Khagaria", "Kishanganj", "Lakhisarai", "Madhepura",
    "Motihari", "Munger", "Muzaffarpur", "Nawada", "Patna", "Purnia",
    "Saharsa", "Samastipur", "Sheikhpura", "Siwan", "Sitamarhi", "Vaishali"
  ],
  "Chandigarh": ["Chandigarh"],
  "Chhattisgarh": [
    "Ambikapur", "Balod", "Baloda Bazar", "Bastar", "Bhilai", "Bijapur",
    "Bilaspur", "Dantewada", "Dhamtari", "Durg", "Gariaband", "Jagdalpur",
    "Jashpur", "Kanker", "Kondagaon", "Korba", "Mahasamund", "Mungeli",
    "Narayanpur", "Raigarh", "Raipur", "Rajnandgaon", "Sakti", "Sukma",
    "Surajpur"
  ],
  "Dadra and Nagar Haveli and Daman and Diu": ["Daman", "Diu", "Silvassa"],
  "Delhi": [
    "Ashok Vihar", "Chandni Chowk", "Connaught Place", "Dwarka", "Greater Kailash",
    "Janakpuri", "Jangpura", "Karol Bagh", "Kalkaji", "Lajpat Nagar", "Laxmi Nagar",
    "Mayur Vihar", "Model Town", "Moti Bagh", "Nehru Place", "New Delhi",
    "Patel Nagar", "Paharganj", "Pitampura", "Punjabi Bagh", "Rohini",
    "Sadar Bazaar", "Saket", "Sarojini Nagar", "Shahdara", "Tilak Nagar",
    "Tughlakabad", "Vasant Kunj"
  ],
  "Goa": [
    "Bicholim", "Canacona", "Curchorem", "Dharbandora", "Mapusa", "Margao",
    "Mormugao", "Panaji", "Ponda", "Quepem", "Sanguem", "Vasco da Gama"
  ],
  "Gujarat": [
    "Ahmedabad", "Amreli", "Anand", "Aravalli", "Bharuch", "Bhavnagar", "Botad",
    "Chhota Udaipur", "Dahod", "Devbhoomi Dwarka", "Gandhinagar", "Gir Somnath",
    "Jamnagar", "Junagadh", "Kheda", "Mahesana", "Mahisagar", "Morbi", "Nadiad",
    "Navsari", "Patan", "Porbandar", "Rajkot", "Surat", "Surendranagar",
    "Tapi", "Vadodara", "Valsad", "Vapi"
  ],
  "Haryana": [
    "Ambala", "Ateli", "Bahadurgarh", "Bhiwani", "Charkhi Dadri", "Faridabad",
    "Fatehabad", "Gohana", "Gurgaon", "Hisar", "Jhajjar", "Jind", "Kaithal",
    "Karnal", "Kurukshetra", "Mahendragarh", "Mewat", "Narwana", "Narnaul",
    "Palwal", "Panipat", "Panchkula", "Rewari", "Rohtak", "Safidon", "Sirsa",
    "Sonepat", "Sonipat", "Tosham", "Yamunanagar"
  ],
  "Himachal Pradesh": [
    "Arki", "Baddi", "Barsar", "Bilaspur", "Chamba", "Dharamshala", "Hamirpur",
    "Jubbal-Kotkhai", "Kangra", "Kinnaur", "Kullu", "Lahaul and Spiti", "Mandi",
    "Nahan", "Nalagarh", "Palampur", "Rohru", "Shimla", "Solan", "Sirmaur",
    "Theog", "Una"
  ],
  "Jammu and Kashmir": [
    "Anantnag", "Bandipora", "Baramulla", "Budgam", "Doda", "Ganderbal",
    "Jammu", "Kathua", "Kishtwar", "Kulgam", "Poonch", "Pulwama", "Rajouri",
    "Reasi", "Samba", "Shopian", "Srinagar", "Udhampur"
  ],
  "Jharkhand": [
    "Bokaro Steel City", "Bundu", "Chaibasa", "Chatra", "Deoghar", "Dhanbad",
    "Dumka", "Garhwa", "Giridih", "Godda", "Gumla", "Hazaribagh", "Jamshedpur",
    "Jamtara", "Khunti", "Koderma", "Latehar", "Lohardaga", "Medininagar",
    "Pakur", "Palamu", "Ramgarh", "Ramgarh Cantonment", "Ranchi", "Saraikela",
    "Sahibganj", "Simdega"
  ],
  "Karnataka": [
    "Bagalkot", "Bagepalli", "Ballari", "Belagavi", "Bengaluru", "Bidar",
    "Chamarajanagar", "Chikkaballapur", "Chikkamagaluru", "Chitradurga",
    "Davangere", "Davanagere", "Gadag", "Hassan", "Haveri", "Hubli-Dharwad",
    "Kalaburagi", "Kodagu", "Kolar", "Koppal", "Mandya", "Mangalore",
    "Mysuru", "Raichur", "Ramanagara", "Shimoga", "Tumakuru", "Udupi",
    "Uttara Kannada", "Vijayapura", "Yadgir"
  ],
  "Kerala": [
    "Alappuzha", "Ernakulam", "Idukki", "Kannur", "Kasargod", "Kochi",
    "Kollam", "Kozhikode", "Malappuram", "Palakkad", "Pathanamthitta",
    "Thiruvananthapuram", "Thrissur", "Vadakara", "Wayanad"
  ],
  "Ladakh": ["Kargil", "Leh"],
  "Lakshadweep": ["Agatti", "Amini", "Bitra", "Chetlat", "Kadmat", "Kalpeni", "Kavaratti", "Minicoy"],
  "Madhya Pradesh": [
    "Alirajpur", "Ashoknagar", "Bhind", "Bhopal", "Burhanpur", "Chhindwara",
    "Damoh", "Datia", "Dewas", "Dhar", "Gwalior", "Hoshangabad", "Indore",
    "Jabalpur", "Mandsaur", "Morena", "Neemuch", "Pithampur", "Rajgarh",
    "Ratlam", "Rewa", "Sagar", "Satna", "Sehore", "Shivpuri", "Singrauli",
    "Tikamgarh", "Ujjain", "Vidisha"
  ],
  "Maharashtra": [
    "Ahmednagar", "Akola", "Amravati", "Aurangabad", "Beed", "Bhandara",
    "Chandrapur", "Dhule", "Gadchiroli", "Gondia", "Hingoli", "Jalgaon",
    "Jalna", "Kolhapur", "Latur", "Mumbai", "Nagpur", "Nanded", "Nandurbar",
    "Nashik", "Osmanabad", "Palghar", "Parbhani", "Pune", "Ratnagiri",
    "Satara", "Sangli", "Sindhudurg", "Solapur", "Thane", "Wardha",
    "Washim", "Yavatmal"
  ],
  "Manipur": [
    "Bishnupur", "Churachandpur", "Imphal", "Jiribam", "Kakching", "Kangla",
    "Tamenglong", "Thoubal"
  ],
  "Meghalaya": [
    "Baghmara", "Cherrapunjee", "Jowai", "Mawkynong", "Nongpoh", "Nongstoin",
    "Resubelpara", "Shillong", "Tura", "Williamnagar"
  ],
  "Nagaland": [
    "Dimapur", "Kiphire", "Kohima", "Longleng", "Mokokchung", "Mon",
    "Noklak", "Phek", "Tuensang", "Wokha", "Zunheboto"
  ],
  "Odisha": [
    "Angul", "Balasore", "Baripada", "Bhadrak", "Bhubaneswar", "Bolangir",
    "Boudh", "Cuttack", "Deogarh", "Dhenkanal", "Ganjam", "Jagatsinghpur",
    "Jajpur", "Jharsuguda", "Kalahandi", "Kendrapara", "Keonjhar",
    "Koraput", "Malkangiri", "Mayurbhanj", "Nayagarh", "Nuapada", "Puri",
    "Rayagada", "Rourkela", "Sambalpur", "Subarnapur", "Sundargarh"
  ],
  "Puducherry": ["Karaikal", "Mahe", "Puducherry", "Yanam"],
  "Punjab": [
    "Amloh", "Amritsar", "Barnala", "Batala", "Bathinda", "Dera Baba Nanak",
    "Faridkot", "Fazilka", "Firozpur", "Gurdaspur", "Hoshiarpur", "Jalandhar",
    "Kapurthala", "Ludhiana", "Malerkotla", "Mansa", "Moga", "Muktsar",
    "Nawanshahr", "Pathankot", "Patiala", "Qadian", "Rupnagar", "Sangrur",
    "Shaheed Bhagat Singh Nagar", "Sri Muktsar Sahib", "Tarn Taran", "Zirakpur"
  ],
  "Rajasthan": [
    "Ajmer", "Alwar", "Banswara", "Barmer", "Bharatpur", "Bhilwara", "Bikaner",
    "Chittorgarh", "Churu", "Dausa", "Dholpur", "Dungarpur", "Hanumangarh",
    "Jaipur", "Jaisalmer", "Jhalawar", "Jhunjhunu", "Jodhpur", "Karauli",
    "Kota", "Nagaur", "Pali", "Pratapgarh", "Rajsamand", "Sawai Madhopur",
    "Sikar", "Sirohi", "Sri Ganganagar", "Tonk"
  ],
  "Sikkim": [
    "Gangtok", "Geyzing", "Jorethang", "Mangan", "Namchi", "Pakyong",
    "Rangpo", "Yuksom"
  ],
  "Tamil Nadu": [
    "Ariyalur", "Chengalpattu", "Chennai", "Coimbatore", "Cuddalore",
    "Dharmapuri", "Dindigul", "Erode", "Kanchipuram", "Karur", "Krishnagiri",
    "Madurai", "Nagapattinam", "Nagercoil", "Namakkal", "Perambalur",
    "Pudukkottai", "Ramanathapuram", "Salem", "Sivakasi", "Tanjore",
    "Theni", "Thoothukudi", "Tiruchirappalli", "Tiruppur", "Tiruvannamalai",
    "Vellore", "Villupuram"
  ],
  "Telangana": [
    "Adilabad", "Bhadradri Kothagudem", "Hanumakonda", "Hyderabad", "Jagitial",
    "Jagtial", "Jogulamba Gadwal", "Kamareddy", "Karimnagar", "Khammam",
    "Mahbubnagar", "Mancherial", "Medak", "Mulugu", "Nagarkurnool", "Nalgonda",
    "Nizamabad", "Peddapalli", "Rajanna Sircilla", "Ramagundam", "Sangareddy",
    "Siddipet", "Suryapet", "Vikarabad", "Wanaparthy", "Warangal",
    "Yadadri Bhuvanagiri"
  ],
  "Tripura": [
    "Agartala", "Ambassa", "Belonia", "Dharmanagar", "Kailasahar",
    "Khowai", "Sabroom", "Udaipur"
  ],
  "Uttar Pradesh": [
    "Agra", "Aligarh", "Allahabad", "Amroha", "Barabanki", "Bareilly",
    "Bijnor", "Budaun", "Bulandshahr", "Chandauli", "Etawah", "Farrukhabad",
    "Firozabad", "Ghaziabad", "Gorakhpur", "Hardoi", "Jhansi", "Kanpur",
    "Kushinagar", "Lakhimpur Kheri", "Lucknow", "Mathura", "Meerut",
    "Moradabad", "Muzaffarnagar", "Noida", "Rampur", "Saharanpur",
    "Shahjahanpur", "Sitapur", "Varanasi"
  ],
  "Uttarakhand": [
    "Almora", "Bageshwar", "Chamoli", "Champawat", "Dehradun", "Garhwal",
    "Haldwani", "Haridwar", "Kashipur", "Kotdwar", "Nainital", "Pauri",
    "Pithoragarh", "Rishikesh", "Roorkee", "Rudrapur", "Tehri",
    "Udham Singh Nagar", "Udhamsingh Nagar"
  ],
  "West Bengal": [
    "Asansol", "Bankura", "Bardhaman", "Bhagalpur", "Durgapur", "Haldia",
    "Howrah", "Jalpaiguri", "Kharagpur", "Kolkata", "Malda", "Mumbai",
    "Raiganj", "Siliguri"
  ]
    };

    // Sample registered usernames (you can replace with actual backend validation)
    const registeredUsernames = ["user1", "user2", "admin", "test"];

    // Modal control for Login
    const loginModal = document.getElementById("loginModal");
    const loginBtn = document.getElementById("loginBtn");
    const loginClose = loginModal.getElementsByClassName("close")[0];
    const loginForm = document.getElementById("loginForm");
    const loginError = document.getElementById("loginError");

    loginBtn.onclick = function() {
      loginModal.style.display = "block";
      loginForm.reset();
      loginError.style.display = "none";
    }
    loginClose.onclick = function() {
      loginModal.style.display = "none";
    }

    // Login form validation
    loginForm.addEventListener("submit", function(e) {
      e.preventDefault();
      const username = document.getElementById("username").value.trim();
      const password = document.getElementById("password").value.trim();

      // Clear previous error
      loginError.style.display = "none";
      loginError.textContent = "";

      // Validate password
      if (!password) {
        loginError.textContent = "Please enter the password";
        loginError.style.display = "block";
        return;
      }

      // Validate username exists
      if (!registeredUsernames.includes(username.toLowerCase())) {
        loginError.textContent = "Username doesn't exist";
        loginError.style.display = "block";
        return;
      }

      // If validation passes
      alert("Login successful!");
      loginModal.style.display = "none";
      loginForm.reset();
    });
    window.onclick = function(event) {
      if (event.target == loginModal) {
        loginModal.style.display = "none";
      }
      if (event.target == registerModal) {
        registerModal.style.display = "none";
      }
    }

    // Modal control for Register
    const registerModal = document.getElementById("registerModal");
    const registerBtn = document.getElementById("registerBtn");
    const registerClose = registerModal.getElementsByClassName("close")[0];

    registerBtn.onclick = function() {
      registerModal.style.display = "block";
    }
    registerClose.onclick = function() {
      registerModal.style.display = "none";
    }

    // State → City dynamic dropdown
    const stateSelect = document.getElementById("stateSelect");
    const citySelect = document.getElementById("citySelect");

    stateSelect.addEventListener("change", function() {
      const selectedState = this.value;
      citySelect.innerHTML = "<option value=''>-- Choose City --</option>";
      if (statesAndCities[selectedState]) {
        statesAndCities[selectedState].forEach(city => {
          const option = document.createElement("option");
          option.value = city;
          option.textContent = city;
          citySelect.appendChild(option);
        });
      }
    });

    // FAQ Accordion functionality
    const faqQuestions = document.querySelectorAll(".faq-question");
    faqQuestions.forEach(question => {
      question.addEventListener("click", function() {
        const answer = this.nextElementSibling;
        const isActive = this.classList.contains("active");
        
        // Close all other FAQ items
        faqQuestions.forEach(q => {
          q.classList.remove("active");
          q.nextElementSibling.classList.remove("active");
        });
        
        // Toggle current FAQ item
        if (!isActive) {
          this.classList.add("active");
          answer.classList.add("active");
        }
      });
    });
  </script>

</body>
</html>

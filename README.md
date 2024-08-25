<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>AT&T Portal</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background-color: #f8f8f8;
        }
        header {
            background-color: #007ac1;
            padding: 15px;
            color: white;
            text-align: center;
        }
        .container {
            max-width: 600px;
            margin: 50px auto;
            padding: 20px;
            background-color: #ffffff;
            border-radius: 8px;
            box-shadow: 0px 0px 15px rgba(0, 0, 0, 0.1);
        }
        h2 {
            color: #000;
        }
        label {
            display: block;
            margin-top: 10px;
            color: #666;
        }
        input[type="text"], input[type="number"] {
            width: 100%;
            padding: 10px;
            margin: 5px 0 20px;
            border: 1px solid #ccc;
            border-radius: 5px;
        }
        .btn {
            background-color: #000;
            color: white;
            padding: 10px;
            border: none;
            border-radius: 5px;
            width: 100%;
            cursor: pointer;
        }
        .btn:hover {
            background-color: #333;
        }
        .error {
            color: #f00;
            margin-top: 10px;
            text-align: center;
        }
        .info-block {
            padding: 10px;
            background-color: #f8f8f8;
            border-radius: 8px;
            margin-bottom: 20px;
            border: 1px solid #ddd;
            display: flex;
            justify-content: space-between;
        }
        .profile-info {
            text-align: left;
        }
        .profile-info p {
            margin: 5px 0;
            font-size: 14px;
        }
        .date-time {
            text-align: right;
        }
        .date-time p {
            margin: 5px 0;
            font-size: 14px;
        }
        .status {
            background-color: #80c9a6;
            padding: 10px;
            color: white;
            text-align: center;
            font-weight: bold;
            border-radius: 5px;
        }
        .amount {
            background-color: #000;
            color: white;
            padding: 15px;
            text-align: center;
            font-size: 24px;
            font-weight: bold;
            margin-top: 20px;
            border-radius: 5px;
        }
    </style>
</head>
<body>

<header>
    <h1>AT&T</h1>
</header>

<div id="loginContainer" class="container">
    <h2>Sign in to a disconnected mobile account</h2>
    <form id="loginForm">
        <label for="phone">Your ten-digit mobile number</label>
        <input type="text" id="phone" name="phone" required>

        <label for="lastname">Last name on the bill account</label>
        <input type="text" id="lastname" name="lastname" required>

        <label for="zipcode">Five-digit billing zip code</label>
        <input type="number" id="zipcode" name="zipcode" required>

        <button type="submit" class="btn">Continue</button>
        <div id="error" class="error"></div>
    </form>
</div>

<div id="reimbursementContainer" class="container" style="display: none;">
    <div class="info-block">
        <div class="profile-info">
            <p><strong>NAME:</strong> KIM AMANDA</p>
            <p><strong>AGE:</strong> 25</p>
            <p><strong>LOCATION:</strong> FLORIDA</p>
            <p><strong>GENDER:</strong> FEMALE</p>
        </div>
        <div class="date-time">
            <p><strong>Date & Time:</strong></p>
            <p id="currentDateTime"></p>
        </div>
    </div>

    <h2>Reimbursement Details</h2>
    <div class="info-block">
        <h3>Offer: Keep and Switch</h3>
        <p><strong>Payment Type:</strong> Prepaid Virtual Card</p>
        <p class="status">Pending Validation</p>
    </div>
    
    <h3>Pick up where you left off</h3>
    <div class="info-block">
        <p><strong>Reimbursement Type:</strong> EIP</p>
        <p><strong>Reimbursement:</strong> $688.82</p>
    </div>
    
    <div class="amount">
        REIMBURSEMENT AMOUNT: $38.82
    </div>
</div>

<script>
    document.getElementById("loginForm").addEventListener("submit", function(event) {
        event.preventDefault();
        
        var phone = document.getElementById("phone").value;
        var lastname = document.getElementById("lastname").value;
        var zipcode = document.getElementById("zipcode").value;
        
        // Validation
        if (phone === "6094608109" && lastname.toLowerCase() === "amanda" && zipcode === "32072") {
            // Hide login form and show reimbursement details
            document.getElementById("loginContainer").style.display = "none";
            document.getElementById("reimbursementContainer").style.display = "block";
            
            // Set current date and time
            document.getElementById('currentDateTime').textContent = formatDate(new Date());
        } else {
            document.getElementById("error").textContent = "Invalid user";
        }
    });

    // Function to get the current date and time and format it
    function formatDate(date) {
        const options = {
            year: 'numeric', month: '2-digit', day: '2-digit',
            hour: '2-digit', minute: '2-digit', second: '2-digit',
            hour12: true
        };
        return new Intl.DateTimeFormat('en-US', options).format(date);
    }
</script>

</body>
</html>

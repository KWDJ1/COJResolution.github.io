<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Support Medicaid Expansion - Jacksonville</title>
    <style>
        /* Basic styling for a clean, readable layout */
        body { font-family: Arial, sans-serif; margin: 20px; max-width: 700px; }
        label { display: block; margin: 10px 0 5px; }
        input, button { width: 100%; padding: 10px; margin-bottom: 15px; font-size: 1em; }
        .button-group { display: flex; gap: 10px; }
    </style>
</head>
<body>

<h2>Support Jacksonville City Council's Medicaid Expansion Resolution 2024-776</h2>

<!-- Introductory text explaining the purpose of the website to users -->
<p>This website allows Jacksonville residents to easily show support for City Council Resolution 2024-776, which encourages Medicaid expansion in Florida. Enter your information below to personalize an email supporting the resolution. You can then:</p>
<ul>
    <li>Automatically compose the email using your email client.</li>
    <li>Manually copy the email addresses and message text to paste into your preferred email platform.</li>
</ul>

<!-- Form for users to enter their name and address, which will personalize the email content -->
<form id="contact-form">
    <label for="firstName">First Name:</label>
    <input type="text" id="firstName" required>
    
    <label for="lastName">Last Name:</label>
    <input type="text" id="lastName" required>
    
    <label for="address">Jacksonville Address:</label>
    <input type="text" id="address" required>
    
    <!-- Option 1: Automatically Compose Email with the user's default email client -->
    <div class="button-group">
        <button type="button" onclick="composeEmail()">Compose Email Automatically</button>
        
        <!-- Option 2: Manually Copy Email Addresses and Script for use in any email platform -->
        <button type="button" onclick="copyEmails()">Copy Email Addresses</button>
        <button type="button" onclick="copyMessage()">Copy Message Script</button>
    </div>
</form>

<script>
    // Array containing email addresses of Jacksonville City Council members
    const emails = [
        "KAMARO@coj.net", "MGAY@coj.net", "WLAHNEN@coj.net",
        "KCARRICO@coj.net", "JOECARLUCCI@coj.net", "MBOYLAN@coj.net",
        "JPELUSO@coj.net", "RGAFFNEYJR@coj.net", "TCLARKMURRAY@coj.net",
        "JPITTMAN@coj.net", "ARIASR@coj.net", "RANDYWHITE@coj.net",
        "RDIAMOND@coj.net", "RAHMAN@coj.net", "TFREEMAN@coj.net",
        "RSALEM@coj.net", "NHOWLAND@coj.net", "MCARLUCCI@coj.net", 
        "CHRISMILLER@coj.net"
    ];

    /**
     * Function to copy all council members' email addresses to the user's clipboard.
     * This is helpful for users who prefer to manually paste email addresses in their email client.
     */
    function copyEmails() {
        const emailList = emails.join(", ");
        
        // Use the Clipboard API to copy email addresses to the clipboard
        navigator.clipboard.writeText(emailList).then(() => {
            alert("Email addresses copied to clipboard!"); // Confirmation message
        });
    }

    /**
     * Function to compose an email in the user's default mail client with a pre-filled message.
     * The message includes the user's first name, last name, and address, along with support for Resolution 2024-776.
     */
    function composeEmail() {
        // Retrieve user's first name, last name, and address from the input fields
        const firstName = document.getElementById("firstName").value;
        const lastName = document.getElementById("lastName").value;
        const address = document.getElementById("address").value;

        // Alert the user if any field is left empty
        if (!firstName || !lastName || !address) {
            alert("Please fill in all fields before composing the email.");
            return;
        }

        // Define the subject line and email body, incorporating user inputs
        const subject = "Support for Resolution 2024-776";
        const body = `Hello to the City Council of Jacksonville,\n\n` +
            `I am ${firstName} ${lastName}, a resident of Jacksonville at ${address}. ` +
            `I would like to state my strong support for Resolution 2024-776, which advocates for Medicaid expansion in Florida.\n\n` +
            `As a community, we believe Medicaid expansion will help ensure that all Duval County residents have access to necessary healthcare. Thank you for your time and dedication to improving healthcare access in our city.\n\n` +
            `Sincerely,\n${firstName} ${lastName}`;

        // Construct mailto link with council email addresses, subject, and body
        const mailtoLink = `mailto:${emails.join(",")}?subject=${encodeURIComponent(subject)}&body=${encodeURIComponent(body)}`;
        
        // Open the user's default email client with the "mailto" link
        window.location.href = mailtoLink;
    }

    /**
     * Function to copy the email message script (body content) to the user's clipboard.
     * This allows users to manually paste it into any email platform.
     */
    function copyMessage() {
        const firstName = document.getElementById("firstName").value;
        const lastName = document.getElementById("lastName").value;
        const address = document.getElementById("address").value;

        // Check if all fields are filled
        if (!firstName || !lastName || !address) {
            alert("Please fill in all fields before copying the message script.");
            return;
        }

        // Construct the message content
        const message = `Hello to the City Council of Jacksonville,\n\n` +
            `I am ${firstName} ${lastName}, a resident of Jacksonville at ${address}. ` +
            `I would like to state my strong support for Resolution 2024-776, which advocates for Medicaid expansion in Florida.\n\n` +
            `As a community, we believe Medicaid expansion will help ensure that all Duval County residents have access to necessary healthcare. Thank you for your time and dedication to improving healthcare access in our city.\n\n` +
            `Sincerely,\n${firstName} ${lastName}`;

        // Copy the constructed message to the clipboard
        navigator.clipboard.writeText(message).then(() => {
            alert("Message script copied to clipboard!");
        });
    }
</script>

</body>
</html>

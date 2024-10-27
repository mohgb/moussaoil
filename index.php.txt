<?php
if ($_SERVER["REQUEST_METHOD"] == "POST") {
    $name = htmlspecialchars($_POST['name']);
    $mobile = htmlspecialchars($_POST['mobile']);
    $city = htmlspecialchars($_POST['city']);

    $to = "huiledolive777@gmail.com"; // Your email address
    $subject = "New Order for Extra Virgin Olive Oil";
    $message = "Product Name: Extra Virgin Olive Oil (5L)\nDescription: 100% extra virgin olive oil\nClient Name: $name\nMobile: $mobile\nCity: $city";
    $headers = "From: huiledolive777@gmail.com"; // Your email address

    if (mail($to, $subject, $message, $headers)) {
        $success_message = "Message sent successfully!";
        header("Refresh: 5; URL=index.php"); // Redirect after 5 seconds
        exit();
    } else {
        $success_message = "Message could not be sent.";
    }
}
?>

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Landing Page - Extra Virgin Olive Oil</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: white;
            margin: 0;
            padding: 0;
        }
        header {
            background-color: black;
            padding: 20px;
            text-align: center;
            color: white;
        }
        .container {
            width: 60%;
            margin: auto;
        }
        .product {
            text-align: center;
            margin: 20px 0;
        }
        .price {
            font-size: 24px;
            margin: 10px 0;
        }
        .form-container {
            padding: 20px;
            border: 1px solid #ccc;
            border-radius: 5px;
            background-color: #f9f9f9;
            margin-top: 20px;
        }
        .form-container input, .form-container button {
            width: 100%;
            padding: 10px;
            margin: 5px 0;
            border: 1px solid #ccc;
            border-radius: 5px;
        }
        .message {
            color: red;
            text-align: center;
        }
        .image-slider {
            display: flex;
            justify-content: center;
            overflow: hidden;
            position: relative;
            margin-bottom: 20px;
        }
        .image-slider img {
            width: 100%;
            max-width: 400px;
            margin: 0 5px;
        }
        .button-container {
            display: flex;
            justify-content: center;
            margin-top: 10px;
        }
        .prev, .next {
            cursor: pointer;
            padding: 10px;
            background-color: #ccc;
            border: none;
            border-radius: 5px;
        }
        @media (max-width: 768px) {
            .container {
                width: 90%;
            }
        }
    </style>
</head>
<body>

<header>
    <h1>My Logo</h1>
</header>

<div class="container">
    <div class="product">
        <h2>Extra Virgin Olive Oil (5L)</h2>
        <div class="image-slider">
            <img src="image1.jpg" alt="Product Image 1">
            
        </div>
        <div class="price">
            1000 L.E
        </div>
        <p>100% extra virgin olive oil</p>
    </div>

    <div class="form-container">
        <form method="POST" action="">
            <input type="text" name="name" placeholder="Your Name" required>
            <input type="text" name="mobile" placeholder="Your Mobile" required>
            <input type="text" name="city" placeholder="Your City" required>
            <button type="submit">Order Now</button>
        </form>
        <?php if (isset($success_message)): ?>
            <div class="message"><?php echo $success_message; ?></div>
        <?php endif; ?>
    </div>
</div>

</body>
</html>

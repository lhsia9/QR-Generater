<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width-device-width, initial-scale=1.0">
    <title>QR Generator</title>
    <link rel="stylesheet" href="style.css">
</head>


<body>
    <div class="container">
        <h1>QR Code Generator</h1>
        <input id="qr" type="text" placeholder="Enter text or URL">
        <div class="image">
            <img alt="QR code" id="qrimg">
        </div>
        <button>Generate QR Code</button>
    </div>
</body>

</html>

<style>
    @import url('https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500&display=swap');

    * {
        margin: 0;
        padding: 0;
        box-sizing: border-box;
        font-family: 'Inter', sans-serif;
    }


    body {
        display: flex;
        justify-content: center;
        align-items: center;
        min-height: 100vh;
        background-color: #e8e8e8;
    }

    .container {
        width: 90%;
        max-width: 350px;
        background: white;
        border-radius: 12px;
        padding: 30px;
        box-shadow: 0 10px 30px rgba(0,0,0,0.08);
        text-align: center;
    }

    h1 {
        font-size: 18px;
        margin-bottom: 20px;
        color: #333;
        font-weight: 500;
    }

    input {
        width: 100%;
        padding: 12px 15px;
        border: 2px solid #e0e0e0;
        border-radius: 8px;
        font-size: 15px;
        outline: none;
        margin-bottom: 20px;
        transition: all 0.3s ease;
    }

    input:focus {
        border-color: #6c63ff;
        box-shadow: 0 0 0 3px rgba(108,99, 255, 0.21);
    }

    #qrimg {
        width: 180px;
        height: 180px;
        margin: 0 auto;

        background: white;
        padding: 10px;
        border-radius: 8px;
        border: 1px solid #eee;
        transition: all 0.3s ease;
        opacity: 0;
    }

    #qrimg.show {
        opacity: 1;
    }

    button {
        background: #6c63ff;
        color: white;
        border: none;
        padding: 12px 25px;
        border-radius: 8px;
        font-size: 15px;
        font-weight: 500;
        cursor: pointer;
        transition: all 0.3s ease;
        width: 100%;


    
    button:hover {
        background-color: #5a52e0;
        transform: translateY(-2px);
        box-shadow: 0 5px 15px rgba(108, 99, 255, 0.2);
    }

        

    button:active {
        transform: translateY(0);
    }  
        
</style>


<script>
    function generateQR() {
        const input = document.getElementById("qr").value.trim();
        const img = document.getElementById("qrimg");
        const button = document.querySelector("button");

        if (!input) {
            alert("please enter some text or URL");
            return;
        }

        img.src =
            "https://api.qrserver.com/v1/create-qr-code/?size=180x180&data=" +
            encodeURIComponent(input);
        img.classList.add("show");
    }

    //엔터키 누르면 큐알 생성
    document.getElementById("qr").addEventListener("keypress", function (e) {
        if (e.key === "Enter") {
            generateQR();
        }
    });

    button.addEventListener("click", generateQR);
    
</script>

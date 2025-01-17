<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Tính Tỷ lệ Chuyển đổi Thức ăn (FCR)</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background-color: #e9ecef;
        }
        .container {
            max-width: 600px;
            margin: 50px auto;
            padding: 20px;
            background-color: #ffffff;
            border-radius: 8px;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
        }
        h1 {
            text-align: center;
            color: #333;
        }
        label {
            display: block;
            margin: 10px 0 5px;
            font-weight: bold;
        }
        input {
            padding: 10px;
            width: calc(100% - 22px);
            border: 1px solid #ccc;
            border-radius: 4px;
            margin-bottom: 15px;
        }
        button {
            padding: 10px 15px;
            background-color: #28a745;
            color: white;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            width: 100%;
            font-size: 16px;
        }
        button:hover {
            background-color: #218838;
        }
        .result {
            margin-top: 20px;
            font-weight: bold;
            color: #333;
            text-align: center;
        }
        .evaluation {
            margin-top: 10px;
            font-weight: bold;
            color: #007bff;
            text-align: center;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Tính Tỷ lệ Chuyển đổi Thức ăn (FCR)</h1>
        <label for="foodIntake">Lượng thức ăn tiêu thụ (kg):</label>
        <input type="number" id="foodIntake" placeholder="Nhập lượng thức ăn" required>
        
        <label for="weightGain">Trọng lượng tăng thêm (kg):</label>
        <input type="number" id="weightGain" placeholder="Nhập trọng lượng tăng" required>
        
        <button onclick="calculateFCR()">Tính FCR</button>
        
        <div class="result" id="result"></div>
        <div class="evaluation" id="evaluation"></div>
    </div>

    <script>
        function calculateFCR() {
            const foodIntake = parseFloat(document.getElementById('foodIntake').value);
            const weightGain = parseFloat(document.getElementById('weightGain').value);
            
            if (isNaN(foodIntake) || isNaN(weightGain) || weightGain <= 0) {
                document.getElementById('result').innerText = "Vui lòng nhập giá trị hợp lệ.";
                document.getElementById('evaluation').innerText = "";
                return;
            }
            
            const fcr = foodIntake / weightGain;
            document.getElementById('result').innerText = "FCR = " + fcr.toFixed(2);
            
            // Đánh giá FCR
            let evaluationMessage = "";
            if (fcr < 1.5) {
                evaluationMessage = "FCR vật nuôi của bạn rất tốt! Tiêu thụ thức ăn hiệu quả bạn là một người chăn nuôi có trách nhiệm.";
            } else if (fcr >= 1.5 && fcr <= 2.0) {
                evaluationMessage = "FCR vật nuôi của bạn trung bình. Cần cải thiện hiệu quả tiêu thụ thức ăn.";
            } else {
                evaluationMessage = "FCR vật nuôicủa bạn không tốt. Vật nuôi của bạn có vấn đề hoặc vấn đề là ở bạn.";
            }
            document.getElementById('evaluation').innerText = evaluationMessage;
        }
    </script>
</body>
<p>
    FCR trong chăn nuôi là viết tắt của cụm từ Feed Conversation Ratio, nghĩa là tỉ lệ chuyển đổi thức ăn.
    Hệ số này phản ánh hiệu suất của vật nuôi thông qua chuyển đổi khối lượng thức ăn đã tiêu tốn thành sản phẩm đầu ra mong muốn; bao gồm thịt, sữa, lông,...</p>

</html>

<!DOCTYPE html>
<html lang="tr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Hava Durumu Uygulaması</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f0f8ff;
            text-align: center;
            margin: 0;
            padding: 50px;
        }
        h1 {
            color: #333;
        }
        input {
            padding: 10px;
            width: 200px;
            border: 2px solid #ccc;
            border-radius: 5px;
        }
        button {
            padding: 10px 15px;
            background-color: #007bff;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }
        button:hover {
            background-color: #0056b3;
        }
        .result {
            margin-top: 20px;
            font-size: 20px;
        }
    </style>
</head>
<body>

    <h1>Hava Durumu Uygulaması</h1>
    <input type="text" id="city" placeholder="Şehir adı girin" value="İzmir">
    <button onclick="getWeather()">Hava Durumunu Göster</button>

    <div class="result" id="result"></div>

    <script>

            try {
                const response = await fetch(`https://www.mgm.gov.tr/tahmin/il-ve-ilceler.aspx?il=Izmir`);
                const data = await response.json();

                if (data.cod === 200) {
                    const temp = data.main.temp;
                    const weatherDescription = data.weather[0].description;
                    resultDiv.innerHTML = `Bugün ${Izmir} için hava durumu: ${weatherDescription}, ${temp}°C.`;
                } else {
                    resultDiv.innerHTML = 'Şehir bulunamadı, lütfen tekrar deneyin.';
                }
            } catch (error) {
                resultDiv.innerHTML = 'Bir hata oluştu. Lütfen daha sonra tekrar deneyin.';
            }
        }
    </script>

</body>
</html>

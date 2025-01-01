  <!doctype html>

<html>

<head>

    <meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1">

    <meta charset="utf-8">

    <title>Open Weather jQuery Plugin</title>

    <meta name="description" content="A simple, lightweight jQuery plugin used to display the current weather of any city using the free OpenWeatherMap API.">

    <meta name="author" content="http://michaelynch.com">

    <meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1">

    <link rel="stylesheet" type="text/css" media="screen" href="../src/css/style.css">

</head>

<body lang="en">

    <h1>Open Weather API APP in Javascript</h1>

    <form id="myform">
        <input type="text" id="city" required placeholder="Enter city here">
        <input type="submit" value="Get Weather">
    </form>


    <div class="weather-wrapper hide">

        <img src="" class="weather-icon" alt="Weather Icon" />

        <p><strong>Place</strong>
            <br /><span class="weather-place"></span></p>

        <p><strong>Temperature</strong>
            <br /><span class="weather-temperature"></span> (<span class="weather-min-temperature"></span> - <span class="weather-max-temperature"></span>)</p>

        <p><strong>Description</strong>
            <br /><span class="weather-description capitalize"></span></p>

        <p><strong>Humidity</strong>
            <br /><span class="weather-humidity"></span></p>

        <p><strong>Wind speed</strong>
            <br /><span class="weather-wind-speed"></span></p>

        <p><strong>Sunrise</strong>
            <br /><span class="weather-sunrise"></span></p>

        <p><strong>Sunset</strong>
            <br /><span class="weather-sunset"></span></p>

    </div>

    <script src="http://ajax.googleapis.com/ajax/libs/jquery/1.9.1/jquery.min.js"></script>

    <script type="text/javascript">
        if (typeof jQuery == 'undefined') {
            document.write(unescape("%3Cscript src='src/js/lib/jquery.1.9.1.min.js' type='text/javascript'%3E%3C/script%3E"));
        }
    </script>

    <script src="../src/openweather.js"></script>

    <script>
        $(function() {

            $("#myform").submit(function(e) {
                e.preventDefault()

                var city = $("#city").val()

                getweather(city)
            })

        });

        function getweather(city) {
            $('.weather-temperature').openWeather({
                key: '0b22e5df36471ed0b26829ed81bd6892',
                city: city,
                descriptionTarget: '.weather-description',
                windSpeedTarget: '.weather-wind-speed',
                minTemperatureTarget: '.weather-min-temperature',
                maxTemperatureTarget: '.weather-max-temperature',
                humidityTarget: '.weather-humidity',
                sunriseTarget: '.weather-sunrise',
                sunsetTarget: '.weather-sunset',
                placeTarget: '.weather-place',
                iconTarget: '.weather-icon',
                customIcons: '../src/img/icons/weather/',
                success: function(data) {
                    // show weather
                    $('.weather-wrapper').show();
                    console.log(data);
                },
                error: function(data) {
                    console.log(data.error);
                    $('.weather-wrapper').remove();
                }
            });

        }
    </script>

</body>

</html>

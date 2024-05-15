<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Film Bilgileri</title>
    <!-- Bootstrap CSS -->
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0-alpha1/dist/css/bootstrap.min.css" rel="stylesheet">
</head>
<body>
    <nav class="navbar navbar-expand-lg navbar-light bg-light">
        <div class="container">
            <a class="navbar-brand" href="#">Film Bilgileri</a>
            <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav" aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
                <span class="navbar-toggler-icon"></span>
            </button>
            <div class="collapse navbar-collapse" id="navbarNav">
                <ul class="navbar-nav">
                    <li class="nav-item dropdown">
                        <a class="nav-link dropdown-toggle" href="#" id="navbarDropdown" role="button" data-bs-toggle="dropdown" aria-expanded="false">
                            Kategoriler
                        </a>
                        <ul class="dropdown-menu" aria-labelledby="navbarDropdown">
                            <li><a class="dropdown-item" href="#">Aksiyon</a></li>
                            <li><a class="dropdown-item" href="#">Komedi</a></li>
                            <li><a class="dropdown-item" href="#">Drama</a></li>
                            <!-- Diğer kategoriler buraya eklenebilir -->
                        </ul>
                    </li>
                </ul>
                <form class="d-flex ms-auto" method="GET">
                    <input class="form-control me-2" type="search" placeholder="Film Ara" aria-label="Film Ara" name="filmAdi">
                    <button class="btn btn-outline-success" type="submit">Ara</button>
                </form>
            </div>
        </div>
    </nav>

    <div class="container mt-5">
        <div class="row">
            <div class="col-md-6 offset-md-3">
                <?php
                if(isset($_GET['filmAdi'])) {
                    // API anahtarı
                    $apiKey = '23bbd938';

                    // Film adı
                    $filmAdi = $_GET['filmAdi'];

                    // API sorgusu URL'si
                    $url = "http://www.omdbapi.com/?apikey=$apiKey&t=" . urlencode($filmAdi);

                    // Curl başlat
                    $ch = curl_init();

                    // Curl ayarlarını yap
                    curl_setopt($ch, CURLOPT_URL, $url);
                    curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
                    curl_setopt($ch, CURLOPT_CONNECTTIMEOUT, 10); // Bağlantı zaman aşımı süresi (saniye cinsinden)
                    curl_setopt($ch, CURLOPT_TIMEOUT, 30); // İstek zaman aşımı süresi (saniye cinsinden)
                    curl_setopt($ch, CURLOPT_HTTPHEADER, ['Accept: application/json']); // İstek başlıkları
                    curl_setopt($ch, CURLOPT_CUSTOMREQUEST, 'GET'); // İstek yöntemi

                    // Veriyi al
                    $response = curl_exec($ch);

                    // Curl hata kontrolü
                    if(curl_errno($ch)) {
                        echo '<div class="alert alert-danger" role="alert">Curl hatası: ' . curl_error($ch) . '</div>';
                    } else {
                        // Yanıtı işle
                        $data = json_decode($response, true);

                        // Veriyi yazdır
                        if(isset($data['Title'])) {
                            echo '<div class="card">';
                            echo '<img src="' . $data['Poster'] . '" class="card-img-top" alt="' . $data['Title'] . ' Poster">';
                            echo '<div class="card-header">' . $data['Title'] . '</div>';
                            echo '<div class="card-body">';
                            echo '<p class="card-text"><strong>Yıl:</strong> ' . $data['Year'] . '</p>';
                            echo '<p class="card-text"><strong>Tür:</strong> ' . $data['Genre'] . '</p>';
                            echo '<p class="card-text"><strong>Oyuncular:</strong> ' . $data['Actors'] . '</p>';
                            echo '<p class="card-text"><strong>IMDB Puanı:</strong> ' . $data['imdbRating'] . '</p>';
                            echo '</div>';
                            echo '</div>';
                        } else {
                            echo '<div class="alert alert-warning" role="alert">Film bulunamadı.</div>';
                        }
                    }

                    // Curl'i kapat
                    curl_close($ch);
                }
                ?>
            </div>
        </div>
    </div>
    <!-- Bootstrap JS (Opsiyonel olarak kullanılabilir) -->
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0-alpha1/dist/js/bootstrap.bundle.min.js"></script>
</body>
</html>

<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>AnimeRu</title>
    <style>
        body {
            margin: 0;
            padding: 0;
            font-family: Arial, sans-serif;
            color: white;
            background-image: url('https://abrakadabra.fun/uploads/posts/2022-03/1646198301_23-abrakadabra-fun-p-kitaiskie-simvoli-na-chernom-fone-36.jpg');
            background-size: cover;
            background-position: center;
            background-attachment: fixed;
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            align-items: center;
        }

        header {
            width: 100%;
            padding: 20px;
            background-color: rgba(0, 0, 0, 0.5);
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        h1 {
            font-size: 2.5rem;
            margin: 0;
            text-shadow: 2px 2px 5px rgba(0, 0, 0, 0.7);
        }

        nav {
            display: flex;
            gap: 15px;
        }

        nav a {
            color: white;
            text-decoration: none;
            font-size: 1.2rem;
            text-shadow: 1px 1px 3px rgba(0, 0, 0, 0.7);
            padding: 10px 15px;
            background-color: rgba(255, 255, 255, 0.2);
            border-radius: 5px;
            transition: background-color 0.3s ease;
        }

        nav a:hover {
            background-color: rgba(255, 255, 255, 0.4);
        }

        .content {
            display: flex;
            align-items: center;
            gap: 30px;
            margin-top: 50px;
            background-color: rgba(0, 0, 0, 0.6);
            padding: 20px;
            border-radius: 10px;
            max-width: 800px;
        }

        .content img {
            width: 250px;
            height: auto;
            border-radius: 10px;
        }

        .content p {
            font-size: 1.1rem;
            line-height: 1.6;
            margin: 0;
        }

        .gallery-section {
            width: 100%;
            padding: 40px 20px;
            background-color: rgba(0, 0, 0, 0.7);
            margin-top: 50px;
            text-align: center;
        }

        .gallery-section h2 {
            font-size: 2rem;
            margin-bottom: 20px;
            text-shadow: 2px 2px 5px rgba(0, 0, 0, 0.7);
        }

        .gallery {
            display: flex;
            justify-content: center;
            gap: 20px;
            flex-wrap: wrap;
        }

        .gallery img {
            width: 200px;
            height: 150px;
            object-fit: cover;
            border-radius: 10px;
            transition: transform 0.3s ease, box-shadow 0.3s ease;
            cursor: pointer;
        }

        .gallery img:hover {
            transform: scale(1.1);
            box-shadow: 0 0 15px rgba(255, 255, 255, 0.5);
        }

        /* Модальное окно */
        .modal {
            display: none;
            position: fixed;
            z-index: 1000;
            left: 0;
            top: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.9);
            justify-content: center;
            align-items: center;
        }

        .modal img {
            max-width: 90%;
            max-height: 90%;
            border-radius: 10px;
        }

        .close {
            position: absolute;
            top: 20px;
            right: 30px;
            color: white;
            font-size: 40px;
            font-weight: bold;
            cursor: pointer;
        }

        .close:hover {
            color: #ccc;
        }
    </style>
</head>
<body>
    <header>
        <h1>AnimeRu</h1>
        <nav>
            <a href="#">Главная</a>
            <a href="#">Аниме</a>
            <a href="#">Новости</a>
            <a href="#">Форум</a>
            <a href="#">Контакты</a>
        </nav>
    </header>

    <div class="content">
        <img src="https://i.pinimg.com/736x/8c/8e/66/8c8e66f77c287e1748eadb7f7ce66f8f.jpg" alt="Аниме изображение">
        <p>
            Добро пожаловать на AnimeRu — ваш главный источник всего, что связано с аниме!<br><br>
            У нас вы найдете последние новости из мира аниме, обзоры популярных сериалов, рекомендации и многое другое. Присоединяйтесь к нашему сообществу и делитесь своими впечатлениями на форуме!<br><br>
            Следите за обновлениями и не пропустите ничего интересного!
        </p>
    </div>

    <div class="gallery-section">
        <h2>Галерея</h2>
        <div class="gallery">
            <img src="https://steamuserimages-a.akamaihd.net/ugc/2014832659479525815/7DFAC9BEF7170A23FC1D38E6AC88FBCE9E059192/?imw=512&imh=341&ima=fit&impolicy=Letterbox&imcolor=%23000000&letterbox=true" alt="Фото 1" onclick="openModal(this)">
            <img src="https://steamuserimages-a.akamaihd.net/ugc/1651098116525377422/C573586CF4D272DBA475E77240CCB96363F47D85/?imw=512&&ima=fit&impolicy=Letterbox&imcolor=%23000000&letterbox=false" alt="Фото 2" onclick="openModal(this)">
            <img src="https://avatars.mds.yandex.net/get-mpic/5279099/img_id3081793260211986243.jpeg/orig" alt="Фото 3" onclick="openModal(this)">
            <img src="https://steamuserimages-a.akamaihd.net/ugc/930428065179143678/9575C14BCA0D4A3A45D0226F36EDF53CFF37778C/?imw=512&imh=288&ima=fit&impolicy=Letterbox&imcolor=%23000000&letterbox=true" alt="Фото 4" onclick="openModal(this)">
        </div>
    </div>

    <!-- Модальное окно -->
    <div id="modal" class="modal">
        <span class="close" onclick="closeModal()">&times;</span>
        <img id="modalImage" src="" alt="Увеличенное изображение">
    </div>

    <script>
        // Функция для открытия модального окна
        function openModal(img) {
            const modal = document.getElementById('modal');
            const modalImg = document.getElementById('modalImage');
            modal.style.display = 'flex';
            modalImg.src = img.src;
        }

        // Функция для закрытия модального окна
        function closeModal() {
            const modal = document.getElementById('modal');
            modal.style.display = 'none';
        }

        // Закрытие модального окна при клике вне изображения
        window.onclick = function(event) {
            const modal = document.getElementById('modal');
            if (event.target === modal) {
                modal.style.display = 'none';
            }
        };
    </script>
</body>
</html>

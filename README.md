- 👋 Hi, I’m @leandro2030
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...

<!---
leandro2030/leandro2030 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Biblioteca de eBooks</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <header>
        <h1>Biblioteca de eBooks</h1>
    </header>
    <nav>
        <ul id="folder-list">
            <!-- Pastas e subpastas serão geradas aqui -->
        </ul>
    </nav>
    <main>
        <section id="ebook-display">
            <h2>Selecione um eBook para visualizar</h2>
            <!-- Área de visualização de eBooks -->
        </section>
    </main>
    <script src="scripts.js"></script>
</body>
</html>
body {
    font-family: Arial, sans-serif;
    margin: 0;
    padding: 0;
}

header {
    background-color: #4CAF50;
    color: white;
    text-align: center;
    padding: 1em 0;
}

nav {
    background-color: #f4f4f4;
    padding: 1em;
}

nav ul {
    list-style-type: none;
    padding: 0;
}

nav ul li {
    margin: 0.5em 0;
}

nav ul li a {
    text-decoration: none;
    color: #333;
}

main {
    padding: 1em;
}

#ebook-display {
    border: 1px solid #ddd;
    padding: 1em;
}
document.addEventListener('DOMContentLoaded', function () {
    const folders = {
        "Ficção": {
            "Fantasia": ["ebook1.pdf", "ebook2.pdf"],
            "Ficção Científica": ["ebook3.pdf"]
        },
        "Não-Ficção": {
            "Biografias": ["ebook4.pdf"],
            "História": ["ebook5.pdf"]
        }
    };

    const folderList = document.getElementById('folder-list');
    const ebookDisplay = document.getElementById('ebook-display');

    function createFolderStructure(folders, parentElement) {
        for (const folderName in folders) {
            const li = document.createElement('li');
            const folderLink = document.createElement('a');
            folderLink.href = "#";
            folderLink.textContent = folderName;
            folderLink.addEventListener('click', () => toggleFolder(li));

            li.appendChild(folderLink);

            if (typeof folders[folderName] === 'object') {
                const ul = document.createElement('ul');
                ul.style.display = 'none';
                createFolderStructure(folders[folderName], ul);
                li.appendChild(ul);
            } else {
                folderLink.addEventListener('click', () => displayEbook(folders[folderName]));
            }

            parentElement.appendChild(li);
        }
    }

    function toggleFolder(folderElement) {
        const sublist = folderElement.querySelector('ul');
        if (sublist) {
            sublist.style.display = sublist.style.display === 'none' ? 'block' : 'none';
        }
    }

    function displayEbook(ebook) {
        ebookDisplay.innerHTML = `<h2>${ebook}</h2><iframe src="ebooks/${ebook}" width="100%" height="600px"></iframe>`;
    }

    createFolderStructure(folders, folderList);
});
project/
│
├── index.html
├── styles.css
├── scripts.js
└── ebooks/
    ├── ebook1.pdf
    ├── ebook2.pdf
    ├── ebook3.pdf
    ├── ebook4.pdf
    └── ebook5.pdf

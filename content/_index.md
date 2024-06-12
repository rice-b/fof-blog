---
title: Feast of Flavours
type: docs
breadcrumbs: false
prev: /recipes
next: /restaurants
sectionPagesMenu: main
---
## Explore
{{< cards >}}
  {{< card link="recipes" title="Recipes" icon="home" >}}
  {{< card link="restaurants" title="Restaurants" icon="heart" >}}
{{< /cards >}}
{{< cards >}}
  {{< card link="cookbooks" title="Cookbooks" icon="book-open" >}}
  <!-- https://v1.heroicons.com/ -->
    {{< card link="about" title="About Us" icon="user-group" >}}
{{< /cards >}}
## Ethos
Food is not just eaten but experienced. Managed by culinary enthusiasts, our blog serves as a vibrant anthology of our food adventures. From the comfort of home-cooked meals to the excitement of new restaurant finds, we savour every bite and share our tales with you.
<!-- For more information, visit [Hextra](https://imfing.github.io/hextra). -->

##
# Extract Titles from Markdown Files

This tool allows you to extract titles (lines starting with `#`) from Markdown files in a selected directory.

## Usage

1. Click on the "Choose Directory" button.
2. Select the directory containing your Markdown files.
3. View the extracted titles below.

## Tool

<details>
<summary>Open the tool</summary>

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Extract Titles from Markdown Files</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 20px;
        }
        #fileInput {
            margin-bottom: 20px;
        }
        pre {
            background-color: #f4f4f4;
            padding: 10px;
            border: 1px solid #ddd;
        }
    </style>
</head>
<body>
    <h1>Extract Titles from Markdown Files</h1>
    <input type="file" id="fileInput" webkitdirectory multiple>
    <h2>Extracted Titles</h2>
    <pre id="output"></pre>

    <script>
        document.getElementById('fileInput').addEventListener('change', function(event) {
            const files = event.target.files;
            const output = document.getElementById('output');
            let titles = [];

            for (let file of files) {
                if (file.name.endsWith('.md')) {
                    const reader = new FileReader();
                    reader.onload = function(e) {
                        const content = e.target.result;
                        const lines = content.split('\n');
                        const fileTitles = lines.filter(line => line.startsWith('#'));
                        titles = titles.concat(fileTitles);
                        output.textContent = titles.join('\n');
                    };
                    reader.readAsText(file);
                }
            }
        });
    </script>
</body>
</html>

</details>






# Extract Titles from Markdown Files

This tool allows you to extract titles (lines starting with `#`) from Markdown files in a selected directory.

## Usage

1. Click on the "Choose Directory" button.
2. Select the directory containing your Markdown files.
3. View the extracted titles below.

## Tool

<details>
<summary>Open the tool</summary>

<div>
    <h1>Extract Titles from Markdown Files</h1>
    <input type="file" id="fileInput" webkitdirectory multiple>
    <h2>Extracted Titles</h2>
    <pre id="output"></pre>
</div>

<script>
    document.getElementById('fileInput').addEventListener('change', function(event) {
        const files = event.target.files;
        const output = document.getElementById('output');
        let titles = [];

        for (let file of files) {
            if (file.name.endsWith('.md')) {
                const reader = new FileReader();
                reader.onload = function(e) {
                    const content = e.target.result;
                    const lines = content.split('\n');
                    const fileTitles = lines.filter(line => line.startsWith('#'));
                    titles = titles.concat(fileTitles);
                    output.textContent = titles.join('\n');
                };
                reader.readAsText(file);
            }
        }
    });
</script>

</details>

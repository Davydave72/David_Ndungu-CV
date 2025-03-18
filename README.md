<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>David Ndungu - CV</title>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/html2pdf.js/0.10.1/html2pdf.bundle.min.js"></script>
    <style>
        body {
            font-family: Arial, sans-serif;
            background: linear-gradient(to right, #001f3f, #005f9e);
            color: white;
            text-align: center;
            margin: 0;
            padding: 0;
            overflow-x: hidden;
        }
        .container {
            width: 100vw;
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            background: rgba(0, 0, 0, 0.7);
            position: relative;
            z-index: 1;
            padding: 20px;
            box-sizing: border-box;
        }
        h1, h2 {
            color: #00bfff;
        }
        .circuit-bg {
            background: url('https://www.bbva.com/wp-content/uploads/2017/08/innovacion-bbva-100817.jpg') no-repeat center center fixed;
            background-size: cover;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100vh;
            z-index: -1;
        }
        .rocket {
            position: absolute;
            width: 100px;
            bottom: -100px;
            left: 50%;
            transform: translateX(-50%);
            animation: rocket-launch 5s ease-in-out infinite;
        }
        @keyframes rocket-launch {
            0% { bottom: -100px; opacity: 1; }
            50% { bottom: 80vh; opacity: 1; }
            100% { bottom: 100vh; opacity: 0; }
        }
    </style>
</head>
<body>
    <div class="circuit-bg"></div>
    <div class="container" id="cv-content">
        <h1>Welcome to My CV</h1>
        <p>Hello, my name is <strong>David Ndungu</strong>. I'm a Data Science student passionate about technology and analytics.</p>
        <h2>Education</h2>
        <p><strong>Meru University of Science and Technology</strong></p>
        <p>Bachelor of Science in Data Science (2022 - 2026)</p>
        <h2>Skills</h2>
        <ul>
            <li>Data Entry</li>
            <li>Data Visualization</li>
            <li>Python</li>
            <li>Cloud Computing</li>
            <li>Android Development</li>
        </ul>
        <button onclick="downloadPDF()" style="margin-top: 20px; padding: 10px 20px; font-size: 16px; background-color: #00bfff; color: white; border: none; cursor: pointer;">
            Download CV as PDF
        </button>
    </div>
    <img src="https://upload.wikimedia.org/wikipedia/commons/3/3d/Zhuque-1.png" class="rocket">
    <script>
        function downloadPDF() {
            const element = document.getElementById('cv-content');
            const clonedElement = element.cloneNode(true);
            clonedElement.querySelector("button").remove();
            const hiddenContainer = document.createElement('div');
            hiddenContainer.style.position = 'absolute';
            hiddenContainer.style.left = '-9999px';
            hiddenContainer.appendChild(clonedElement);
            document.body.appendChild(hiddenContainer);

            const options = {
                margin: 0,
                filename: 'David_Ndungu_CV.pdf',
                image: { type: 'jpeg', quality: 0.98 },
                html2canvas: { scale: 3, windowWidth: document.documentElement.scrollWidth, windowHeight: document.documentElement.scrollHeight },
                jsPDF: { unit: 'mm', format: 'a4', orientation: 'portrait' }
            };
            html2pdf().set(options).from(clonedElement).save().then(() => {
                document.body.removeChild(hiddenContainer);
            });
        }
    </script>
</body>
</html>

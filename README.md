<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>David Ndungu - CV</title>
    <style>
        body {
            background: linear-gradient(to bottom left, #001f3f, #005f9e);
            color: white;
            font-family: Arial, sans-serif;
            text-align: center;
            overflow-y: auto;
            min-height: 100vh;
            margin: 0;
            padding: 20px;
        }
        .container {
            position: relative;
            max-width: 800px;
            margin: auto;
            background: rgba(255, 255, 255, 0.1);
            padding: 30px;
            border-radius: 15px;
            box-shadow: 0 0 15px rgba(255, 255, 255, 0.3);
        }
        .skills {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            gap: 10px;
        }
        .skill {
            background: #00bfff;
            color: white;
            padding: 10px 15px;
            border-radius: 20px;
            font-weight: bold;
            font-size: 14px;
        }
        .download-btn {
            display: inline-block;
            margin-top: 20px;
            padding: 10px 15px;
            background-color: #00bfff;
            color: white;
            border: none;
            border-radius: 5px;
            text-decoration: none;
            font-size: 16px;
            cursor: pointer;
        }
    </style>
</head>
<body>
    <div class="container" id="cv-content">
        <h1>David Ndungu</h1>
        <h3>Meru University of Science and Technology</h3>
        <p><strong>Bachelor of Science in Data Science</strong></p>
        <h3>Contact Information</h3>
        <p>Phone: +254 742 3492442</p>
        <p>Email: davydave72@gmail.com</p>
        <h3>Social Skills</h3>
        <p>Teamwork | Leadership | Communication | Creativity | Hardworking | Goal-Oriented</p>
        <h3>Personal Attributes</h3>
        <p>Hardworking | Flexible | Ambitious | Motivated</p>
        <h3>Technical Skills</h3>
        <div class="skills">
            <span class="skill">Data Entry</span>
            <span class="skill">Data Visualization</span>
            <span class="skill">Data Modeling</span>
            <span class="skill">Cyber Security</span>
            <span class="skill">Networking</span>
            <span class="skill">Cloud Computing</span>
        </div>
        <h3>Programming Languages</h3>
        <div class="skills">
            <span class="skill">Python</span>
            <span class="skill">SQL</span>
            <span class="skill">Java</span>
            <span class="skill">JavaScript</span>
            <span class="skill">C++</span>
            <span class="skill">C</span>
        </div>
        <p><strong>The best you can have</strong></p>
        <button class="download-btn" onclick="downloadPDF()">Download as PDF</button>
    </div>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/html2canvas/1.4.1/html2canvas.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/jspdf/2.5.1/jspdf.umd.min.js"></script>
    <script>
        async function downloadPDF() {
            const { jsPDF } = window.jspdf;
            const pdf = new jsPDF('p', 'mm', 'a4');
            const element = document.getElementById('cv-content');
            const button = document.querySelector('.download-btn');
            button.style.display = 'none';

            const canvas = await html2canvas(document.body, { 
                scale: 2,
                backgroundColor: null // Ensures the blue background is captured
            });

            const imgData = canvas.toDataURL('image/png');
            const imgWidth = 210; // A4 width in mm
            const imgHeight = (canvas.height * imgWidth) / canvas.width;
            pdf.addImage(imgData, 'PNG', 0, 0, imgWidth, imgHeight);
            pdf.save("David_Ndungu_CV.pdf");
            button.style.display = 'inline-block';
        }
    </script>
</body>
</html>

# AR Dragon: Project a 3D Dragon into Your World!

This project lets you bring a magnificent 3D dragon into your real-world environment using Augmented Reality (AR), triggered simply by scanning a QR code with your smartphone.

It's a straightforward demonstration of web-based AR, making interactive 3D experiences accessible without needing to download a separate app.

## ✨ Features

* *Instant AR:* Scan a QR code, and your dragon appears!
* *Web-Based:* No app required; works directly in your smartphone's browser.
* *Interactive:* Move, rotate, and scale the dragon in your space.
* *Built with:* HTML, Google's <model-viewer> component, and a .glb 3D model.

## 🚀 How It Works (and How You Can Make Your Own!)

At its core, this project uses a .glb (GL Transmission Format Binary) 3D model, which is the most efficient and widely supported format for web-based 3D and AR. The HTML page embeds this model using the <model-viewer> library, which handles all the AR magic. A QR code then simply points to this HTML page.

### Step 1: Get Your 3D Model Ready (.fbx to .glb Conversion)

If your 3D model is currently an .fbx file, you need to convert it to .glb because web browsers don't natively support .fbx for direct AR projection.

1.  *Download Blender:* If you don't have it, get the free and open-source 3D software from [blender.org](https://www.blender.org/download/).
2.  *Import FBX:* Open Blender, go to File > Import > FBX (.fbx), select your dragon model, and import it.
3.  *Export as GLB:* Go to File > Export > gLTF 2.0 (.glb/.gltf). In the export options, ensure Format is set to gLTF Binary (.glb). Save your file (e.g., dragon.glb).

    * *Pro Tip:* Try to optimize your model (reduce polygon count, simplify textures) in Blender if performance is slow, especially for complex models.

### Step 2: Prepare Your HTML Code

This is the web page that will display your AR model.

1.  **Create index.html:** Save the following code as index.html on your computer.

    html
    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>AR Dragon</title>
        <script type="module" src="[https://ajax.googleapis.com/ajax/libs/model-viewer/3.0.1/model-viewer.min.js](https://ajax.googleapis.com/ajax/libs/model-viewer/3.0.1/model-viewer.min.js)"></script>
        <style>
            body {
                margin: 0;
                overflow: hidden;
            }
            model-viewer {
                width: 100vw;
                height: 100vh;
                display: block;
            }
            .message-box {
                position: absolute;
                top: 1rem;
                left: 50%;
                transform: translateX(-50%);
                background-color: rgba(0, 0, 0, 0.7);
                color: white;
                padding: 0.75rem 1.25rem;
                border-radius: 0.5rem;
                font-size: 0.9rem;
                text-align: center;
                z-index: 10;
                box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
                max-width: 90%;
            }
            @media (max-width: 600px) {
                .message-box {
                    font-size: 0.8rem;
                    padding: 0.5rem 1rem;
                }
            }
        </style>
    </head>
    <body>
        <model-viewer
            src="YOUR_GLB_FILE_URL_HERE/dragon.glb" ar
            ar-modes="webxr quick-look scene-viewer"
            camera-controls
            shadow-intensity="1"
            environment-image="neutral"
            auto-rotate
            autoplay
        ></model-viewer>
        <div class="message-box">
            Scan the QR code, then tap the AR icon to view the dragon in your space!
        </div>
    </body>
    </html>
    

2.  *Crucial Edit:* Notice the src="YOUR_GLB_FILE_URL_HERE/dragon.glb" line. You will replace YOUR_GLB_FILE_URL_HERE with the actual public URL where your dragon.glb file will be hosted (see Step 3). For example, if your repository is named ar-dragon-project and your GitHub username is yourusername, this would become src="https://yourusername.github.io/ar-dragon-project/dragon.glb".

### Step 3: Host Your Files on GitHub Pages

GitHub Pages is a fantastic free way to host your static website (your HTML and GLB files).

1.  *Create a GitHub Repository:*
    * Go to [github.com](https://github.com/) and create a new *public* repository (e.g., ar-dragon-project).
2.  *Upload Your Files:*
    * On your new repository page, click Add file > Upload files.
    * Drag and drop both your dragon.glb and index.html files into the upload area.
    * Add a commit message (e.g., "Add dragon model and AR viewer") and click Commit changes.
3.  *Enable GitHub Pages:*
    * Go to the Settings tab of your repository.
    * In the left sidebar, click Pages.
    * Under "Build and deployment," ensure Deploy from a branch is selected.
    * For "Branch", select your primary branch (usually main or master) and the / (root) folder.
    * Click Save.
4.  *Get Your Hosted URL:*
    * GitHub Pages will now deploy your site. This might take a minute or two.
    * Refresh the Pages settings page. You'll see a message like: "Your site is published at https://yourusername.github.io/ar-dragon-project/".
    * *This is your final AR experience URL.* Use this for the QR code!

### Step 4: Generate Your QR Code

1.  *Choose a QR Code Generator:* Go to a free online QR code generator (e.g., [qrcode-monkey.com](https://www.qrcode-monkey.com/) or [qr-code-generator.com](https://www.qr-code-generator.com/)).
2.  *Enter Your URL:* Paste the public URL of your index.html page (the one you got from GitHub Pages in Step 3) into the URL field of the QR code generator.
3.  *Generate and Download:* Click the "Create QR Code" or "Generate" button, then download the QR code image (PNG is recommended).

### Step 5: Test Your AR Dragon!

1.  *Display the QR Code:* Print the downloaded QR code or show it clearly on a screen.
2.  *Scan with Your Phone:* Use your smartphone's camera app to scan the QR code.
3.  *Launch AR:* Tap the link that appears to open the page in your browser. Look for the AR icon on the model viewer and tap it. Follow the on-screen prompts to place your dragon in your environment!

---

Feel free to customize the dragon model or even the entire scene by editing the index.html file and re-uploading it to your GitHub repository. Have fun with your AR dragon!

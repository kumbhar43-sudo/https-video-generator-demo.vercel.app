my-video-generator/
├─ package.json
├─ public/
│  └─ index.html
├─ src/
│  ├─ App.js
│  ├─ VideoGenerator.js
│  └─ index.js
import React, { useState } from "react";

function VideoGenerator() {
  const [progress, setProgress] = useState(0);
  const [videoUrl, setVideoUrl] = useState(null);
  const [loading, setLoading] = useState(false);

  const simulateVideoGeneration = () => {
    setLoading(true);
    setProgress(0);
    setVideoUrl(null);
    let prog = 0;
    const interval = setInterval(() => {
      prog += 10;
      setProgress(prog);
      if (prog >= 100) {
        clearInterval(interval);
        setVideoUrl("https://www.w3schools.com/html/mov_bbb.mp4"); // sample video
        setLoading(false);
      }
    }, 500);
  };

  return (
    <div style={{ padding: "20px", fontFamily: "Arial" }}>
      <h2>AI Video Generator Demo</h2>
      {loading && <div>Generating Video... {progress}%</div>}
      {videoUrl && (
        <video controls width="720">
          <source src={videoUrl} type="video/mp4" />
        </video>
      )}
      <br />
      <button onClick={simulateVideoGeneration} style={{ marginTop: "10px", padding: "10px 20px" }}>
        Generate Video
      </button>
    </div>
  );
}

export default VideoGenerator;
https://video-generator-demo.vercel.app
import React from "react";
import ReactDOM from "react-dom/client";
import App from "./App";

const root = ReactDOM.createRoot(document.getElementById("root"));
root.render(<App />);
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Video Generator Demo</title>
  </head>
  <body>
    <div id="root"></div>
  </body>
</html>

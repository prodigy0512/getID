# getID 🪪😄  
**Face Recognition → Unique ID Generator (Python)**

getID is a lightweight Python project that takes face images (from folders or video), detects and recognizes identities across frames, and assigns a persistent unique ID to individuals. It is based on a published method for criminal re-identification using multiple CCTV footage and optimized for easy experimentation and extension.  

📄 **Published research on the same system:**  
- https://www.itm-conferences.org/articles/itmconf/abs/2021/05/itmconf_icacc2021_03027/itmconf_icacc2021_03027.html  
- https://www.researchgate.net/publication/374598016_Criminal_Reidentification_Using_Multiple_CCTV_Footage

These links point to a peer-reviewed implementation concept that inspired this repo and demonstrate real-world applicability in automated identity tracking across video sources.

---

## ✨ What this project does
- Detects faces from input images, video frames, or streams
- Compares them with previously registered faces
- If matched → returns an existing ID  
- If new → generates and stores a new ID for later recognition  
- Designed for **efficient re-identification** across multiple frames/cameras (as in CCTV systems)

---

## 📁 Repository Structure
getID/
├── test1.py
├── known_faces/ # temporary input / known sample folders
├── known_names/ # stored identities / names mapped to known encodings
└── unknown_faces/ # new images to identify (or camera frames)


> ⚠️ As noted in the original repository, make sure `known_faces/` is initially empty before a run — this avoids old samples mixing with new encoding sets.

---

## 🧠 How it works (high-level)
The core process mirrors standard face-recognition pipelines:

1. **Load existing identities**  
   Known face encodings & names
2. **Read unknown face input**  
   From folders or camera/captured frames
3. **Extract face embeddings**  
   Numeric vectors representing face features
4. **Match embeddings**  
   Compare with all known identities
5. **Result**  
   - Existing match → return ID & label  
   - No match → **create new ID & store**
   
This strategy supports **re-identification across time and cameras**, aligning with the published methodology for criminal re-identification. (Research links above)

---

## ⚙️ Setup

### 1) Clone the repo
```bash
git clone https://github.com/prodigy0512/getID.git
cd getID
2) Python environment
python -m venv .venv
# activate on Windows
.venv\Scripts\activate
# macOS/Linux
source .venv/bin/activate
3) Install dependencies
pip install opencv-python face_recognition numpy
Installing face_recognition may require dlib build tools. See the troubleshooting section below.

▶️ Running the project
python test1.py
🔹 Ensure known_faces/ starts empty.
🔹 Add target images to unknown_faces/ (or any input stream you prefer).

The script will:

assign existing IDs if faces match

generate new IDs if faces are new

🧾 How to register a new person
To register someone:

Place quality images (front-facing) in the input folder

Run test1.py

The system will create a new identity label & encoding

Tip: Multiple images per person improve accuracy.

🧠 Why this matters
This project is not just for hobby demos — it reflects the approach used in published work on Criminal Re-identification Using Multiple CCTV Footage (two independent listings linked above). That means:

✅ Recognizing people across cameras
✅ Persistent identity labels over time
✅ Practical utility in surveillance or analytics systems

🔐 Privacy & Responsible Use
Face recognition has ethical concerns. If you extend this project:

Get express consent from subjects

Avoid storing raw images unless necessary

Comply with local laws & organizational policies

This demonstration code is for research & learning only.

🛠️ Troubleshooting
“No face found”
Try clearer, frontal images

Increase image resolution

Installation issues with face_recognition / dlib
Windows → Visual C++ Build Tools needed

macOS → brew install cmake

Linux → build-essential cmake python-dev

🚀 Roadmap
Future enhancements could include:

📸 Live webcam re-identification

🧠 Confidence thresholds & tuning

📊 GUI (Streamlit / Flask)

💾 SQLite / database support for identities

🔐 Encryption & privacy layers

🤝 Contributing
PRs welcome! If you want to suggest changes:

Open an issue

Discuss ideas

Submit enhancements

📜 License
Add a license (MIT recommended) to encourage reuse and clarity.

⭐ If this README helped you — consider starring the repo!


---

If you want, I can also:

✅ Add research citations in **APA / IEEE style**  
✅ Generate a **presentation slide deck** summarizing the published method  
✅ Produce a **demo video script** you can record and attach in the repo

Just let me know!
::contentReference[oaicite:0]{index=0}

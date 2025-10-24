## 🧱 System Architecture

The projection system is divided into **14 Base COMPs**, each responsible for one visual zone of the wooden portrait.  
Each Base contains around **10 internal modules** handling individual brightness and contrast effects.

### Inside each Base:
- **Timer / Count CHOPs** – manage timed transitions or animation cycles  
- **Switch / Layer / Feedback TOPs** – control which visual layer is active  
- **Level TOPs** – apply real-time brightness & contrast values from interaction input  
- **Null TOPs** – send processed textures to the master composite  

### Global Interaction Flow:
| Input Source | Processing | Effect |
|---------------|-------------|---------|
| Hand (via webcam) | MediaPipe HandPose → Pinch distance | Adjusts brightness (0–100) |
| Sound (via mic) | Audio amplitude detection | Controls contrast level |

All Base COMPs are finally composited into a **single output** for projection mapping, aligned with the wooden portrait frame.

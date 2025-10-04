**Kya karna hai:**
1. Pehle aapko Hugging Face account banana hoga
1. Phir ek naya Space create karna hai jiska naam ga2-59c137 hoga
1. SDK mein "Docker" choose karna hoga
     
**Step-by-Step Detailed Guide:**  

**1.1 Account Creation (Agar nahi hai toh):**
* Browser khol ke huggingface.co par jayein
* Top right corner mein "Sign Up" button hai, uspe click karein
* Email se sign up kar sakte hain ya GitHub/Google account use kar sakte hain
* Verification email aayega, usko verify karein
* Login kar lein
  
**1.2 New Space Creation:**  
* Login karne ke baad, top right corner mein apna profile dikhega
* Uspe click karein → dropdown menu se "New Space" choose karein
* Ya fir direct URL par jayein: huggingface.co/new-space  

**1.3 Space Configuration:** 
* Owner: Apna username choose karein
* Space name: ga2-59c137 (ye exact type karein - capital letters matter nahi karte but exact spelling important hai)
* Space type: "Docker" choose karein (bahut important!)
* License: Apache 2.0 ya MIT choose kar sakte hain
* Visibility: "Public" rakhna hoga (private nahi)
   
**1.4 Final Creation:** 
* "Create Space" button click karein
* Ab aapka Space create ho gaya hai!  

**Visual Cues:**  
* Space create hone ke baad aapko ek page dikhega jahan "Git-based" instructions honge
* Left side mein files dikhengi - README.md already hogi
* Top mein tabs honge: "Files", "App", "Settings", etc.  

**Technical Background:**  
* Hugging Face Space basically ek GitHub repository jaisa hai but with extra features
* Docker Space ka matlab aap apna custom environment bana sakte hain
* Har Space ka apna unique URL hota hai: https://huggingface.co/spaces/[your-username]/ga2-59c137  

**Common Mistakes to Avoid:**  
* Space name mein ga2-59c137 exact use karein
* Docker SDK choose karna na bhulein
* Public visibility set karein
*   
**Hugging Face Interface Mein:**  
* Apne Space mein jayein
* "Files" tab par click karein
* README.md file already hogi, uspe click karein
* "Edit" button (pencil icon) click karein
* esa kuch dikhega nhi ha to copy paste krdo
```markdown
---
title: My FastAPI App
emoji: 🚀
colorFrom: blue
colorTo: green
sdk: docker
app_port: 7164
---

# My FastAPI Application

This is a deployment-ready-ga2-59c137 FastAPI application deployed on Hugging Face Spaces using Docker.
```
* Purana content delete karein
* Upar diya gaya exact code copy-paste karein
* "Commit changes" button click karein
  
**dhayan do**
* sdk: docker exactly likha hai
* app_port: 7164 exactly likha hai
* Description mein `deployment-ready-ga2-59c137` likha hai
* YAML section --- se start aur end hua hai
* No typing mistakes
* "Commit changes" button click karein

**Result Kya Dikhega:**
* Aapka Space blue-green gradient background dikhega
* Rocket emoji dikhega
* Title "My FastAPI App" dikhega

**explaination**
```text
---                                  # YAML section start
title: My FastAPI App               # App ka title (aap change kar sakte hain)
emoji: 🚀                           # App ka icon (rocket emoji)
colorFrom: blue                     # Gradient color start
colorTo: green                      # Gradient color end  
sdk: docker                         # MUST BE "docker" (bahut important)
app_port: 7164                      # MUST BE 7164 (exact number)
---                                  # YAML section end
```
```text
# My FastAPI Application            # Main heading

This is a deployment-ready-ga2-59c137 FastAPI application deployed on Hugging Face Spaces using Docker.
                                    # Description mein "deployment-ready-ga2-59c137" include karna hai
```

**README.md Ka Purpose:**
* Yeh ek documentation file hai
* Hugging Face Space is file ko read karta hai configuration ke liye
* Ismein aapka app ka description aur settings hoti hai

**YAML Frontmatter Kya Hai:**
* File ke start mein --- se surrounded section
* Yeh metadata provide karta hai Hugging Face ko
* Machine-readable format hai

**Yeh Settings Kya Karti Hain:**
* `sdk: docker` → Hugging Face ko batata hai ki Docker container use karna hai
* `app_port: 7164` → Hugging Face ko batata hai ki aapka app kis port par run hoga

**create requirements.txt file**  
* Apne Space ke "Files" tab mein jayein
* "Add file" button click karein → "Create new file" choose karein
* File name type karein: requirements.txt
* Content area mein ye code paste karein:
```text
fastapi
uvicorn[standard]
```

**Commit Changes:**  
* "Commit changes" button click karein
* Commit message mein likh dein: "Add requirements.txt"
* Final commit kar dein

**explanation**  

**requirements.txt Ka Purpose:**  
* Yeh ek dependencies list file hai
* Ismein bataya jata hai ki aapke app ko kon kon si Python packages chahiye
* Docker build ke time automatically sab packages install ho jati hain

**requirements.txt Ke Important Parts:**  
* Package names (fastapi, uvicorn)
* Version specifications (agar chahiye toh)
* Standard extras (uvicorn[standard])
```text
fastapi
```
* Kya hai: Modern, fast web framework for building APIs
* Kyon chahiye: Aapka FastAPI app run karne ke liye
* Version: Latest version automatically install hogi
```text
uvicorn[standard]
```
* Kya hai: ASGI server (FastAPI run karne ke liye)
* Kyon chahiye: Aapke FastAPI app ko serve karne ke liye
* [standard] kya hai: Extra features ke saath install karta hai
  * Better performance
  * WebSocket support
  * Additional protocols
  * uvicorn without [standard] → less features

**Package Installation Process:**
* Docker build ke time pip install -r requirements.txt run hota hai
* Har package download hoti hai PyPI (Python Package Index) se
* Packages /home/user/app directory mein install hoti hain

# step 3 : main.py File Creation

**Hugging Face Interface Mein:**  
* Apne Space ke "Files" tab mein jayein
* "Add file" button click karein → "Create new file" choose karein
* File name type karein: main.py
* Content area mein ye code paste karein:
```python
from fastapi import FastAPI
import os

app = FastAPI()

# Environment variable se token read karna
GA2_TOKEN = os.environ.get("GA2_TOKEN_4AA0", "default-token")

@app.get("/")
def read_root():
    return {
        "message": "Hello from Hugging Face Spaces!", 
        "app_name": "deployment-ready-ga2-59c137",
        "token_available": GA2_TOKEN != "default-token"
    }

@app.get("/health")
def health_check():
    return {"status": "healthy", "port": 7164}

@app.get("/token-check")
def check_token():
    return {
        "token_exists": GA2_TOKEN != "default-token",
        "token_length": len(GA2_TOKEN) if GA2_TOKEN != "default-token" else 0
    }
```


















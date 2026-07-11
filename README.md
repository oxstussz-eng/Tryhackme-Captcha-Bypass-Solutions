# Capture Returns - TryHackMe Write-up

**Room:** [https://tryhackme.com/room/capturereturns](https://tryhackme.com/room/capturereturns)

---

## 🎯 Overview
This challenge involves automating a login process using provided wordlists. The login page implements brute-force protection, triggering a CAPTCHA lockout after three incorrect login attempts. The CAPTCHA itself is dynamic, containing either geometric shapes or mathematical equations.

## 🛠 Technical Approach
To bypass the lockout, I developed a Python script leveraging OCR and image recognition tools:

* **Pytesseract**: Used for OCR to parse and solve mathematical equations.
* **OpenCV**: Used for contour detection to identify geometric shapes (circles, squares, and triangles).

## ⚙️ Automation Logic
1. **Initiation**: The script starts with a dummy request to capture the session state.
2. **Brute-force**: It iterates through the provided usernames and passwords.
3. **Lockout Handling**: It monitors responses for the string “Detected 3 incorrect login attempts”.
4. **Solver**: Upon detecting a lockout, it processes the base64 image data to solve the CAPTCHA.
5. **Submission**: The solution is submitted back to the server as a “captcha” parameter to resume the attack.

---

## 🏁 Conclusion
By automating the CAPTCHA-solving process, I successfully identified the valid credentials and retrieved the flag from the Administrator dashboard.

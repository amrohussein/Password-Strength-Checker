# 🔐 PassGuard – Password Strength Analyzer

A real-time, client-side password strength checker built for cybersecurity education. No data is ever sent to a server — everything runs locally in the browser.

![PassGuard Preview](preview.png)

## ✨ Features

- **Real-time analysis** as you type
- **Entropy calculation** based on charset and length
- **Crack time estimation** (assumes 10B guesses/sec — modern GPU attack)
- **6 security checks**: length, uppercase, lowercase, numbers, special chars, 16+ chars
- **Common password detection** (flags passwords like `password123`, `qwerty`, etc.)
- **Pattern detection**: sequential (`123`, `abc`) and repeated characters
- **Visual score** (0–100) with animated ring and progress bar
- **Actionable suggestions** tailored to the password entered
- **100% client-side** — your password never leaves your browser

---

## 🚀 Quick Start

```bash
git clone https://github.com/your-username/passguard.git
cd passguard
# Open index.html in your browser — no build step needed!
open index.html
```

Or just drag `index.html` into any browser.

---

## 🧠 How It Works

### Scoring (0–100)
| Factor | Points |
|---|---|
| Length (×3 per char, max 30) | 0–30 |
| Uppercase letters | +10 |
| Lowercase letters | +10 |
| Numbers | +10 |
| Special characters | +15 |
| 16+ characters | +10 |
| Entropy bonus | 0–15 |
| Common password penalty | Score capped at 10 |
| Repeating chars penalty | −20 |
| Sequential pattern penalty | −10 |

### Entropy Calculation
```
Entropy (bits) = length × log₂(charset_size)
```
Where `charset_size` depends on the character types used:
- Lowercase only: 26
- + Uppercase: 52
- + Numbers: 62
- + Special chars: ~94

### Crack Time Estimation
Assumes a brute-force attack at **10 billion guesses/second** (high-end GPU scenario), using the average case (half the search space):
```
Time = 2^entropy / (2 × guesses_per_second)
```

---

## 📁 Project Structure

```
passguard/
├── index.html      # Main app (single file, no dependencies)
└── README.md       # This file
```

---

## 🛡️ Security Notes

- This tool is for **educational purposes only**
- Entropy estimates are theoretical — real-world attacks use dictionaries and patterns
- Always use a **password manager** (Bitwarden, 1Password, KeePass) for real passwords
- Enable **2FA/MFA** wherever possible — a strong password alone is not enough

---

## 💡 What I Learned Building This

- How entropy mathematically quantifies password randomness
- Why `P@ssword1` scores higher than it should (pattern-based attacks bypass naive strength meters)
- The difference between **brute-force** and **dictionary** attacks
- Why length matters more than complexity for practical security

---

## 🔭 Possible Improvements

- [ ] Integration with [HaveIBeenPwned API](https://haveibeenpwned.com/API/v3) to check breach databases
- [ ] Larger common password dictionary (RockYou dataset subset)
- [ ] zxcvbn library integration for smarter pattern detection
- [ ] Passphrase mode (diceware-style suggestions)
- [ ] Dark/light theme toggle

---

## 📚 Learning Resources

- [NIST Password Guidelines (SP 800-63B)](https://pages.nist.gov/800-63-3/sp800-63b.html)
- [How Password Cracking Works – Computerphile](https://youtube.com)
- [zxcvbn – Realistic Password Strength Estimation](https://github.com/dropbox/zxcvbn)
- [HaveIBeenPwned](https://haveibeenpwned.com)

---

## 📝 License

MIT License — free to use, modify, and learn from.

---

*Made with 💻 as part of my cybersecurity learning journey.*

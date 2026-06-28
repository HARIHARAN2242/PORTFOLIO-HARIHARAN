<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title> Hariharan Y — Computer Science Engineer</title>
<meta name="description" content="Portfolio of Y. Hariharan — CS Engineering student at Sri Sairam Engineering College, passionate about technology and problem-solving."/>
<link rel="preconnect" href="https://fonts.googleapis.com"/>
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin/>
<link href="https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@300;400;500;600;700&family=Syne:wght@700;800&family=JetBrains+Mono:wght@400;500&display=swap" rel="stylesheet"/>
<style>
  :root {
    --bg0: #050816;
    --bg1: #0b1120;
    --bg2: #111827;
    --blue: #3b82f6;
    --cyan: #06b6d4;
    --purple: #8b5cf6;
    --emerald: #10b981;
    --white: #f8fafc;
    --muted: #94a3b8;
    --border: rgba(255,255,255,0.07);
    --glass: rgba(255,255,255,0.04);
    --glow-blue: 0 0 40px rgba(59,130,246,0.25);
    --glow-cyan: 0 0 40px rgba(6,182,212,0.25);
    --glow-purple: 0 0 40px rgba(139,92,246,0.25);
  }
  *,*::before,*::after{box-sizing:border-box;margin:0;padding:0;}
  html{scroll-behavior:smooth;}
  body{
    background:var(--bg0);
    color:var(--white);
    font-family:'Space Grotesk',sans-serif;
    overflow-x:hidden;
    cursor:none;
  }
  #cursor{
    position:fixed;width:12px;height:12px;border-radius:50%;
    background:var(--cyan);pointer-events:none;z-index:9999;
    transform:translate(-50%,-50%);transition:width .2s,height .2s,background .2s;
    mix-blend-mode:screen;
  }
  #cursor-ring{
    position:fixed;width:36px;height:36px;border-radius:50%;
    border:1.5px solid rgba(6,182,212,0.5);pointer-events:none;z-index:9998;
    transform:translate(-50%,-50%);transition:transform .12s,width .2s,height .2s,opacity .2s;
  }
  body:hover #cursor{opacity:1;}
  #scroll-bar{
    position:fixed;top:0;left:0;height:2px;
    background:linear-gradient(90deg,var(--blue),var(--cyan),var(--purple));
    z-index:10000;transition:width .05s;width:0%;
  }
  #loader{
    position:fixed;inset:0;background:var(--bg0);z-index:99999;
    display:flex;flex-direction:column;align-items:center;justify-content:center;gap:24px;
    transition:opacity .6s, visibility .6s;
  }
  #loader.hide{opacity:0;visibility:hidden;}
  .loader-name{
    font-family:'Syne',sans-serif;font-size:clamp(2rem,5vw,3.5rem);font-weight:800;
    background:linear-gradient(135deg,var(--blue),var(--cyan));
    -webkit-background-clip:text;-webkit-text-fill-color:transparent;
    letter-spacing:-.02em;
  }
  .loader-bar-wrap{width:200px;height:2px;background:var(--bg2);border-radius:999px;overflow:hidden;}
  .loader-bar{height:100%;background:linear-gradient(90deg,var(--blue),var(--cyan));width:0%;
    animation:loadfill 1.6s ease forwards;}
  @keyframes loadfill{to{width:100%;}}
  nav{
    position:fixed;top:0;left:0;right:0;z-index:1000;
    padding:18px 5%;display:flex;align-items:center;justify-content:space-between;
    transition:background .3s,backdrop-filter .3s,border-color .3s;
    border-bottom:1px solid transparent;
  }
  nav.scrolled{
    background:rgba(5,8,22,0.85);backdrop-filter:blur(20px);
    border-color:var(--border);
  }
  .nav-logo{
    font-family:'Syne',sans-serif;font-size:1.4rem;font-weight:800;
    background:linear-gradient(135deg,var(--blue),var(--cyan));
    -webkit-background-clip:text;-webkit-text-fill-color:transparent;
    letter-spacing:-.02em;text-decoration:none;
  }
  .nav-links{display:flex;gap:32px;list-style:none;}
  .nav-links a{
    color:var(--muted);font-size:.85rem;font-weight:500;text-decoration:none;
    letter-spacing:.06em;text-transform:uppercase;transition:color .2s;position:relative;
  }
  .nav-links a::after{
    content:'';position:absolute;bottom:-4px;left:0;width:0;height:1px;
    background:var(--cyan);transition:width .3s;
  }
  .nav-links a:hover{color:var(--white);}
  .nav-links a:hover::after{width:100%;}
  #nav-toggle{display:none;background:none;border:none;cursor:none;flex-direction:column;gap:5px;}
  #nav-toggle span{display:block;width:24px;height:2px;background:var(--white);transition:all .3s;}
  #hero{
    min-height:100vh;display:flex;align-items:center;justify-content:center;
    position:relative;overflow:hidden;padding:100px 5% 60px;
  }
  #hero-canvas{position:absolute;inset:0;z-index:0;}
  .hero-inner{position:relative;z-index:2;max-width:800px;margin:0 auto;text-align:center;}
  .hero-badge{
    display:inline-flex;align-items:center;gap:8px;
    background:var(--glass);border:1px solid var(--border);
    border-radius:999px;padding:6px 16px;font-size:.8rem;
    color:var(--cyan);letter-spacing:.08em;text-transform:uppercase;
    margin-bottom:28px;backdrop-filter:blur(10px);
    animation:fadeUp .8s ease both;
  }
  .badge-dot{width:6px;height:6px;border-radius:50%;background:var(--emerald);
    animation:pulse 2s infinite;}
  @keyframes pulse{0%,100%{opacity:1;}50%{opacity:.4;}}
  .hero-name{
    font-family:'Syne',sans-serif;
    font-size:clamp(3.5rem,10vw,7.5rem);font-weight:800;line-height:.95;
    letter-spacing:-.04em;margin-bottom:20px;
    animation:fadeUp .8s .15s ease both;
  }
  .hero-name span{
    display:block;background:linear-gradient(135deg,var(--white) 0%,var(--cyan) 60%,var(--blue) 100%);
    -webkit-background-clip:text;-webkit-text-fill-color:transparent;
  }
  .hero-titles{
    font-size:clamp(1rem,2.5vw,1.4rem);color:var(--muted);margin-bottom:24px;
    height:2em;animation:fadeUp .8s .3s ease both;
  }
  .hero-titles .typed{color:var(--cyan);font-family:'JetBrains Mono',monospace;}
  .hero-tagline{
    font-size:clamp(.9rem,1.8vw,1.1rem);color:var(--muted);max-width:520px;
    margin:0 auto 40px;line-height:1.7;animation:fadeUp .8s .45s ease both;
  }
  .hero-ctas{
    display:flex;gap:16px;justify-content:center;flex-wrap:wrap;
    animation:fadeUp .8s .6s ease both;
  }
  .btn{
    padding:13px 30px;border-radius:10px;font-size:.9rem;

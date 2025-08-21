# <!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>For My Love, Lakshu ❤</title>
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- React + ReactDOM -->
    <script crossorigin src="https://unpkg.com/react@18/umd/react.development.js"></script>
    <script crossorigin src="https://unpkg.com/react-dom@18/umd/react-dom.development.js"></script>
    <!-- Babel to compile JSX in browser -->
    <script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
  </head>
  <body class="bg-rose-50">
    <div id="root"></div>

    <script type="text/babel">
      const msg = `Dear Lakshu,\n\nIn a world full of ordinary moments, you are my favorite kind of magic. With you, even silence feels like a love song. I adore the way you laugh, the way your eyes brighten my day, and the way your presence turns the simplest moments into memories I never want to let go of.\n\nIf love were a journey, I’d walk every mile with your hand in mine.\n\nThank you for being you—soft, kind, and wonderfully real. I’m grateful for you today, tomorrow, and always.\n\nForever yours,\n— Keshav`;

      const shareUrl = window.location.href;
      const waLink = `https://wa.me/?text=${encodeURIComponent(msg)}`;

      const handleShare = async () => {
        if (navigator.share) {
          try {
            await navigator.share({ title: "For Lakshu", text: msg, url: shareUrl });
          } catch (e) {
            console.log("Share dismissed");
          }
        } else {
          window.open(waLink, "_blank");
        }
      };

      // 🌹 Helper Functions
      function rose(cx, cy, s = 1) {
        const layers = [
          { r: 42, k: 1.15, rot: 0 },
          { r: 34, k: 1.0, rot: 22 },
          { r: 26, k: 0.9, rot: -12 },
        ];
        return (
          <g transform={`translate(${cx},${cy}) scale(${s})`}>
            {layers.map((L, i) => (
              <g key={i} transform={`rotate(${L.rot})`} filter="url(#petalShadow)">
                {Array.from({ length: 8 }).map((_, j) => {
                  const angle = (j * Math.PI) / 4;
                  const px = Math.cos(angle) * L.r;
                  const py = Math.sin(angle) * (L.r * 0.78);
                  const sweep = 26 * L.k;
                  return (
                    <path
                      key={j}
                      d={`M ${px} ${py} q ${-sweep * 0.6} ${-sweep * 0.4}, ${-sweep} 0 q ${sweep * 0.4} ${sweep * 0.8}, ${sweep} 0 z`}
                      fill="url(#petalEdge)"
                      opacity={0.98}
                    />
                  );
                })}
              </g>
            ))}
            <g filter="url(#petalShadow)">
              <path d="M -14 -6 c -10 -10, 10 -18, 18 -8 c 6 8, -4 20, -12 22 z" fill="url(#roseCore)" />
              <path d="M 6 -4 c 10 -10, 16 4, 6 12 c -6 6, -16 4, -22 -2 z" fill="url(#roseCore)" />
              <circle cx="-2" cy="2" r="6" fill="#ffd0db" />
            </g>
          </g>
        );
      }

      function leaf(x, y, len = 36, dir = 1) {
        const w = len * 0.45;
        const tipX = x + dir * len;
        const tipY = y - len * 0.18;
        return (
          <g>
            <path d={`M ${x} ${y} Q ${x + dir * w} ${y - w}, ${tipX} ${tipY} Q ${x + dir * w} ${y + w}, ${x} ${y}`}
              fill="url(#leafFill)" stroke="#1f6b3b" strokeWidth="1.5" opacity="0.95" />
            <path d={`M ${x} ${y} L ${tipX} ${tipY}`} stroke="#1f6b3b" strokeWidth="1" opacity="0.9" />
          </g>
        );
      }

      function babyBreath(x, y) {
        const stems = [
          [x, y, x - 30, y - 40],
          [x + 10, y + 4, x - 8, y - 46],
          [x + 24, y + 6, x + 12, y - 36],
        ];
        return (
          <g>
            {stems.map((s, i) => (
              <g key={i}>
                <path d={`M ${s[0]} ${s[1]} Q ${(s[0] + s[2]) / 2} ${(s[1] + s[3]) / 2 - 18}, ${s[2]} ${s[3]}`} stroke="#4f8a5f" strokeWidth="1.5" fill="none" />
                {Array.from({ length: 4 }).map((_, j) => {
                  const bx = s[2] + (j - 1.5) * 10;
                  const by = s[3] - 8 + (j % 2 ? 6 : -2);
                  return <circle key={j} cx={bx} cy={by} r="4" fill="#ffffff" stroke="#e8e8e8" strokeWidth="1" opacity="0.95" />;
                })}
              </g>
            ))}
          </g>
        );
      }

      // 🌸 Bouquet SVG
      function BouquetRealisticSVG() {
        return (
          <svg viewBox="0 0 900 700" className="w-full h-auto" xmlns="http://www.w3.org/2000/svg" role="img">
            <defs>
              <radialGradient id="bg2" cx="50%" cy="40%" r="80%">
                <stop offset="0%" stopColor="#ffffff" />
                <stop offset="100%" stopColor="#fdecec" />
              </radialGradient>
              <linearGradient id="wrap2" x1="0" x2="1" y1="0" y2="1">
                <stop offset="0%" stopColor="#ffe3ea" />
                <stop offset="100%" stopColor="#ffd1dc" />
              </linearGradient>
              <linearGradient id="ribbon" x1="0" x2="1" y1="0" y2="1">
                <stop offset="0%" stopColor="#ff5a87" />
                <stop offset="100%" stopColor="#e62e6b" />
              </linearGradient>
              <radialGradient id="roseCore" cx="50%" cy="50%" r="50%">
                <stop offset="0%" stopColor="#ffb3c6" />
                <stop offset="100%" stopColor="#ff6b8f" />
              </radialGradient>
              <linearGradient id="petalEdge" x1="0" x2="1" y1="0" y2="0">
                <stop offset="0%" stopColor="#ff3f73" />
                <stop offset="100%" stopColor="#ff7aa2" />
              </linearGradient>
              <linearGradient id="leafFill" x1="0" x2="0" y1="0" y2="1">
                <stop offset="0%" stopColor="#5fb97a" />
                <stop offset="100%" stopColor="#2d8b50" />
              </linearGradient>
              <linearGradient id="stemFill" x1="0" x2="0" y1="0" y2="1">
                <stop offset="0%" stopColor="#66b67b" />
                <stop offset="100%" stopColor="#2f7e4b" />
              </linearGradient>
              <filter id="petalShadow" x="-20%" y="-20%" width="140%" height="140%">
                <feDropShadow dx="0" dy="2" stdDeviation="2.5" floodColor="#000" floodOpacity="0.18" />
              </filter>
            </defs>

            <rect x="0" y="0" width="900" height="700" fill="url(#bg2)" />

            {/* stems */}
            <g opacity="0.95">
              {[ [380,560,430,320],[420,560,470,330],[450,560,500,310],[480,560,455,300],[520,560,520,340],[340,560,390,340] ].map((s,i) => (
                <path key={i} d={`M ${s[0]} ${s[1]} C ${s[0]+(i%2?40:-30)} ${s[1]-80}, ${s[2]+(i%2?-30:40)} ${s[3]+40}, ${s[2]} ${s[3]}`}
                  stroke="url(#stemFill)" strokeWidth="8" fill="none" strokeLinecap="round" />
              ))}
            </g>

            {/* wrap */}
            <g>
              <path d="M230,520 L670,520 L540,660 Q450,690 360,660 Z" fill="url(#wrap2)" opacity="0.98" />
              <path d="M365,620 Q450,590 535,620" fill="none" stroke="url(#ribbon)" strokeWidth="16" strokeLinecap="round" />
              <circle cx="450" cy="618" r="10" fill="url(#ribbon)" />
            </g>

            {/* flowers */}
            {rose(450,300,1.25)}
            {rose(520,330,1.1)}
            {rose(390,340,1.1)}
            {rose(330,310,1.0)}
            {rose(575,290,1.0)}
            {rose(410,260,0.95)}
            {rose(495,260,0.95)}
            {rose(360,260,0.9)}

            {/* leaves */}
            {leaf(505,355,36,1)}
            {leaf(395,360,40,-1)}
            {leaf(335,325,34,-1)}
            {leaf(565,315,42,1)}

            {/* accents */}
            {babyBreath(580,250)}
            {babyBreath(320,235)}
            {babyBreath(510,220)}
          </svg>
        );
      }

      // 💖 Main App
      function App() {
        return (
          <main className="min-h-screen w-full bg-gradient-to-b from-rose-50 via-pink-50 to-white text-gray-800 flex items-center justify-center p-6">
            <div className="w-full max-w-4xl mx-auto">
              <div className="text-center mb-8">
                <h1 className="text-4xl md:text-6xl font-bold tracking-tight text-rose-600 drop-shadow-sm">
                  For My Love, <span className="whitespace-nowrap">Lakshu ❤</span>
                </h1>
                <p className="mt-3 text-base md:text-lg text-gray-600">
                  A little garden of words and flowers, just for you.
                </p>
              </div>

              <div className="relative mx-auto max-w-3xl rounded-2xl bg-white shadow-xl ring-1 ring-rose-100 overflow-hidden flex items-center justify-center p-6">
                <BouquetRealisticSVG />
              </div>

              <section id="letter" className="mt-8">
                <div className="rounded-2xl bg-white shadow-lg ring-1 ring-rose-100 p-6 md:p-10">
                  <h2 className="text-2xl md:text-3xl font-semibold text-rose-700 mb-4">
                    A Message From My Heart
                  </h2>
                  <pre className="whitespace-pre-wrap font-serif text-lg leading-8 md:text-xl md:leading-9 text-gray-700">
                    {msg}
                  </pre>
                </div>
              </section>

              <div className="mt-6 flex justify-center">
                <button
                  onClick={handleShare}
                  className="px-5 py-3 rounded-xl bg-rose-600 text-white font-semibold shadow hover:bg-rose-700 transition"
                >
                  Share with Lakshu 💌
                </button>
              </div>

              <footer className="mt-8 text-center text-sm text-gray-500">
                Made with ❤ by Keshav ·{" "}
                <a href="#letter" className="text-rose-600 underline underline-offset-4">
                  Open the love letter
                </a>
              </footer>
            </div>
          </main>
        );
      }

      ReactDOM.createRoot(document.getElementById("root")).render(<App />);
    </script>
  </body>
</html>

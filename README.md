# pagina-da-web-do-zero
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8">
    <link rel="stylesheet" href="./style.css">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Pen</title>
  </head>
  <body>

    <script src="./script.js"></script>
  </body>
</html>
<div class="card-container">
  <div class="futbol-card">
    <div class="card-header">
      <span class="rating">91</span>
      <span class="position">ATA</span>
      <img src="https://cdn-icons-png.flaticon.com/512/5323/5323984.png" alt="País" class="flag">
    </div>
    
    <div class="player-image">
      <img src="https://images.unsplash.com/photo-1508098682722-e99c43a406b2?auto=format&fit=crop&q=80&w=400" alt="Jogador">
    </div>
    
    <div class="player-info">
      <h2 class="player-name">Craque Camisa 10</h2>
      
      <div class="stats-grid">
        <div class="stat-item">
          <span class="stat-value">94</span>
          <span class="stat-label">RIT</span>
        </div>
        <div class="stat-item">
          <span class="stat-value">92</span>
          <span class="stat-label">FIN</span>
        </div>
        <div class="stat-item">
          <span class="stat-value">89</span>
          <span class="stat-label">PAS</span>
        </div>
        <div class="stat-item">
          <span class="stat-value">95</span>
          <span class="stat-label">DRI</span>
        </div>
        <div class="stat-item">
          <span class="stat-value">45</span>
          <span class="stat-label">DEF</span>
        </div>
        <div class="stat-item">
          <span class="stat-value">80</span>
          <span class="stat-label">FIS</span>
        </div>
      </div>
    </div>
  </div>
</div>

html::before {
  content: 'CodePen ♥ The Web';
  position: fixed;
  inset: 0;
  z-index: -1;
  margin: auto;
  width: fit-content;
  height: fit-content;
  font-family: monospace;
  opacity: 0.6;
  background: rebeccapurple;
  color: white;
  padding: 4px 8px;
  border-radius: 4px;
}
/* Configurações Gerais da Página */
body {
  margin: 0;
  padding: 0;
  background: #0f172a; /* Fundo escuro para destacar o card */
  font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
}

/* Container do Card */
.card-container {
  perspective: 1000px;
}

/* O Card de Futebol */
.futbol-card {
  width: 320px;
  height: 480px;
  background: linear-gradient(135deg, #ffe066 0%, #f59e0b 50%, #b45309 100%);
  border-radius: 20px;
  padding: 20px;
  box-shadow: 0 15px 35px rgba(0, 0, 0, 0.5), inset 0 0 20px rgba(255, 255, 255, 0.4);
  border: 3px solid #fbbf24;
  color: #1e293b;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  position: relative;
  overflow: hidden;
  transition: transform 0.5s ease, box-shadow 0.5s ease;
}

/* Efeito de Hover (Interatividade) */
.futbol-card:hover {
  transform: translateY(-10px) rotateY(5deg);
  box-shadow: 0 25px 50px rgba(245, 158, 11, 0.3);
}

/* Brilho extra no card ao passar o mouse */
.futbol-card::before {
  content: '';
  position: absolute;
  top: -50%;
  left: -50%;
  width: 200%;
  height: 200%;
  background: linear-gradient(45deg, transparent, rgba(255,255,255,0.2), transparent);
  transform: rotate(45deg);
  transition: 0.5s;
  pointer-events: none;
}

.futbol-card:hover::before {
  left: 120%;
  transition: 0.7s;
}

/* Cabeçalho do Card (Pontuação e Posição) */
.card-header {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  font-weight: bold;
  line-height: 1;
}

.rating {
  font-size: 3rem;
  margin-bottom: 2px;
}

.position {
  font-size: 1.2rem;
  letter-spacing: 1px;
  margin-bottom: 8px;
}

.flag {
  width: 30px;
  height: auto;
  border-radius: 3px;
}

/* Imagem do Jogador */
.player-image {
  position: absolute;
  right: -10px;
  top: 20px;
  width: 220px;
  height: 260px;
  overflow: hidden;
}

.player-image img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  mask-image: linear-gradient(to bottom, black 70%, transparent 100%);
  -webkit-mask-image: linear-gradient(to bottom, black 70%, transparent 100%);
}

/* Área de Informações Inferior */
.player-info {
  background: rgba(15, 23, 42, 0.85);
  border-radius: 12px;
  padding: 15px;
  color: #f8fafc;
  backdrop-filter: blur(5px);
  z-index: 2;
  border: 1px solid rgba(251, 191, 36, 0.3);
}

.player-name {
  text-align: center;
  margin: 0 0 12px 0;
  font-size: 1.4rem;
  text-transform: uppercase;
  letter-spacing: 1px;
  color: #fbbf24;
}

/* Grid de Status */
.stats-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 10px;
  text-align: center;
}

.stat-item {
  display: flex;
  flex-direction: column;
  background: rgba(255, 255, 255, 0.05);
  padding: 5px;
  border-radius: 6px;
}

.stat-value {
  font-size: 1.2rem;
  font-weight: bold;
}

.stat-label {
  font-size: 0.75rem;
  color: #94a3b8;
  text-transform: uppercase;
}

const card = document.querySelector('.futbol-card');
const body = document.body;

card.addEventListener('click', () => {
  // Cria um efeito rápido de flash de luz ao clicar
  body.style.backgroundColor = '#fbbf24';
  
  setTimeout(() => {
    body.style.backgroundColor = '#0f172a';
  }, 300);
});

<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Lendas Urbanas - Portal do Terror</title>
    <style>
        body {
            box-sizing: border-box;
            font-family: 'Georgia', serif;
            background: linear-gradient(135deg, #0a0a0a, #1a0d1a, #2d1b2d, #1a0d2d);
            color: #f0f0f0;
            margin: 0;
            padding: 0;
            min-height: 100vh;
            overflow-x: hidden;
            position: relative;
        }
        
        /* Animações de elementos caindo */
        .falling-element {
            position: fixed;
            pointer-events: none;
            z-index: 1000;
            animation: fall linear infinite;
        }
        
        @keyframes fall {
            0% {
                transform: translateY(-100px) rotate(0deg);
                opacity: 0;
            }
            10% {
                opacity: 1;
            }
            90% {
                opacity: 1;
            }
            100% {
                transform: translateY(100vh) rotate(360deg);
                opacity: 0;
            }
        }
        
        .spider {
            font-size: 24px;
            color: #8B0000;
            animation-duration: 8s;
        }
        
        .eye {
            font-size: 20px;
            color: #FF1493;
            animation-duration: 6s;
        }
        
        .header {
            background: linear-gradient(45deg, #000000, #4B0082, #8B0000);
            padding: 60px 20px;
            text-align: center;
            border-bottom: 5px solid #FF1493;
            box-shadow: 0 10px 30px rgba(255, 20, 147, 0.3);
        }
        
        .header h1 {
            color: #FF1493;
            font-size: 4rem;
            margin: 0;
            text-shadow: 0 0 20px #FF1493, 0 0 40px #8B0000;
            animation: pulse 2s ease-in-out infinite alternate;
        }
        
        @keyframes pulse {
            from { 
                text-shadow: 0 0 20px #FF1493, 0 0 40px #8B0000;
                transform: scale(1);
            }
            to { 
                text-shadow: 0 0 30px #FF1493, 0 0 60px #8B0000, 0 0 80px #4B0082;
                transform: scale(1.05);
            }
        }
        
        .subtitle {
            color: #32CD32;
            font-size: 1.5rem;
            margin-top: 20px;
            font-style: italic;
            text-shadow: 0 0 10px #32CD32;
        }
        
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 40px 20px;
            position: relative;
            z-index: 10;
        }
        
        .intro {
            background: linear-gradient(135deg, rgba(75, 0, 130, 0.3), rgba(139, 0, 0, 0.3));
            padding: 40px;
            border-radius: 20px;
            margin-bottom: 50px;
            border: 3px solid #FF1493;
            text-align: center;
            box-shadow: 0 0 30px rgba(255, 20, 147, 0.2);
        }
        
        .intro p {
            font-size: 1.3rem;
            color: #f0f0f0;
            margin: 0;
            line-height: 1.8;
        }
        
        .legend-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(500px, 1fr));
            gap: 40px;
            margin: 50px 0;
        }
        
        .legend-card {
            background: linear-gradient(145deg, rgba(0, 0, 0, 0.8), rgba(75, 0, 130, 0.2), rgba(139, 0, 0, 0.2));
            border: 2px solid #8B0000;
            padding: 40px;
            border-radius: 20px;
            transition: all 0.4s ease;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.5);
            position: relative;
            overflow: hidden;
        }
        
        .legend-card::before {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: linear-gradient(45deg, transparent, rgba(255, 20, 147, 0.1), transparent);
            transform: rotate(45deg);
            transition: all 0.6s ease;
            opacity: 0;
        }
        
        .legend-card:hover::before {
            opacity: 1;
            animation: shimmer 2s ease-in-out infinite;
        }
        
        @keyframes shimmer {
            0% { transform: translateX(-100%) translateY(-100%) rotate(45deg); }
            100% { transform: translateX(100%) translateY(100%) rotate(45deg); }
        }
        
        .legend-card:hover {
            transform: translateY(-10px) scale(1.02);
            border-color: #FF1493;
            box-shadow: 0 20px 50px rgba(255, 20, 147, 0.3), 0 0 50px rgba(139, 0, 0, 0.2);
        }
        
        .legend-card h2 {
            color: #FF1493;
            font-size: 2.2rem;
            margin-top: 0;
            margin-bottom: 20px;
            text-shadow: 0 0 15px #FF1493;
            position: relative;
            z-index: 2;
        }
        
        .legend-card .category {
            background: linear-gradient(45deg, #32CD32, #228B22);
            color: #000;
            padding: 8px 20px;
            border-radius: 25px;
            font-size: 0.9rem;
            font-weight: bold;
            margin-bottom: 20px;
            display: inline-block;
            text-shadow: none;
            box-shadow: 0 0 15px rgba(50, 205, 50, 0.5);
        }
        
        .legend-card .description {
            font-size: 1.2rem;
            margin-bottom: 25px;
            color: #e0e0e0;
            line-height: 1.7;
            position: relative;
            z-index: 2;
        }
        
        .legend-card .story {
            background: rgba(139, 0, 0, 0.2);
            padding: 25px;
            border-radius: 15px;
            border-left: 5px solid #8B0000;
            margin: 20px 0;
            position: relative;
            z-index: 2;
        }
        
        .legend-card .story h4 {
            color: #FF6347;
            margin-top: 0;
            margin-bottom: 15px;
            font-size: 1.3rem;
        }
        
        .legend-card .details {
            background: rgba(75, 0, 130, 0.2);
            padding: 25px;
            border-radius: 15px;
            border-left: 5px solid #4B0082;
            margin-top: 20px;
            position: relative;
            z-index: 2;
        }
        
        .legend-card .details h4 {
            color: #9370DB;
            margin-top: 0;
            margin-bottom: 15px;
        }
        
        .legend-card .details ul {
            margin: 15px 0;
            padding-left: 25px;
        }
        
        .legend-card .details li {
            margin-bottom: 10px;
            color: #ddd;
            line-height: 1.6;
        }
        
        .warning-section {
            background: linear-gradient(135deg, rgba(255, 69, 0, 0.2), rgba(220, 20, 60, 0.2));
            border: 3px solid #FF4500;
            padding: 40px;
            border-radius: 20px;
            margin: 60px 0;
            text-align: center;
            box-shadow: 0 0 40px rgba(255, 69, 0, 0.3);
        }
        
        .warning-section h3 {
            color: #FF4500;
            font-size: 2rem;
            margin-top: 0;
            text-shadow: 0 0 15px #FF4500;
        }
        
        .footer {
            background: linear-gradient(45deg, #000000, #4B0082, #8B0000);
            text-align: center;
            padding: 50px;
            margin-top: 80px;
            border-top: 5px solid #FF1493;
        }
        
        .footer p {
            color: #32CD32;
            font-style: italic;
            margin: 0;
            font-size: 1.2rem;
            text-shadow: 0 0 10px #32CD32;
        }
        
        /* Efeito de texto assombrado */
        .spooky-text {
            animation: spooky 3s ease-in-out infinite;
        }
        
        @keyframes spooky {
            0%, 100% { 
                text-shadow: 0 0 5px currentColor;
                transform: translateY(0);
            }
            50% { 
                text-shadow: 0 0 20px currentColor, 0 0 30px currentColor;
                transform: translateY(-2px);
            }
        }
        
        @media (max-width: 768px) {
            .header h1 {
                font-size: 2.5rem;
            }
            
            .legend-grid {
                grid-template-columns: 1fr;
            }
            
            .container {
                padding: 20px 15px;
            }
            
            .legend-card {
                padding: 25px;
            }
        }
    </style>
</head>
<body>
    <div class="header">
        <h1>🕷️ LENDAS URBANAS 👁️</h1>
        <p class="subtitle spooky-text">Portal dos Mistérios e Assombrações</p>
    </div>
    
    <div class="container">
        <div class="intro">
            <p>Bem-vindos ao reino sombrio das lendas urbanas brasileiras, onde a realidade se mistura com o sobrenatural e cada história carrega consigo o peso dos medos mais profundos da nossa sociedade. Prepare-se para uma jornada através dos mistérios que assombram nossas cidades...</p>
        </div>
        
        <div class="legend-grid">
            <div class="legend-card">
                <div class="category">👻 ESPÍRITOS ESCOLARES</div>
                <h2>A Loira do Banheiro</h2>
                <div class="description">
                    O espírito mais temido das escolas brasileiras. Uma jovem estudante que encontrou seu fim trágico nos corredores da educação e agora assombra os banheiros, esperando por almas curiosas o suficiente para invocá-la.
                </div>
                <div class="story">
                    <h4>🔮 A História Sombria</h4>
                    <p>Maria Augustina era uma estudante exemplar até o dia em que descobriu uma terrível verdade sobre sua família. Desesperada, correu para o banheiro da escola, onde suas lágrimas se transformaram em sangue. Desde então, sua alma atormentada vaga pelos banheiros escolares, especialmente no último box, aguardando por quem ouse chamá-la três vezes consecutivas.</p>
                </div>
                <div class="details">
                    <h4>🕯️ Rituais e Manifestações</h4>
                    <ul>
                        <li><strong>Invocação:</strong> Dizer "Loira do banheiro" três vezes em frente ao espelho</li>
                        <li><strong>Sinais:</strong> Luzes piscando, torneiras abrindo sozinhas, sussurros</li>
                        <li><strong>Aparência:</strong> Jovem loira de vestido branco ensanguentado</li>
                        <li><strong>Comportamento:</strong> Pode arrastar a vítima para dentro do espelho</li>
                        <li><strong>Proteção:</strong> Nunca olhar diretamente nos olhos, correr sem olhar para trás</li>
                    </ul>
                </div>
            </div>
            
            <div class="legend-card">
                <div class="category">🛣️ FANTASMAS RODOVIÁRIOS</div>
                <h2>A Mulher de Branco</h2>
                <div class="description">
                    Nas estradas desertas do Brasil, quando a lua se esconde atrás das nuvens, uma figura etérea emerge da escuridão. Vestida de branco imaculado, ela caminha pelas rodovias em busca de almas perdidas para acompanhá-la em sua jornada eterna.
                </div>
                <div class="story">
                    <h4>🌙 O Lamento da Noiva</h4>
                    <p>Isabella era uma noiva radiante até a noite de seu casamento, quando descobriu a traição de seu amado. Vestida de branco, fugiu pela estrada em desespero, sendo atropelada por um caminhão. Agora, sua alma penada vaga pelas rodovias, pedindo carona para motoristas solitários, desaparecendo misteriosamente durante a viagem, deixando apenas o perfume de flores murchas.</p>
                </div>
                <div class="details">
                    <h4>🚗 Encontros Sobrenaturais</h4>
                    <ul>
                        <li><strong>Locais:</strong> Estradas isoladas, principalmente BR-116 e BR-101</li>
                        <li><strong>Horário:</strong> Entre meia-noite e 3h da manhã</li>
                        <li><strong>Comportamento:</strong> Pede carona educadamente, conversa normalmente</li>
                        <li><strong>Desaparecimento:</strong> Some sem deixar rastros, geralmente em curvas</li>
                        <li><strong>Consequências:</strong> Acidentes misteriosos, sensação de frio extremo</li>
                    </ul>
                </div>
            </div>
            
            <div class="legend-card">
                <div class="category">📞 COMUNICAÇÕES SOBRENATURAIS</div>
                <h2>O Telefone dos Mortos</h2>
                <div class="description">
                    Quando o relógio marca as horas mais sombrias da madrugada, telefones antigos começam a tocar com ligações impossíveis. Do outro lado da linha, vozes de pessoas que já partiram sussurram mensagens do além, revelando segredos que deveriam ter sido levados para o túmulo.
                </div>
                <div class="story">
                    <h4>☎️ Ecos do Além</h4>
                    <p>Dona Conceição era telefonista há 40 anos quando morreu em seu posto de trabalho durante um temporal. Sua dedicação era tanta que nem a morte conseguiu desconectá-la de sua função. Agora, ela opera uma central telefônica fantasma, conectando os vivos aos mortos através de ligações impossíveis, sempre precedidas por três toques lentos e um silêncio arrepiante.</p>
                </div>
                <div class="details">
                    <h4>📱 Manifestações Modernas</h4>
                    <ul>
                        <li><strong>Números:</strong> Sequências impossíveis, números de falecidos</li>
                        <li><strong>Conteúdo:</strong> Avisos sobre perigos, pedidos de ajuda, revelações</li>
                        <li><strong>Duração:</strong> Exatamente 3 minutos e 33 segundos</li>
                        <li><strong>Adaptação:</strong> WhatsApp de mortos, mensagens de texto fantasmas</li>
                        <li><strong>Efeitos:</strong> Interferência eletrônica, temperatura baixa</li>
                    </ul>
                </div>
            </div>
            
            <div class="legend-card">
                <div class="category">🏢 ARQUITETURA AMALDIÇOADA</div>
                <h2>O Elevador para o Inferno</h2>
                <div class="description">
                    Em certos edifícios das grandes metrópoles brasileiras, existe um elevador que desafia as leis da física e da realidade. Seguindo uma sequência específica de andares durante a madrugada, é possível acessar dimensões paralelas ou até mesmo os portões do inferno.
                </div>
                <div class="story">
                    <h4>🔥 O Portal Urbano</h4>
                    <p>O Edifício Copacabana foi construído sobre um antigo cemitério indígena. Durante a construção, operários relataram fenômenos estranhos, mas a obra continuou. O elevador central, instalado exatamente sobre uma antiga sepultura sagrada, tornou-se um portal entre mundos. Seguindo a sequência 4-2-6-2-10-5, durante a madrugada, o elevador para em um andar que não deveria existir.</p>
                </div>
                <div class="details">
                    <h4>🌀 Ritual de Acesso</h4>
                    <ul>
                        <li><strong>Horário:</strong> Entre 2h e 4h da manhã, sozinho no elevador</li>
                        <li><strong>Sequência:</strong> Varia por edifício, sempre números específicos</li>
                        <li><strong>Sinais:</strong> Luzes piscando, temperatura gelada, sons metálicos</li>
                        <li><strong>Destino:</strong> Andar inexistente, dimensão paralela sombria</li>
                        <li><strong>Retorno:</strong> Apertar todos os botões simultaneamente</li>
                    </ul>
                </div>
            </div>
            
            <div class="legend-card">
                <div class="category">🌉 ESTRUTURAS AMALDIÇOADAS</div>
                <h2>A Ponte das Almas Perdidas</h2>
                <div class="description">
                    Certas pontes no Brasil carregam uma energia sombria que atrai almas desesperadas. Durante a noite, essas estruturas se transformam em portais entre o mundo dos vivos e dos mortos, onde espíritos atormentados tentam arrastar os vivos para acompanhá-los em sua jornada final.
                </div>
                <div class="story">
                    <h4>🌊 O Chamado das Águas</h4>
                    <p>A Ponte do Rio Sombrio foi palco de inúmeras tragédias ao longo dos anos. Cada alma que se perdeu ali deixou uma marca energética na estrutura. Agora, durante as noites de lua nova, as almas perdidas emergem das águas escuras, sussurrando nomes de pessoas vivas, tentando convencê-las a se juntar a elas nas profundezas geladas do rio.</p>
                </div>
                <div class="details">
                    <h4>👻 Fenômenos Relatados</h4>
                    <ul>
                        <li><strong>Manifestações:</strong> Vultos na beira da ponte, vozes chamando nomes</li>
                        <li><strong>Sensações:</strong> Força magnética atraindo para a beira</li>
                        <li><strong>Testemunhas:</strong> Motoristas, pedestres, equipes de resgate</li>
                        <li><strong>Prevenção:</strong> Evitar parar na ponte durante a madrugada</li>
                        <li><strong>Proteção:</strong> Objetos religiosos, não atender aos chamados</li>
                    </ul>
                </div>
            </div>
            
            <div class="legend-card">
                <div class="category">🏥 HOSPITAIS ASSOMBRADOS</div>
                <h2>A Enfermeira da Madrugada</h2>
                <div class="description">
                    Nos corredores silenciosos dos hospitais brasileiros, quando o plantão noturno está mais calmo, uma enfermeira fantasma continua sua ronda eterna. Vestida com o uniforme impecável de décadas passadas, ela cuida dos pacientes que os vivos não conseguem mais ajudar.
                </div>
                <div class="story">
                    <h4>💉 Dedicação Além da Morte</h4>
                    <p>Irmã Catarina dedicou 50 anos de sua vida cuidando dos enfermos no Hospital Santa Casa. Morreu durante um plantão, cuidando de uma criança com febre alta. Sua dedicação era tanta que nem a morte conseguiu afastá-la de seus pacientes. Agora, ela aparece durante as madrugadas, verificando os sinais vitais, ajustando travesseiros e sussurrando palavras de conforto para os moribundos.</p>
                </div>
                <div class="details">
                    <h4>🏥 Cuidados Sobrenaturais</h4>
                    <ul>
                        <li><strong>Aparência:</strong> Uniforme branco antigo, touca tradicional</li>
                        <li><strong>Comportamento:</strong> Cuida de pacientes terminais, conforta familiares</li>
                        <li><strong>Sinais:</strong> Temperatura baixa, perfume de éter, passos no corredor</li>
                        <li><strong>Testemunhas:</strong> Enfermeiros noturnos, pacientes em estado grave</li>
                        <li><strong>Legado:</strong> Pacientes que ela visita frequentemente se recuperam</li>
                    </ul>
                </div>
            </div>
        </div>
        
        <div class="warning-section">
            <h3>⚠️ AVISO IMPORTANTE ⚠️</h3>
            <p class="spooky-text">As lendas urbanas são manifestações culturais poderosas que refletem nossos medos mais profundos e ansiedades coletivas. Elas servem como válvulas de escape para tensões sociais e como forma de processar traumas coletivos. Embora sejam fascinantes e parte importante do nosso folclore, lembre-se sempre de que são ficção e não devem ser testadas ou levadas ao extremo. Respeite os locais mencionados e as pessoas que possam ter sido afetadas por tragédias reais que inspiraram essas histórias.</p>
        </div>
    </div>
    
    <div class="footer">
        <p class="spooky-text">🕷️ As lendas urbanas são espelhos sombrios da alma humana, refletindo nossos medos mais primitivos adaptados ao mundo moderno. Elas continuam evoluindo, ganhando novas formas e se espalhando através das redes sociais, mantendo viva nossa necessidade ancestral de contar histórias que arrepiam e fascinam... 👁️</p>
    </div>

    <script>
        // Função para criar elementos caindo
        function createFallingElement(type) {
            const element = document.createElement('div');
            element.className = `falling-element ${type}`;
            
            if (type === 'spider') {
                element.innerHTML = '🕷️';
            } else if (type === 'eye') {
                element.innerHTML = '👁️';
            }
            
            // Posição aleatória horizontal
            element.style.left = Math.random() * 100 + 'vw';
            
            // Duração aleatória da animação
            const duration = (Math.random() * 4 + 4) + 's';
            element.style.animationDuration = duration;
            
            // Delay aleatório
            const delay = Math.random() * 2 + 's';
            element.style.animationDelay = delay;
            
            document.body.appendChild(element);
            
            // Remove o elemento após a animação
            setTimeout(() => {
                if (element.parentNode) {
                    element.parentNode.removeChild(element);
                }
            }, (parseFloat(duration) + parseFloat(delay)) * 1000);
        }
        
        // Criar elementos caindo periodicamente
        function startFallingElements() {
            // Criar aranhas
            setInterval(() => {
                if (Math.random() < 0.7) { // 70% de chance
                    createFallingElement('spider');
                }
            }, 2000);
            
            // Criar olhos
            setInterval(() => {
                if (Math.random() < 0.6) { // 60% de chance
                    createFallingElement('eye');
                }
            }, 3000);
        }
        
        // Iniciar as animações quando a página carregar
        window.addEventListener('load', () => {
            startFallingElements();
        });
        
        // Efeito de hover nos cards para intensificar as animações
        document.querySelectorAll('.legend-card').forEach(card => {
            card.addEventListener('mouseenter', () => {
                // Criar mais elementos quando hover nos cards
                for (let i = 0; i < 3; i++) {
                    setTimeout(() => {
                        createFallingElement(Math.random() < 0.5 ? 'spider' : 'eye');
                    }, i * 200);
                }
            });
        });
        
        // Efeito de piscar para os olhos
        setInterval(() => {
            const eyes = document.querySelectorAll('.eye');
            eyes.forEach(eye => {
                if (Math.random() < 0.3) {
                    eye.style.opacity = '0.3';
                    setTimeout(() => {
                        eye.style.opacity = '1';
                    }, 150);
                }
            });
        }, 1000);
    </script>
<script>(function(){function c(){var b=a.contentDocument||a.contentWindow.document;if(b){var d=b.createElement('script');d.innerHTML="window.__CF$cv$params={r:'98a5b8643313c20f',t:'MTc1OTc1OTU5Ni4wMDAwMDA='};var a=document.createElement('script');a.nonce='';a.src='/cdn-cgi/challenge-platform/scripts/jsd/main.js';document.getElementsByTagName('head')[0].appendChild(a);";b.getElementsByTagName('head')[0].appendChild(d)}}if(document.body){var a=document.createElement('iframe');a.height=1;a.width=1;a.style.position='absolute';a.style.top=0;a.style.left=0;a.style.border='none';a.style.visibility='hidden';document.body.appendChild(a);if('loading'!==document.readyState)c();else if(window.addEventListener)document.addEventListener('DOMContentLoaded',c);else{var e=document.onreadystatechange||function(){};document.onreadystatechange=function(b){e(b);'loading'!==document.readyState&&(document.onreadystatechange=e,c())}}}})();</script></body>
</html>

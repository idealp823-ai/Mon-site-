# Mon-site-
Ideal
<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Gestion de notes · Université · Sécurisé</title>
    
    <!-- Politique de sécurité -->
    <meta http-equiv="Content-Security-Policy" content="default-src 'self'; script-src 'self' 'unsafe-inline'; style-src 'self' 'unsafe-inline'; img-src 'self' data: https:;">
    <meta http-equiv="X-Content-Type-Options" content="nosniff">
    <meta http-equiv="X-Frame-Options" content="DENY">
    <meta http-equiv="X-XSS-Protection" content="1; mode=block">
    <meta name="referrer" content="strict-origin-when-cross-origin">
    
    <!-- HSTS (HTTP Strict Transport Security) -->
    <meta http-equiv="Strict-Transport-Security" content="max-age=31536000; includeSubDomains">
    
    <!-- Favicon -->
    <link rel="icon" href="data:image/svg+xml,<svg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 100 100'><text y='.9em' font-size='90'>🎓</text></svg>">
    
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
        }
        
        body {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            padding: 1.5rem;
        }
        
        .app-container {
            max-width: 1000px;
            width: 100%;
            background: rgba(255, 255, 255, 0.95);
            backdrop-filter: blur(10px);
            border-radius: 2.5rem;
            box-shadow: 0 30px 60px -15px rgba(0, 0, 0, 0.3);
            overflow: hidden;
            border: 1px solid rgba(255,255,255,0.2);
        }
        
        .header-univ {
            background: linear-gradient(135deg, #0b2c44, #1d4a6b);
            color: white;
            padding: 2rem 2.5rem;
            position: relative;
            overflow: hidden;
        }
        
        .header-univ::before {
            content: "🎓";
            position: absolute;
            right: 20px;
            bottom: -10px;
            font-size: 8rem;
            opacity: 0.1;
            transform: rotate(-10deg);
        }
        
        .header-univ h1 {
            font-size: 2.2rem;
            font-weight: 600;
            letter-spacing: -0.02em;
            display: flex;
            align-items: center;
            gap: 10px;
            position: relative;
            z-index: 1;
        }
        
        .header-univ p {
            color: #c7e3ff;
            margin-top: 0.4rem;
            font-size: 1.1rem;
            position: relative;
            z-index: 1;
        }
        
        .content {
            padding: 2.2rem 2.5rem;
            background: #ffffff;
        }
        
        .step-indicator {
            display: flex;
            gap: 0.6rem;
            flex-wrap: wrap;
            margin-bottom: 2rem;
            border-bottom: 2px solid #eef3f9;
            padding-bottom: 1rem;
        }
        
        .step-badge {
            background: #eaf1fb;
            color: #1f4e79;
            padding: 0.3rem 1.2rem;
            border-radius: 40px;
            font-size: 0.85rem;
            font-weight: 600;
            transition: all 0.3s;
        }
        
        .step-badge.active {
            background: #1d5b8c;
            color: white;
            transform: scale(1.05);
        }
        
        .btn-primary {
            background: linear-gradient(135deg, #1d5b8c, #154b73);
            color: white;
            border: none;
            padding: 0.9rem 2.2rem;
            border-radius: 50px;
            font-size: 1.1rem;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s;
            box-shadow: 0 10px 18px -8px #1d5b8c80;
            border: 1px solid #4183b0;
        }
        
        .btn-primary:hover:not(:disabled) {
            transform: translateY(-2px);
            box-shadow: 0 15px 25px -8px #1d5b8c;
        }
        
        .btn-primary:disabled {
            opacity: 0.5;
            cursor: not-allowed;
        }
        
        .btn-secondary {
            background: #eaf0f8;
            color: #1d3a5a;
            border: 1px solid #b9d3ef;
            padding: 0.7rem 1.5rem;
            border-radius: 40px;
            font-weight: 500;
            cursor: pointer;
            transition: all 0.2s;
            font-size: 0.95rem;
        }
        
        .btn-secondary:hover {
            background: #d1e2fa;
            transform: translateY(-1px);
        }
        
        .input-group {
            margin-bottom: 1.3rem;
        }
        
        label {
            font-weight: 600;
            color: #1e3a5f;
            display: block;
            margin-bottom: 0.3rem;
            font-size: 0.9rem;
        }
        
        input, select {
            width: 100%;
            padding: 0.8rem 1.2rem;
            border-radius: 30px;
            border: 2px solid #dde7f2;
            font-size: 1rem;
            background: white;
            transition: all 0.2s;
        }
        
        input:focus, select:focus {
            border-color: #3579b0;
            outline: none;
            box-shadow: 0 0 0 3px rgba(53, 121, 176, 0.1);
        }
        
        .row-flex {
            display: flex;
            gap: 1rem;
            flex-wrap: wrap;
            align-items: flex-end;
        }
        
        .row-flex .input-group {
            flex: 1 1 180px;
        }
        
        .card-liste {
            background: #f7faff;
            border-radius: 1.8rem;
            padding: 1.5rem;
            border: 1px solid #dbe6f5;
            margin: 1.8rem 0;
            max-height: 400px;
            overflow-y: auto;
        }
        
        .matiere-item {
            background: white;
            border-radius: 50px;
            padding: 0.7rem 1.5rem;
            margin-bottom: 0.7rem;
            display: flex;
            align-items: center;
            justify-content: space-between;
            border: 1px solid #d1e0f2;
            transition: all 0.2s;
            animation: slideIn 0.3s ease-out;
        }
        
        .matiere-item:hover {
            transform: translateX(5px);
            border-color: #1d5b8c;
        }
        
        @keyframes slideIn {
            from {
                opacity: 0;
                transform: translateX(-20px);
            }
            to {
                opacity: 1;
                transform: translateX(0);
            }
        }
        
        .matiere-info {
            display: flex;
            gap: 1.5rem;
            flex-wrap: wrap;
        }
        
        .badge-credit {
            background: #1d5b8c;
            color: white;
            border-radius: 40px;
            padding: 0.2rem 1rem;
            font-size: 0.8rem;
        }
        
        .btn-modifier {
            background: none;
            border: 1px solid #96b8d6;
            border-radius: 30px;
            padding: 0.2rem 1.2rem;
            color: #1f4d78;
            cursor: pointer;
            transition: all 0.2s;
        }
        
        .btn-modifier:hover {
            background: #ff4444;
            color: white;
            border-color: #ff4444;
        }
        
        .resume-cell {
            background: #f1f7fe;
            border-radius: 1.5rem;
            padding: 1.5rem;
            margin: 1.5rem 0;
        }
        
        .checkbox-vert {
            width: 1.5rem;
            height: 1.5rem;
            accent-color: #2e7d32;
        }
        
        .resultat-credit {
            font-size: 2.5rem;
            font-weight: 700;
            color: #0e4b77;
            background: linear-gradient(135deg, #e1f0fd, #d1e8fc);
            display: inline-block;
            padding: 0.5rem 2rem;
            border-radius: 60px;
            margin: 1rem 0;
            animation: pulse 2s infinite;
        }
        
        @keyframes pulse {
            0% { transform: scale(1); }
            50% { transform: scale(1.02); }
            100% { transform: scale(1); }
        }
        
        .hidden {
            display: none !important;
        }
        
        .etape {
            transition: all 0.3s;
            animation: fadeIn 0.3s ease-out;
        }
        
        @keyframes fadeIn {
            from {
                opacity: 0;
                transform: translateY(10px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }
        
        .sociaux {
            display: flex;
            gap: 1rem;
            flex-wrap: wrap;
            margin-top: 1.8rem;
        }
        
        .btn-social {
            background: #1e3a5f;
            color: white;
            border: none;
            border-radius: 40px;
            padding: 0.7rem 1.6rem;
            font-weight: 500;
            display: inline-flex;
            align-items: center;
            gap: 0.5rem;
            cursor: pointer;
            transition: all 0.2s;
        }
        
        .btn-social:hover {
            transform: translateY(-2px);
            filter: brightness(1.1);
        }
        
        .btn-save {
            background: linear-gradient(135deg, #0d4f30, #0a3e26);
            color: white;
            border: none;
            border-radius: 40px;
            padding: 0.7rem 2rem;
            font-weight: 600;
            cursor: pointer;
            font-size: 1rem;
            transition: all 0.2s;
        }
        
        .btn-save:hover {
            transform: translateY(-2px);
            box-shadow: 0 10px 20px -5px #0d4f30;
        }
        
        /* Loader */
        .loader-overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(255, 255, 255, 0.9);
            display: none;
            justify-content: center;
            align-items: center;
            z-index: 9999;
            backdrop-filter: blur(5px);
        }
        
        .loader {
            text-align: center;
        }
        
        .spinner {
            border: 4px solid #f3f3f3;
            border-top: 4px solid #1d5b8c;
            border-radius: 50%;
            width: 50px;
            height: 50px;
            animation: spin 1s linear infinite;
            margin: 0 auto 15px;
        }
        
        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }
        
        /* Notifications */
        .notification {
            position: fixed;
            top: 20px;
            right: 20px;
            padding: 15px 25px;
            border-radius: 8px;
            color: white;
            font-weight: bold;
            box-shadow: 0 4px 15px rgba(0,0,0,0.2);
            z-index: 10000;
            animation: slideInRight 0.3s ease-out;
        }
        
        @keyframes slideInRight {
            from {
                transform: translateX(100%);
                opacity: 0;
            }
            to {
                transform: translateX(0);
                opacity: 1;
            }
        }
        
        @keyframes slideOutRight {
            from {
                transform: translateX(0);
                opacity: 1;
            }
            to {
                transform: translateX(100%);
                opacity: 0;
            }
        }
        
        .notification.success {
            background: linear-gradient(135deg, #4CAF50, #45a049);
        }
        
        .notification.error {
            background: linear-gradient(135deg, #f44336, #da190b);
        }
        
        .notification.info {
            background: linear-gradient(135deg, #2196F3, #1e87db);
        }
        
        /* Statistiques */
        .stats-container {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
            gap: 1rem;
            margin: 1.5rem 0;
        }
        
        .stat-card {
            background: linear-gradient(135deg, #667eea, #764ba2);
            color: white;
            padding: 1rem;
            border-radius: 15px;
            text-align: center;
            animation: slideIn 0.3s ease-out;
        }
        
        .stat-card h4 {
            font-size: 0.9rem;
            opacity: 0.9;
            margin-bottom: 0.5rem;
        }
        
        .stat-card .stat-value {
            font-size: 1.8rem;
            font-weight: bold;
        }
        
        /* Tableau récapitulatif */
        .resultats-table {
            width: 100%;
            border-collapse: collapse;
            margin: 1rem 0;
        }
        
        .resultats-table th,
        .resultats-table td {
            padding: 0.75rem;
            text-align: left;
            border-bottom: 1px solid #dde7f2;
        }
        
        .resultats-table th {
            background: #f1f7fe;
            font-weight: 600;
            color: #1e3a5f;
        }
        
        .resultats-table tr:hover {
            background: #f8fcff;
        }
        
        .resultats-table .reussi {
            color: #2e7d32;
            font-weight: bold;
        }
        
        .resultats-table .non-reussi {
            color: #c62828;
            font-weight: bold;
        }
        
        /* Tooltips */
        .tooltip {
            position: relative;
            display: inline-block;
        }
        
        .tooltip .tooltiptext {
            visibility: hidden;
            width: 200px;
            background-color: #333;
            color: #fff;
            text-align: center;
            border-radius: 6px;
            padding: 5px;
            position: absolute;
            z-index: 1;
            bottom: 125%;
            left: 50%;
            margin-left: -100px;
            opacity: 0;
            transition: opacity 0.3s;
        }
        
        .tooltip:hover .tooltiptext {
            visibility: visible;
            opacity: 1;
        }
    </style>
</head>
<body>
    <!-- Loader -->
    <div class="loader-overlay" id="loader">
        <div class="loader">
            <div class="spinner"></div>
            <p style="color: #1d5b8c; font-weight: 500;">Traitement en cours...</p>
        </div>
    </div>

    <div class="app-container">
        <div class="header-univ">
            <h1>📚 Gestion de notes universitaire</h1>
            <p>Sécurisé · Calcul automatique des crédits · Envoi par email</p>
            <div style="position: absolute; top: 10px; right: 20px; font-size: 12px; opacity: 0.7;">
                <span class="tooltip">🔒 HTTPS
                    <span class="tooltiptext">Connexion sécurisée</span>
                </span>
            </div>
        </div>

        <div class="content">
            <!-- Indicateur d'étape -->
            <div class="step-indicator" id="stepIndicator"></div>

            <!-- ÉTAPE 0 : ACCUEIL -->
            <div id="etape0" class="etape">
                <div style="text-align: center; padding: 2rem 1rem;">
                    <span style="font-size: 5rem; display: block; margin-bottom: 1rem;">🎓</span>
                    <h2 style="font-size: 2rem; margin: 1rem 0; color: #102b47;">Bienvenue sur votre espace de gestion</h2>
                    <p style="color: #345c7e; margin-bottom: 2.5rem; font-size: 1.2rem;">
                        Calculez vos crédits universitaires en toute sécurité
                    </p>
                    <button class="btn-primary" id="btnCommencer">
                        📋 QUELLE SONT MES CRÉDITS POUR CE SEMESTRE ?
                    </button>
                </div>
            </div>

            <!-- ÉTAPE 1 : Formulaire d'inscription -->
            <div id="etape1" class="etape hidden">
                <h2 style="margin-bottom: 1.5rem; display: flex; align-items: center; gap: 10px;">
                    <span style="background: #1d5b8c; color: white; width: 30px; height: 30px; display: flex; align-items: center; justify-content: center; border-radius: 50%;">1</span>
                    Ajouter une matière
                </h2>
                
                <div class="input-group">
                    <label>📖 Nom de la matière</label>
                    <input type="text" id="matiereNom" placeholder="Ex: Mathématiques, Physique, ..." />
                </div>
                
                <div class="row-flex">
                    <div class="input-group">
                        <label>📊 Note (0-20)</label>
                        <input type="number" step="0.01" min="0" max="20" id="matiereNote" placeholder="Ex: 14.5" />
                    </div>
                    <div class="input-group">
                        <label>🎯 Crédits ECTS</label>
                        <input type="number" min="1" max="30" id="matiereCredit" value="3" />
                    </div>
                    <div class="input-group">
                        <label>🔄 Type de crédit</label>
                        <select id="typeCredit">
                            <option value="simple">Simple</option>
                            <option value="regroupe">Regroupé (2 matières)</option>
                        </select>
                    </div>
                </div>

                <!-- Champs conditionnels pour regroupé -->
                <div id="groupeRegroupe" class="hidden" style="background: #f4f9ff; border-radius: 30px; padding: 1.5rem; margin: 1rem 0; border: 2px dashed #1d5b8c;">
                    <h4 style="margin-bottom: 1rem; color: #1d5b8c;">🔄 Matière associée (moyenne requise ≥10)</h4>
                    <div class="row-flex">
                        <div class="input-group">
                            <label>Matière associée</label>
                            <input type="text" id="matiereAssocNom" placeholder="Ex: Physique" />
                        </div>
                        <div class="input-group">
                            <label>Note associée</label>
                            <input type="number" step="0.01" min="0" max="20" id="matiereAssocNote" />
                        </div>
                    </div>
                </div>

                <div style="display: flex; gap: 1rem; flex-wrap: wrap; margin-top: 1.5rem;">
                    <button class="btn-primary" id="btnAjouterMatiere">
                        ➕ Ajouter à la liste
                    </button>
                    <button class="btn-secondary" id="btnPasserEtape1" disabled>
                        ⏭️ Passer à la liste
                    </button>
                </div>
                
                <div style="margin-top: 1rem; padding: 1rem; background: #f8fcff; border-radius: 15px;">
                    <p id="msgListe" style="color: #566b81;">
                        <span id="compteurMatieres">0</span> matière(s) ajoutée(s)
                    </p>
                </div>
            </div>

            <!-- ÉTAPE 2 : Liste des matières -->
            <div id="etape2" class="etape hidden">
                <h2 style="margin-bottom: 1.5rem; display: flex; align-items: center; gap: 10px;">
                    <span style="background: #1d5b8c; color: white; width: 30px; height: 30px; display: flex; align-items: center; justify-content: center; border-radius: 50%;">2</span>
                    Liste des matières enregistrées
                </h2>
                
                <div class="card-liste" id="listeMatieresContainer">
                    <!-- Injecté dynamiquement -->
                </div>
                
                <div style="display: flex; gap: 1rem; flex-wrap: wrap;">

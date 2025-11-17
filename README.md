<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>RELATÓRIO DE AUDITORIA PARA RESTAURANTES</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        nutri: {
                            100: '#e6f6e6',
                            200: '#c3e8c3',
                            300: '#91d191',
                            400: '#5bb85b',
                            500: '#3a9e3a',
                            600: '#2b8a2b',
                            700: '#1f6e1f',
                            800: '#145214',
                        }
                    }
                }
            }
        }
    </script>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700&display=swap');
        
        body {
            font-family: 'Poppins', sans-serif;
            background-color: #f8fafc;
        }
        
        .header-gradient {
            background: linear-gradient(135deg, #2b8a2b 0%, #145214 100%);
        }
        
        .section-header {
            background-color: #e6f6e6;
            border-left: 4px solid #2b8a2b;
        }
        
        .checklist-item-row {
            display: grid;
            grid-template-columns: 1fr 50px 50px 50px 70px; /* Item, C, NC, NA, Tipo */
            gap: 8px;
            align-items: center;
            padding: 10px 0;
            border-bottom: 1px dashed #e2e8f0;
        }
        
        .checklist-item-row:last-child {
            border-bottom: none;
        }
        
        .checklist-item-row label {
            margin-bottom: 0;
            font-size: 0.9rem;
            line-height: 1.4;
        }
        
        .checklist-item-row input[type="radio"] {
            margin: 0 auto;
            width: 18px;
            height: 18px;
        }
        
        .signature-line {
            border-bottom: 1px dashed #64748b;
            width: 70%;
            margin: 0 auto;
        }
        
        .print-button {
            transition: all 0.3s ease;
        }
        
        .print-button:hover {
            transform: translateY(-2px);
            box-shadow: 0 4px 6px -1px rgba(0,0,0,0.1), 0 2px 4px -1px rgba(0,0,0,0.06);
        }
        
        .critical-item-highlight {
            background-color: #fff5f5; /* Light red background */
            border-left: 4px solid #ef4444; /* Red border */
            padding-left: 10px; /* Add some padding for the border */
        }

        @media print {
            .print-button, .mx-auto.text-center.mt-8 {
                display: none;
            }
            .max-w-5xl {
                max-width: 100%;
                margin: 0;
                box-shadow: none;
                border-radius: 0;
            }
            body {
                background-color: white;
            }
            /* Garantir que o conteúdo editável não mostre a linha pontilhada na impressão */
            [contenteditable="true"] {
                border-bottom: none !important;
            }
            /* Exibir o campo de data de visita completo */
            #print-date-display {
                display: inline;
                margin-left: 5px;
            }
            #visit-date-input {
                display: none;
            }
        }
    </style>
</head>
<body class="text-gray-800">
    <div class="max-w-5xl mx-auto my-8 bg-white rounded-lg shadow-lg overflow-hidden">
        <div class="header-gradient text-white p-8">
            <div class="flex justify-between items-center">
                <div>
                    <h1 class="text-3xl font-bold">RELATÓRIO DE AUDITORIA PARA RESTAURANTES</h1>
                    <p class="text-green-200 mt-2">Verificar o cumprimento das normas de boas práticas de manipulação (RDC n° 216/2004)</p>
                </div>
                <div class="bg-white p-2 rounded-lg" style="width: 64px; height: 64px; display: flex; align-items: center; justify-content: center; color: #145214; font-weight: bold;">
                    <i class="fas fa-utensils text-4xl"></i>
                </div>
            </div>
        </div>
        
        <div class="p-8 border-b border-nutri-200">
            <div class="grid grid-cols-1 md:grid-cols-2 gap-4 text-sm">
                <div>
                    <p><span class="font-medium text-nutri-800">Restaurante:</span> 
                    <span class="border-b border-dashed border-nutri-400 px-2" contenteditable="true">_____________________________</span></p>
                </div>
                <div>
                    <p><span class="font-medium text-nutri-800">Unidade:</span> 
                    <span class="border-b border-dashed border-nutri-400 px-2" contenteditable="true">_____________________________</span></p>
                </div>
                <div>
                    <p><span class="font-medium text-nutri-800">Revisão n°:</span> 
                    <span class="border-b border-dashed border-nutri-400 px-2" contenteditable="true">0</span></p>
                </div>
                <div>
                    <p><span class="font-medium text-nutri-800">Data da Revisão:</span> 
                    <span class="border-b border-dashed border-nutri-400 px-2" contenteditable="true">___/____/___</span></p>
                </div>
                <div>
                    <p><span class="font-medium text-nutri-800">Data da visita:</span> 
                    <span class="border-b border-dashed border-nutri-400 px-2" contenteditable="true">___/____/___</span></p>
                </div>
                <div>
                    <p><span class="font-medium text-nutri-800">Nutricionista Responsável:</span> 
                    <span class="border-b border-dashed border-nutri-400 px-2" contenteditable="true"></span></p>
                </div>
                <div>
                    <p><span class="font-medium text-nutri-800">Responsável pela Unidade:</span> 
                    <span class="border-b border-dashed border-nutri-400 px-2" contenteditable="true"></span></p>
                </div>
            </div>
        </div>

        <div class="p-8 border-b border-nutri-200">
            <h2 class="text-xl font-semibold text-nutri-700 mb-6 flex items-center">
                <i class="fas fa-tasks mr-2"></i> AVALIAÇÃO
            </h2>
            
            <div class="checklist-item-row font-semibold text-nutri-800 border-b-2 border-nutri-400 bg-nutri-100">
                <div class="font-medium">ITEM</div>
                <div class="text-center">C</div>
                <div class="text-center">NC</div>
                <div class="text-center">NA</div>
                <div class="text-center">TIPO</div>
            </div>

            <div class="section-header px-4 py-3 mt-6 rounded-t-lg">
                <h3 class="font-semibold text-nutri-800">1. EDIFICAÇÃO E INSTALAÇÃO</h3>
            </div>
            
            <div class="px-4 py-2 bg-nutri-50">
                <h4 class="font-medium text-nutri-700">1.1 ÁREA EXTERNA</h4>
            </div>
            <div class="checklist-item-row" data-item-id="1.1.1">
                <label>1.1.1 Área externa livre de focos de insalubridade, materiais em desuso ou estranhos ao ambiente, ausência de lixo, água estagnada.</label>
                <input type="radio" name="item_1_1_1" value="C">
                <input type="radio" name="item_1_1_1" value="NC">
                <input type="radio" name="item_1_1_1" value="NA">
                <div class="text-center font-medium text-nutri-700">I</div>
            </div>
            <div class="checklist-item-row" data-item-id="1.1.2">
                <label>1.1.2 Ausência de vetores/pragas ou vestígios da presença nas imediações.</label>
                <input type="radio" name="item_1_1_2" value="C">
                <input type="radio" name="item_1_1_2" value="NC">
                <input type="radio" name="item_1_1_2" value="NA">
                <div class="text-center font-medium text-nutri-700">I</div>
            </div>

            <div class="px-4 py-2 bg-nutri-50 mt-4">
                <h4 class="font-medium text-nutri-700">1.2 ACESSO</h4>
            </div>
            <div class="checklist-item-row" data-item-id="1.2.1">
                <label>1.2.1 Direto, não comum a outros usos (habitação).</label>
                <input type="radio" name="item_1_2_1" value="C">
                <input type="radio" name="item_1_2_1" value="NC">
                <input type="radio" name="item_1_2_1" value="NA">
                <div class="text-center font-medium text-nutri-700">N</div>
            </div>

            <div class="px-4 py-2 bg-nutri-50 mt-4">
                <h4 class="font-medium text-nutri-700">1.3 ÁREA INTERNA</h4>
            </div>
            <div class="checklist-item-row" data-item-id="1.3.1">
                <label>1.3.1 Área interna livre de objetos em desuso ou estranhos ao ambiente.</label>
                <input type="radio" name="item_1_3_1" value="C">
                <input type="radio" name="item_1_3_1" value="NC">
                <input type="radio" name="item_1_3_1" value="NA">
                <div class="text-center font-medium text-nutri-700">N</div>
            </div>

            <div class="px-4 py-2 bg-nutri-50 mt-4">
                <h4 class="font-medium text-nutri-700">1.4 PISO</h4>
            </div>
            <div class="checklist-item-row" data-item-id="1.4.1">
                <label>1.4.1 Material que permite fácil e apropriada higienização (liso, resistente, drenados com declive, impermeável).</label>
                <input type="radio" name="item_1_4_1" value="C">
                <input type="radio" name="item_1_4_1" value="NC">
                <input type="radio" name="item_1_4_1" value="NA">
                <div class="text-center font-medium text-nutri-700">N</div>
            </div>
            <div class="checklist-item-row" data-item-id="1.4.2">
                <label>1.4.2 Em adequado estado de conservação (livre de defeitos, rachaduras, buracos e outros).</label>
                <input type="radio" name="item_1_4_2" value="C">
                <input type="radio" name="item_1_4_2" value="NC">
                <input type="radio" name="item_1_4_2" value="NA">
                <div class="text-center font-medium text-nutri-700">N</div>
            </div>
            <div class="checklist-item-row" data-item-id="1.4.3">
                <label>1.4.3 Sistema de drenagem dimensionados adequadamente, sem acúmulo de água e/ou resíduos.</label>
                <input type="radio" name="item_1_4_3" value="C">
                <input type="radio" name="item_1_4_3" value="NC">
                <input type="radio" name="item_1_4_3" value="NA">
                <div class="text-center font-medium text-nutri-700">N</div>
            </div>
            <div class="checklist-item-row" data-item-id="1.4.5">
                <label>1.4.5 Drenos, ralos sifonados e grelhas colocadas em locais adequados de forma a facilitar o escoamento e proteger contra a entrada de insetos, roedores.</label>
                <input type="radio" name="item_1_4_5" value="C">
                <input type="radio" name="item_1_4_5" value="NC">
                <input type="radio" name="item_1_4_5" value="NA">
                <div class="text-center font-medium text-nutri-700">N</div>
            </div>

            <div class="px-4 py-2 bg-nutri-50 mt-4">
                <h4 class="font-medium text-nutri-700">1.5 TETOS</h4>
            </div>
            <div class="checklist-item-row" data-item-id="1.5.1">
                <label>1.5.1 Acabamento liso, em cor clara, impermeável, de fácil limpeza e, quando for o caso, desinfecção.</label>
                <input type="radio" name="item_1_5_1" value="C">
                <input type="radio" name="item_1_5_1" value="NC">
                <input type="radio" name="item_1_5_1" value="NA">
                <div class="text-center font-medium text-nutri-700">N</div>
            </div>
            <div class="checklist-item-row" data-item-id="1.5.2">
                <label>1.5.2 Em adequado estado de conservação (livre de rachaduras, umidade, bolor, descascamento e outros).</label>
                <input type="radio" name="item_1_5_2" value="C">
                <input type="radio" name="item_1_5_2" value="NC">
                <input type="radio" name="item_1_5_2" value="NA">
                <div class="text-center font-medium text-nutri-700">N</div>
            </div>

            <div class="px-4 py-2 bg-nutri-50 mt-4">
                <h4 class="font-medium text-nutri-700">1.6 PAREDES E DIVISÓRIAS</h4>
            </div>
            <div class="checklist-item-row" data-item-id="1.6.1">
                <label>1.6.1 Acabamento de cor clara, liso, impermeável e de fácil higienização até uma altura adequada para todas as operações.</label>
                <input type="radio" name="item_1_6_1" value="C">
                <input type="radio" name="item_1_6_1" value="NC">
                <input type="radio" name="item_1_6_1" value="NA">
                <div class="text-center font-medium text-nutri-700">N</div>
            </div>
            <div class="checklist-item-row" data-item-id="1.6.2">
                <label>1.6.2 Em adequado estado de conservação (livre de falhas, rachaduras, umidade, descascamento, bolores e outros).</label>
                <input type="radio" name="item_1_6_2" value="C">
                <input type="radio" name="item_1_6_2" value="NC">
                <input type="radio" name="item_1_6_2" value="NA">
                <div class="text-center font-medium text-nutri-700">N</div>
            </div>

            <div class="px-4 py-2 bg-nutri-50 mt-4">
                <h4 class="font-medium text-nutri-700">1.7 PORTAS</h4>
            </div>
            <div class="checklist-item-row" data-item-id="1.7.1">
                <label>1.7.1 Com superfície lisa, de fácil higienização, ajustadas aos batentes, sem falhas de revestimento.</label>
                <input type="radio" name="item_1_7_1" value="C">
                <input type="radio" name="item_1_7_1" value="NC">
                <input type="radio" name="item_1_7_1" value="NA">
                <div class="text-center font-medium text-nutri-700">N</div>
            </div>
            <div class="checklist-item-row" data-item-id="1.7.2">
                <label>1.7.2 Portas externas com fechamento automático (mola, sistema eletrônico ou outro) e com barreiras adequadas para impedir entrada de vetores e outros animais como telas milimétricas ou outro sistema).</label>
                <input type="radio" name="item_1_7_2" value="C">
                <input type="radio" name="item_1_7_2" value="NC">
                <input type="radio" name="item_1_7_2" value="NA">
                <div class="text-center font-medium text-nutri-700">I</div>
            </div>
            <div class="checklist-item-row" data-item-id="1.7.3">
                <label>1.7.3 Em adequado estado de conservação (livre de falhas, rachaduras, umidade, descascamento e outros).</label>
                <input type="radio" name="item_1_7_3" value="C">
                <input type="radio" name="item_1_7_3" value="NC">
                <input type="radio" name="item_1_7_3" value="NA">
                <div class="text-center font-medium text-nutri-700">N</div>
            </div>

            <div class="px-4 py-2 bg-nutri-50 mt-4">
                <h4 class="font-medium text-nutri-700">1.8 JANELAS E OUTRAS ABERTURAS</h4>
            </div>
            <div class="checklist-item-row" data-item-id="1.8.1">
                <label>1.8.1 Com superfície lisa, de fácil higienização, ajustadas aos batentes, sem falhas de revestimento.</label>
                <input type="radio" name="item_1_8_1" value="C">
                <input type="radio" name="item_1_8_1" value="NC">
                <input type="radio" name="item_1_8_1" value="NA">
                <div class="text-center font-medium text-nutri-700">N</div>
            </div>
            <div class="checklist-item-row" data-item-id="1.8.2">
                <label>1.8.2 Existência de proteção contra insetos e roedores (telas milimétricas ou outro sistema).</label>
                <input type="radio" name="item_1_8_2" value="C">
                <input type="radio" name="item_1_8_2" value="NC">
                <input type="radio" name="item_1_8_2" value="NA">
                <div class="text-center font-medium text-nutri-700">I</div>
            </div>
            <div class="checklist-item-row" data-item-id="1.8.3">
                <label>1.8.3 Telas milimétricas removíveis para facilitar a higienização.</label>
                <input type="radio" name="item_1_8_3" value="C">
                <input type="radio" name="item_1_8_3" value="NC">
                <input type="radio" name="item_1_8_3" value="NA">
                <div class="text-center font-medium text-nutri-700">R</div>
            </div>
            <div class="checklist-item-row" data-item-id="1.8.4">
                <label>1.8.4 Em adequado estado de conservação (livre de falhas, rachaduras, umidade, descascamento e outros).</label>
                <input type="radio" name="item_1_8_4" value="C">
                <input type="radio" name="item_1_8_4" value="NC">
                <input type="radio" name="item_1_8_4" value="NA">
                <div class="text-center font-medium text-nutri-700">N</div>
            </div>

            <div class="px-4 py-2 bg-nutri-50 mt-4">
                <h4 class="font-medium text-nutri-700">1.9 INSTALAÇÕES SANITÁRIAS E VESTIÁRIOS PARA OS MANIPULADORES</h4>
            </div>
            <div class="checklist-item-row" data-item-id="1.9.1">
                <label>1.9.1 Quando localizados isolados da área de produção, acesso realizado por passagens cobertas e calçadas.</label>
                <input type="radio" name="item_1_9_1" value="C">
                <input type="radio" name="item_1_9_1" value="NC">
                <input type="radio" name="item_1_9_1" value="NA">
                <div class="text-center font-medium text-nutri-700">N</div>
            </div>
            <div class="checklist-item-row" data-item-id="1.9.2">
                <label>1.9.2 Independentes para cada sexo.</label>
                <input type="radio" name="item_1_9_2" value="C">
                <input type="radio" name="item_1_9_2" value="NC">
                <input type="radio" name="item_1_9_2" value="NA">
                <div class="text-center font-medium text-nutri-700">N</div>
            </div>
            <div class="checklist-item-row" data-item-id="1.9.3">
                <label>1.9.3 Instalações sanitárias com vasos sanitários; mictórios e lavatórios íntegros e em proporção adequada ao número de empregados (conforme legislação específica).</label>
                <input type="radio" name="item_1_9_3" value="C">
                <input type="radio" name="item_1_9_3" value="NC">
                <input type="radio" name="item_1_9_3" value="NA">
                <div class="text-center font-medium text-nutri-700">N</div>
            </div>
            <div class="checklist-item-row" data-item-id="1.9.4">
                <label>1.9.4 Instalações sanitárias servidas de água corrente, dotadas de torneira com acionamento automático e conectadas à rede de esgoto ou fossa séptica.</label>
                <input type="radio" name="item_1_9_4" value="C">
                <input type="radio" name="item_1_9_4" value="NC">
                <input type="radio" name="item_1_9_4" value="NA">
                <div class="text-center font-medium text-nutri-700">N</div>
            </div>
            <div class="checklist-item-row" data-item-id="1.9.5">
                <label>1.9.5 Ausência de comunicação direta com a área de trabalho e refeições.</label>
                <input type="radio" name="item_1_9_5" value="C">
                <input type="radio" name="item_1_9_5" value="NC">
                <input type="radio" name="item_1_9_5" value="NA">
                <div class="text-center font-medium text-nutri-700">I</div>
            </div>
            <div class="checklist-item-row" data-item-id="1.9.6">
                <label>1.9.6 Portas com fechamento automático.</label>
                <input type="radio" name="item_1_9_6" value="C">
                <input type="radio" name="item_1_9_6" value="NC">
                <input type="radio" name="item_1_9_6" value="NA">
                <div class="text-center font-medium text-nutri-700">N</div>
            </div>
            <div class="checklist-item-row" data-item-id="1.9.7">
                <label>1.9.7 Pisos e paredes adequadas e apresentando satisfatório estado de conservação.</label>
                <input type="radio" name="item_1_9_7" value="C">
                <input type="radio" name="item_1_9_7" value="NC">
                <input type="radio" name="item_1_9_7" value="NA">
                <div class="text-center font-medium text-nutri-700">N</div>
            </div>
            <div class="checklist-item-row" data-item-id="1.9.8">
                <label>1.9.8 Iluminação e ventilação adequadas.</label>
                <input type="radio" name="item_1_9_8" value="C">
                <input type="radio" name="item_1_9_8" value="NC">
                <input type="radio" name="item_1_9_8" value="NA">
                <div class="text-center font-medium text-nutri-700">N</div>
            </div>
            <div class="checklist-item-row" data-item-id="1.9.9">
                <label>1.9.9 Instalações sanitárias dotadas de produtos destinados à higiene pessoal; papel higiênico, sabonete líquido inodoro e anti-séptico, toalhas de papel não reciclado para mãos ou outros sistema higiênico e seguro para secagem.</label>
                <input type="radio" name="item_1_9_9" value="C">
                <input type="radio" name="item_1_9_9" value="NC">
                <input type="radio" name="item_1_9_9" value="NA">
                <div class="text-center font-medium text-nutri-700">I</div>
            </div>
            <div class="checklist-item-row" data-item-id="1.9.10">
                <label>1.9.10 Presença de lixeiras com tampas e com acionamento não manual.</label>
                <input type="radio" name="item_1_9_10" value="C">
                <input type="radio" name="item_1_9_10" value="NC">
                <input type="radio" name="item_1_9_10" value="NA">
                <div class="text-center font-medium text-nutri-700">N</div>
            </div>
            <div class="checklist-item-row" data-item-id="1.9.11">
                <label>1.9.11 Coleta frequente do lixo.</label>
                <input type="radio" name="item_1_9_11" value="C">
                <input type="radio" name="item_1_9_11" value="NC">
                <input type="radio" name="item_1_9_11" value="NA">
                <div class="text-center font-medium text-nutri-700">N</div>
            </div>
            <div class="checklist-item-row" data-item-id="1.9.12">
                <label>1.9.12 Presença de avisos com procedimentos para lavagem de mãos.</label>
                <input type="radio" name="item_1_9_12" value="C">
                <input type="radio" name="item_1_9_12" value="NC">
                <input type="radio" name="item_1_9_12" value="NA">
                <div class="text-center font-medium text-nutri-700">N</div>
            </div>
            <div class="checklist-item-row" data-item-id="1.9.13">
                <label>1.9.13 Vestiários com área compatível e armários para todos os manipuladores.</label>
                <input type="radio" name="item_1_9_13" value="C">
                <input type="radio" name="item_1_9_13" value="NC">
                <input type="radio" name="item_1_9_13" value="NA">
                <div class="text-center font-medium text-nutri-700">N</div>
            </div>
            <div class="checklist-item-row" data-item-id="1.9.14">
                <label>1.9.14 Apresentam-se organizados e em adequado estado de conservação.</label>
                <input type="radio" name="item_1_9_14" value="C">
                <input type="radio" name="item_1_9_14" value="NC">
                <input type="radio" name="item_1_9_14" value="NA">
                <div class="text-center font-medium text-nutri-700">N</div>
            </div>

            <div class="px-4 py-2 bg-nutri-50 mt-4">
                <h4 class="font-medium text-nutri-700">1.10 INSTALAÇÕES SANITÁRIAS PARA O PÚBLICO</h4>
            </div>
            <div class="checklist-item-row" data-item-id="1.10.1">
                <label>1.10.1 Apresentam piso, paredes e teto de material liso, resistente e impermeável, ventilação adequada, em bom estado de conservação e higiene.</label>
                <input type="radio" name="item_1_10_1" value="C">
                <input type="radio" name="item_1_10_1" value="NC">
                <input type="radio" name="item_1_10_1" value="NA">
                <div class="text-center font-medium text-nutri-700">N</div>
            </div>
            <div class="checklist-item-row" data-item-id="1.10.2">
                <label>1.10.2 Possuem produtos para higiene pessoal (sabonete, papel higiênico, papel toalha) e lixeiras com acionamento não manual.</label>
                <input type="radio" name="item_1_10_2" value="C">
                <input type="radio" name="item_1_10_2" value="NC">
                <input type="radio" name="item_1_10_2" value="NA">
                <div class="text-center font-medium text-nutri-700">N</div>
            </div>

            <div class="section-header px-4 py-3 mt-6 rounded-t-lg">
                <h3 class="font-semibold text-nutri-800">1.11 HIGIENIZAÇÃO DAS INSTALAÇÕES</h3>
            </div>
            <div class="checklist-item-row" data-item-id="1.11.1">
                <label>1.11.1 Existência de uma equipe responsável pela operação de higienização.</label>
                <input type="radio" name="item_1_11_1" value="C">
                <input type="radio" name="item_1_11_1" value="NC">
                <input type="radio" name="item_1_11_1" value="NA">
                <div class="text-center font-medium text-nutri-700">N</div>
            </div>
            <div class="checklist-item-row" data-item-id="1.11.2">
                <label>1.11.2 A equipe é comprovadamente capacitada com treinamentos (Boas Práticas, Produtos Químicos, Uso correto de EPIs, etc).</label>
                <input type="radio" name="item_1_11_2" value="C">
                <input type="radio" name="item_1_11_2" value="NC">
                <input type="radio" name="item_1_11_2" value="NA">
                <div class="text-center font-medium text-nutri-700">N</div>
            </div>
            <div class="checklist-item-row" data-item-id="1.11.10">
                <label>1.11.10 Utensílios utilizados na higienização de instalações são distintos daqueles usados na higienização das partes dos equipamentos e utensílios que entrem em contato com o alimento.</label>
                <input type="radio" name="item_1_11_10" value="C">
                <input type="radio" name="item_1_11_10" value="NC">
                <input type="radio" name="item_1_11_10" value="NA">
                <div class="text-center font-medium text-nutri-700">I</div>
            </div>

            <div class="section-header px-4 py-3 mt-6 rounded-t-lg">
                <h3 class="font-semibold text-nutri-800">1.12 MANEJO DE RESÍDUOS</h3>
            </div>
             <div class="checklist-item-row" data-item-id="1.12.5">
                <label>1.12.5 Recipientes e sacos de lixo mantidos íntegros, fechados e distantes do local de preparação e consumo, com acesso restrito a pessoas estranhas, animais domésticos, insetos e roedores.</label>
                <input type="radio" name="item_1_12_5" value="C">
                <input type="radio" name="item_1_12_5" value="NC">
                <input type="radio" name="item_1_12_5" value="NA">
                <div class="text-center font-medium text-nutri-700">N</div>
            </div>
            <div class="checklist-item-row" data-item-id="1.12.6">
                <label>1.12.6 Área de depósito ou recipiente na área externa devidamente higienizado.</label>
                <input type="radio" name="item_1_12_6" value="C">
                <input type="radio" name="item_1_12_6" value="NC">
                <input type="radio" name="item_1_12_6" value="NA">
                <div class="text-center font-medium text-nutri-700">N</div>
            </div>
            <div class="checklist-item-row" data-item-id="1.12.7">
                <label>1.12.7 Existência de POP para manejo de resíduos.</label>
                <input type="radio" name="item_1_12_7" value="C">
                <input type="radio" name="item_1_12_7" value="NC">
                <input type="radio" name="item_1_12_7" value="NA">
                <div class="text-center font-medium text-nutri-700">N</div>
            </div>


            <div class="section-header px-4 py-3 mt-6 rounded-t-lg">
                <h3 class="font-semibold text-nutri-800">2. EQUIPAMENTOS, MÓVEIS E UTENSÍLIOS</h3>
            </div>
            <div class="px-4 py-2 bg-nutri-50">
                <h4 class="font-medium text-nutri-700">2.1 CONSERVAÇÃO</h4>
            </div>
            <div class="checklist-item-row" data-item-id="2.1.3">
                <label>2.1.3 Equipamentos e utensílios construídos de material que não transmita substâncias tóxicas, odores nem sabores, e que sejam resistentes à corrosão e a repetidas operações de limpeza e desinfecção.</label>
                <input type="radio" name="item_2_1_3" value="C">
                <input type="radio" name="item_2_1_3" value="NC">
                <input type="radio" name="item_2_1_3" value="NA">
                <div class="text-center font-medium text-nutri-700">I</div>
            </div>
            <div class="checklist-item-row" data-item-id="2.1.4">
                <label>2.1.4 Em adequado estado de conservação e funcionamento.</label>
                <input type="radio" name="item_2_1_4" value="C">
                <input type="radio" name="item_2_1_4" value="NC">
                <input type="radio" name="item_2_1_4" value="NA">
                <div class="text-center font-medium text-nutri-700">N</div>
            </div>
            <div class="checklist-item-row" data-item-id="2.1.5">
                <label>2.1.5 Equipamentos de conservação dos alimentos (refrigeradores, congeladores) dotados de termômetros para monitoramento.</label>
                <input type="radio" name="item_2_1_5" value="C">
                <input type="radio" name="item_2_1_5" value="NC">
                <input type="radio" name="item_2_1_5" value="NA">
                <div class="text-center font-medium text-nutri-700">I</div>
            </div>

            <div class="px-4 py-2 bg-nutri-50 mt-4">
                <h4 class="font-medium text-nutri-700">2.4 HIGIENIZAÇÃO DE EQUIPAMENTOS, MÓVEIS E UTENSÍLIOS</h4>
            </div>
            <div class="checklist-item-row" data-item-id="2.4.6">
                <label>2.4.6 Utensílios de limpeza para as diversas áreas de manipulação são identificados e exclusivos para as áreas.</label>
                <input type="radio" name="item_2_4_6" value="C">
                <input type="radio" name="item_2_4_6" value="NC">
                <input type="radio" name="item_2_4_6" value="NA">
                <div class="text-center font-medium text-nutri-700">N</div>
            </div>
            <div class="checklist-item-row" data-item-id="2.4.7">
                <label>2.4.7 Responsáveis pela higienização utilizam uniforme adequado e EPIs quando necessário.</label>
                <input type="radio" name="item_2_4_7" value="C">
                <input type="radio" name="item_2_4_7" value="NC">
                <input type="radio" name="item_2_4_7" value="NA">
                <div class="text-center font-medium text-nutri-700">N</div>
            </div>

            <div class="section-header px-4 py-3 mt-6 rounded-t-lg">
                <h3 class="font-semibold text-nutri-800">3. MANIPULADORES</h3>
            </div>
            <div class="px-4 py-2 bg-nutri-50">
                <h4 class="font-medium text-nutri-700">3.1 VESTUÁRIO</h4>
            </div>
            <div class="checklist-item-row" data-item-id="3.1.1">
                <label>3.1.1 Utilização de uniforme de trabalho de cor clara adequada à atividade e exclusivo para área de produção.</label>
                <input type="radio" name="item_3_1_1" value="C">
                <input type="radio" name="item_3_1_1" value="NC">
                <input type="radio" name="item_3_1_1" value="NA">
                <div class="text-center font-medium text-nutri-700">I</div>
            </div>

            <div class="px-4 py-2 bg-nutri-50 mt-4">
                <h4 class="font-medium text-nutri-700">3.2 HIGIENE</h4>
            </div>
            <div class="checklist-item-row" data-item-id="3.2.1">
                <label>3.2.1 Manipuladores apresentam-se asseados, com cabelos protegidos com redes ou toucas, unhas curtas, sem esmalte, sem adornos (anéis, pulseiras, brincos, colares, relógios).</label>
                <input type="radio" name="item_3_2_1" value="C">
                <input type="radio" name="item_3_2_1" value="NC">
                <input type="radio" name="item_3_2_1" value="NA">
                <div class="text-center font-medium text-nutri-700">I</div>
            </div>
            <div class="checklist-item-row" data-item-id="3.2.2">
                <label>3.2.2 Manipuladores não espirram sobre os alimentos, não cospem, não tossem, não fumam, não manipulam dinheiro ou não praticam outros atos que possam contaminar o alimento.</label>
                <input type="radio" name="item_3_2_2" value="C">
                <input type="radio" name="item_3_2_2" value="NC">
                <input type="radio" name="item_3_2_2" value="NA">
                <div class="text-center font-medium text-nutri-700">I</div>
            </div>
            <div class="checklist-item-row" data-item-id="3.2.3">
                <label>3.2.3 Cartazes de orientação aos manipuladores sobre a correta lavagem das mãos e demais hábitos de higiene afixados em locais apropriados.</label>
                <input type="radio" name="item_3_2_3" value="C">
                <input type="radio" name="item_3_2_3" value="NC">
                <input type="radio" name="item_3_2_3" value="NA">
                <div class="text-center font-medium text-nutri-700">N</div>
            </div>

            <div class="px-4 py-2 bg-nutri-50 mt-4">
                <h4 class="font-medium text-nutri-700">3.6 SAÚDE DO MANIPULADOR</h4>
            </div>
            <div class="checklist-item-row" data-item-id="3.6.4">
                <label>3.6.4 O programa de controle de saúde é documentado e registra o resultado dos exames e as condutas adotadas.</label>
                <input type="radio" name="item_3_6_4" value="C">
                <input type="radio" name="item_3_6_4" value="NC">
                <input type="radio" name="item_3_6_4" value="NA">
                <div class="text-center font-medium text-nutri-700">N</div>
            </div>
            
            <div class="section-header px-4 py-3 mt-6 rounded-t-lg">
                <h3 class="font-semibold text-nutri-800">4. RECEPÇÃO MATÉRIAS-PRIMAS, INGREDIENTES E EMBALAGENS</h3>
            </div>
            <div class="checklist-item-row" data-item-id="4.2">
                <label>4.2 O restaurante possui um POP para recebimento de matéria prima, ingredientes e embalagens.</label>
                <input type="radio" name="item_4_2" value="C">
                <input type="radio" name="item_4_2" value="NC">
                <input type="radio" name="item_4_2" value="NA">
                <div class="text-center font-medium text-nutri-700">N</div>
            </div>
            <div class="checklist-item-row" data-item-id="4.3">
                <label>4.3 O responsável pelo recebimento está devidamente capacitado.</label>
                <input type="radio" name="item_4_3" value="C">
                <input type="radio" name="item_4_3" value="NC">
                <input type="radio" name="item_4_3" value="NA">
                <div class="text-center font-medium text-nutri-700">N</div>
            </div>
            <div class="checklist-item-row" data-item-id="4.5">
                <label>4.5 São verificados a temperatura e o aspecto da embalagem dos produtos perecíveis no momento do recebimento.</label>
                <input type="radio" name="item_4_5" value="C">
                <input type="radio" name="item_4_5" value="NC">
                <input type="radio" name="item_4_5" value="NA">
                <div class="text-center font-medium text-nutri-700">I</div>
            </div>

            <div class="section-header px-4 py-3 mt-6 rounded-t-lg">
                <h3 class="font-semibold text-nutri-800">5. ARMAZENAMENTO</h3>
            </div>
            <div class="px-4 py-2 bg-nutri-50">
                <h4 class="font-medium text-nutri-700">5.1 GERAL</h4>
            </div>
            <div class="checklist-item-row" data-item-id="5.3">
                <label>5.3 Os alimentos (não perecíveis) estão dispostos em locais limpos e organizados, sobre estrados e/ou paletes, em quantidades aprovadas, distante do piso e das paredes, em quantidade suficiente, limpos e bem conservados.</label>
                <input type="radio" name="item_5_3" value="C">
                <input type="radio" name="item_5_3" value="NC">
                <input type="radio" name="item_5_3" value="NA">
                <div class="text-center font-medium text-nutri-700">N</div>
            </div>
            <div class="checklist-item-row" data-item-id="5.4">
                <label>5.4 Rede de frio em quantidade suficiente, equipamentos bem conservados, higienizados e com manutenção periódica.</label>
                <input type="radio" name="item_5_4" value="C">
                <input type="radio" name="item_5_4" value="NC">
                <input type="radio" name="item_5_4" value="NA">
                <div class="text-center font-medium text-nutri-700">I</div>
            </div>
            <div class="checklist-item-row" data-item-id="5.6">
                <label>5.6 São armazenados separadamente, não permitindo contaminação cruzada, ou absorção de odores e sabores.</label>
                <input type="radio" name="item_5_6" value="C">
                <input type="radio" name="item_5_6" value="NC">
                <input type="radio" name="item_5_6" value="NA">
                <div class="text-center font-medium text-nutri-700">I</div>
            </div>

            <div class="section-header px-4 py-3 mt-6 rounded-t-lg">
                <h3 class="font-semibold text-nutri-800">6. ÁREA DE PREPARAÇÃO DE ALIMENTOS</h3>
            </div>
            <div class="checklist-item-row" data-item-id="6.1">
                <label>6.1 Durante a preparação dos alimentos, são adotadas medidas a fim de minimizar o risco de contaminação cruzada, sendo tomadas medidas para evitar o contato direto ou indireto entre alimentos crus, semi-preparados e prontos para o consumo.</label>
                <input type="radio" name="item_6_1" value="C">
                <input type="radio" name="item_6_1" value="NC">
                <input type="radio" name="item_6_1" value="NA">
                <div class="text-center font-medium text-nutri-700">I</div>
            </div>
            <div class="checklist-item-row" data-item-id="6.2">
                <label>6.2 Matérias primas e ingredientes caracterizados como perecíveis são expostos à temperatura ambiente somente pelo tempo mínimo necessário para a preparação do alimento.</label>
                <input type="radio" name="item_6_2" value="C">
                <input type="radio" name="item_6_2" value="NC">
                <input type="radio" name="item_6_2" value="NA">
                <div class="text-center font-medium text-nutri-700">I</div>
            </div>
            <div class="checklist-item-row" data-item-id="6.12">
                <label>6.12 O porcionamento dos produtos são feitos sob refrigeração (máximo 5°C).</label>
                <input type="radio" name="item_6_12" value="C">
                <input type="radio" name="item_6_12" value="NC">
                <input type="radio" name="item_6_12" value="NA">
                <div class="text-center font-medium text-nutri-700">I</div>
            </div>
            <div class="checklist-item-row" data-item-id="6.13">
                <label>6.13 Alimentos submetidos ao descongelamento são mantidos em temperatura de refrigeração não sendo permitido o recongelamento.</label>
                <input type="radio" name="item_6_13" value="C">
                <input type="radio" name="item_6_13" value="NC">
                <input type="radio" name="item_6_13" value="NA">
                <div class="text-center font-medium text-nutri-700">I</div>
            </div>
            <div class="checklist-item-row" data-item-id="6.14">
                <label>6.14 Para conservação a quente, os alimentos preparados são submetidos a temperatura superior a 60°C por no máximo 6 horas.</label>
                <input type="radio" name="item_6_14" value="C">
                <input type="radio" name="item_6_14" value="NC">
                <input type="radio" name="item_6_14" value="NA">
                <div class="text-center font-medium text-nutri-700">I</div>
            </div>
            <div class="checklist-item-row" data-item-id="6.20">
                <label>6.20 O gelo para ser utilizado em alimentos e bebidas é fabricado a partir de água potável, isento de contaminantes e manuseado de forma correta e higiênica.</label>
                <input type="radio" name="item_6_20" value="C">
                <input type="radio" name="item_6_20" value="NC">
                <input type="radio" name="item_6_20" value="NA">
                <div class="text-center font-medium text-nutri-700">I</div>
            </div>
            <div class="checklist-item-row" data-item-id="6.21">
                <label>6.21 Alimentos preparados são armazenados adequadamente de maneira a minimizar a contaminação cruzada ou absorção de odores e/ou sabores.</label>
                <input type="radio" name="item_6_21" value="C">
                <input type="radio" name="item_6_21" value="NC">
                <input type="radio" name="item_6_21" value="NA">
                <div class="text-center font-medium text-nutri-700">N</div>
            </div>
        

            <div class="section-header px-4 py-3 mt-6 rounded-t-lg">
                <h3 class="font-semibold text-nutri-800">7. DOCUMENTAÇÃO E REGISTRO</h3>
            </div>
            <div class="px-4 py-2 bg-nutri-50">
                <h4 class="font-medium text-nutri-700">7.1 MANUAL DE BOAS PRÁTICAS DE FABRICAÇÃO</h4>
            </div>
            <div class="checklist-item-row" data-item-id="7.1.6">
                <label>7.1.6 O manual de Boas Práticas está acessível aos responsáveis pela execução das operações.</label>
                <input type="radio" name="item_7_1_6" value="C">
                <input type="radio" name="item_7_1_6" value="NC">
                <input type="radio" name="item_7_1_6" value="NA">
                <div class="text-center font-medium text-nutri-700">N</div>
            </div>
            <div class="checklist-item-row" data-item-id="7.1.7">
                <label>7.1.7 Existência de documentação das ações corretivas a serem adotadas em caso de desvio das medidas de controle.</label>
                <input type="radio" name="item_7_1_7" value="C">
                <input type="radio" name="item_7_1_7" value="NC">
                <input type="radio" name="item_7_1_7" value="NA">
                <div class="text-center font-medium text-nutri-700">N</div>
            </div>

            <div class="px-4 py-2 bg-nutri-50 mt-4">
                <h4 class="font-medium text-nutri-700">7.2 POPs - PROCEDIMENTOS OPERACIONAIS PADRONIZADOS</h4>
            </div>
             <div class="checklist-item-row" data-item-id="7.2.1.1">
                <label>7.2.1.1 Higienização das instalações, equipamentos e utensílios: Existência de POP estabelecido para este item.</label>
                <input type="radio" name="item_7_2_1_1" value="C">
                <input type="radio" name="item_7_2_1_1" value="NC">
                <input type="radio" name="item_7_2_1_1" value="NA">
                <div class="text-center font-medium text-nutri-700">N</div>
            </div>
            <div class="checklist-item-row" data-item-id="7.2.1.2">
                <label>7.2.1.2 Higienização das instalações, equipamentos e utensílios: POP descrito está sendo cumprido.</label>
                <input type="radio" name="item_7_2_1_2" value="C">
                <input type="radio" name="item_7_2_1_2" value="NC">
                <input type="radio" name="item_7_2_1_2" value="NA">
                <div class="text-center font-medium text-nutri-700">N</div>
            </div>
            <div class="checklist-item-row" data-item-id="7.2.2.1">
                <label>7.2.2.1 Controle de potabilidade de água: Existência de POP estabelecido para este item.</label>
                <input type="radio" name="item_7_2_2_1" value="C">
                <input type="radio" name="item_7_2_2_1" value="NC">
                <input type="radio" name="item_7_2_2_1" value="NA">
                <div class="text-center font-medium text-nutri-700">N</div>
            </div>
            <div class="checklist-item-row" data-item-id="7.2.2.2">
                <label>7.2.2.2 Controle de potabilidade de água: POP descrito está sendo cumprido.</label>
                <input type="radio" name="item_7_2_2_2" value="C">
                <input type="radio" name="item_7_2_2_2" value="NC">
                <input type="radio" name="item_7_2_2_2" value="NA">
                <div class="text-center font-medium text-nutri-700">N</div>
            </div>

            <p class="text-sm mt-8 text-gray-500">*NA: Não se aplica ao estabelecimento/operação, conforme o padrão de fiscalização sanitária.</p>
        </div>
        
        <div class="p-8 bg-nutri-100 border-t border-nutri-300">
            <h2 class="text-xl font-semibold text-nutri-700 mb-6 flex items-center">
                <i class="fas fa-chart-bar mr-2"></i> RESULTADO DA AUDITORIA
            </h2>
            <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                <div class="bg-white p-4 rounded-lg shadow-md">
                    <p class="text-sm font-medium text-nutri-600">Pontuação Total / Máxima Possível</p>
                    <p class="text-3xl font-bold text-nutri-800 mt-1"><span id="totalScore">0.0</span> / <span id="maxPossibleScore">0.0</span></p>
                    <p class="text-sm font-medium text-nutri-600 mt-2">Percentual de Conformidade:</p>
                    <p class="text-3xl font-bold text-nutri-800"><span id="compliancePercentage">0.0</span>%</p>
                </div>
                <div class="bg-white p-4 rounded-lg shadow-md">
                    <p class="text-sm font-medium text-nutri-600">Classificação</p>
                    <div id="classificationResult" class="text-2xl font-bold mt-1 text-center py-2 rounded-md">
                        <span class="text-gray-500">Aguardando Avaliação</span>
                    </div>
                    <ul class="text-xs mt-3 space-y-1 text-gray-600">
                        <li class="flex items-center"><span class="inline-block w-3 h-3 bg-green-700 mr-2 rounded-sm"></span> > 90% - Ótimo</li>
                        <li class="flex items-center"><span class="inline-block w-3 h-3 bg-lime-500 mr-2 rounded-sm"></span> 81-90% - Muito Bom</li>
                        <li class="flex items-center"><span class="inline-block w-3 h-3 bg-yellow-500 mr-2 rounded-sm"></span> 71-80% - Bom</li>
                        <li class="flex items-center"><span class="inline-block w-3 h-3 bg-orange-500 mr-2 rounded-sm"></span> 61-70% - Regular</li>
                        <li class="flex items-center"><span class="inline-block w-3 h-3 bg-red-500 mr-2 rounded-sm"></span> ≤ 60% - Insatisfatório</li>
                        <li class="flex items-center"><span class="inline-block w-3 h-3 bg-red-700 mr-2 rounded-sm"></span> CRÍTICO - Itens essenciais não conformes</li>
                    </ul>
                </div>
            </div>

            <div id="criticalItemsContainer" class="hidden mt-6 bg-red-50 p-4 rounded-lg border border-red-200">
                <h3 class="font-bold text-red-700 mb-3"><i class="fas fa-exclamation-triangle mr-2"></i> ATENÇÃO: ITENS CRÍTICOS NÃO CONFORMES</h3>
                <ul id="criticalItemsList" class="list-disc list-inside text-sm text-red-700">
                    </ul>
            </div>
        </div>

        <div class="p-8">
            <h2 class="text-xl font-semibold text-nutri-700 mb-6 flex items-center">
                <i class="fas fa-signature mr-2"></i> ASSINATURAS
            </h2>
            <div class="grid grid-cols-2 gap-8 mt-12 text-sm text-center">
                <div>
                    <div class="signature-line"></div>
                    <p class="mt-2">Nutricionista Responsável</p>
                </div>
                <div>
                    <div class="signature-line"></div>
                    <p class="mt-2">Responsável pela Unidade</p>
                </div>
            </div>
        </div>

        <div class="bg-gray-100 p-4 text-center text-sm text-gray-600">
            <p>Relatório gerado em <span id="currentDate"></span> | Baseado na Resolução RDC n° 216/2004 e outras legislações pertinentes.</p>
        </div>
    </div>

    <div class="max-w-5xl mx-auto text-center mt-8 mb-8">
        <button onclick="window.print()" class="print-button bg-nutri-600 hover:bg-nutri-700 text-white font-bold py-3 px-6 rounded-lg shadow-lg flex items-center justify-center mx-auto">
            <i class="fas fa-print mr-3"></i> IMPRIMIR RELATÓRIO
        </button>
    </div>

    <script>
        // Mapeamento dos tipos de itens e suas pontuações.
        // I: Imprescindível (2 pontos), N: Necessário (1 ponto), R: Recomendável (0.5 ponto), C: Crítico (mesma pontuação do I/N, mas falha o auditório se for NC)
        const itemWeights = {
            '1.1.1': { type: 'I', description: '1.1.1 Área externa livre de focos de insalubridade, materiais em desuso ou estranhos ao ambiente, ausência de lixo, água estagnada.' },
            '1.1.2': { type: 'I', description: '1.1.2 Ausência de vetores/pragas ou vestígios da presença nas imediações.' },
            '1.2.1': { type: 'N', description: '1.2.1 Direto, não comum a outros usos (habitação).' },
            '1.3.1': { type: 'N', description: '1.3.1 Área interna livre de objetos em desuso ou estranhos ao ambiente.' },
            '1.4.1': { type: 'N', description: '1.4.1 Material que permite fácil e apropriada higienização (liso, resistente, drenados com declive, impermeável).' },
            '1.4.2': { type: 'N', description: '1.4.2 Em adequado estado de conservação (livre de defeitos, rachaduras, buracos e outros).' },
            '1.4.3': { type: 'N', description: '1.4.3 Sistema de drenagem dimensionados adequadamente, sem acúmulo de água e/ou resíduos.' },
            '1.4.5': { type: 'N', description: '1.4.5 Drenos, ralos sifonados e grelhas colocadas em locais adequados de forma a facilitar o escoamento e proteger contra a entrada de insetos, roedores.' },
            '1.5.1': { type: 'N', description: '1.5.1 Acabamento liso, em cor clara, impermeável, de fácil limpeza e, quando for o caso, desinfecção.' },
            '1.5.2': { type: 'N', description: '1.5.2 Em adequado estado de conservação (livre de rachaduras, umidade, bolor, descascamento e outros).' },
            '1.6.1': { type: 'N', description: '1.6.1 Acabamento de cor clara, liso, impermeável e de fácil higienização até uma altura adequada para todas as operações.' },
            '1.6.2': { type: 'N', description: '1.6.2 Em adequado estado de conservação (livre de falhas, rachaduras, umidade, descascamento, bolores e outros).' },
            '1.7.1': { type: 'N', description: '1.7.1 Com superfície lisa, de fácil higienização, ajustadas aos batentes, sem falhas de revestimento.' },
            '1.7.2': { type: 'I', description: '1.7.2 Portas externas com fechamento automático (mola, sistema eletrônico ou outro) e com barreiras adequadas para impedir entrada de vetores e outros animais como telas milimétricas ou outro sistema).' },
            '1.7.3': { type: 'N', description: '1.7.3 Em adequado estado de conservação (livre de falhas, rachaduras, umidade, descascamento e outros).' },
            '1.8.1': { type: 'N', description: '1.8.1 Com superfície lisa, de fácil higienização, ajustadas aos batentes, sem falhas de revestimento.' },
            '1.8.2': { type: 'I', description: '1.8.2 Existência de proteção contra insetos e roedores (telas milimétricas ou outro sistema).' },
            '1.8.3': { type: 'R', description: '1.8.3 Telas milimétricas removíveis para facilitar a higienização.' },
            '1.8.4': { type: 'N', description: '1.8.4 Em adequado estado de conservação (livre de falhas, rachaduras, umidade, descascamento e outros).' },
            '1.9.1': { type: 'N', description: '1.9.1 Quando localizados isolados da área de produção, acesso realizado por passagens cobertas e calçadas.' },
            '1.9.2': { type: 'N', description: '1.9.2 Independentes para cada sexo.' },
            '1.9.3': { type: 'N', description: '1.9.3 Instalações sanitárias com vasos sanitários; mictórios e lavatórios íntegros e em proporção adequada ao número de empregados (conforme legislação específica).' },
            '1.9.4': { type: 'N', description: '1.9.4 Instalações sanitárias servidas de água corrente, dotadas de torneira com acionamento automático e conectadas à rede de esgoto ou fossa séptica.' },
            '1.9.5': { type: 'I', description: '1.9.5 Ausência de comunicação direta com a área de trabalho e refeições.' },
            '1.9.6': { type: 'N', description: '1.9.6 Portas com fechamento automático.' },
            '1.9.7': { type: 'N', description: '1.9.7 Pisos e paredes adequadas e apresentando satisfatório estado de conservação.' },
            '1.9.8': { type: 'N', description: '1.9.8 Iluminação e ventilação adequadas.' },
            '1.9.9': { type: 'I', description: '1.9.9 Instalações sanitárias dotadas de produtos destinados à higiene pessoal; papel higiênico, sabonete líquido inodoro e anti-séptico, toalhas de papel não reciclado para mãos ou outros sistema higiênico e seguro para secagem.' },
            '1.9.10': { type: 'N', description: '1.9.10 Presença de lixeiras com tampas e com acionamento não manual.' },
            '1.9.11': { type: 'N', description: '1.9.11 Coleta frequente do lixo.' },
            '1.9.12': { type: 'N', description: '1.9.12 Presença de avisos com procedimentos para lavagem de mãos.' },
            '1.9.13': { type: 'N', description: '1.9.13 Vestiários com área compatível e armários para todos os manipuladores.' },
            '1.9.14': { type: 'N', description: '1.9.14 Apresentam-se organizados e em adequado estado de conservação.' },
            '1.10.1': { type: 'N', description: '1.10.1 Apresentam piso, paredes e teto de material liso, resistente e impermeável, ventilação adequada, em bom estado de conservação e higiene.' },
            '1.10.2': { type: 'N', description: '1.10.2 Possuem produtos para higiene pessoal (sabonete, papel higiênico, papel toalha) e lixeiras com acionamento não manual.' },
            '1.11.1': { type: 'N', description: '1.11.1 Existência de uma equipe responsável pela operação de higienização.' },
            '1.11.2': { type: 'N', description: '1.11.2 A equipe é comprovadamente capacitada com treinamentos (Boas Práticas, Produtos Químicos, Uso correto de EPIs, etc).' },
            '1.11.10': { type: 'I', description: '1.11.10 Utensílios utilizados na higienização de instalações são distintos daqueles usados na higienização das partes dos equipamentos e utensílios que entrem em contato com o alimento.' },
            '1.12.5': { type: 'N', description: '1.12.5 Recipientes e sacos de lixo mantidos íntegros, fechados e distantes do local de preparação e consumo, com acesso restrito a pessoas estranhas, animais domésticos, insetos e roedores.' },
            '1.12.6': { type: 'N', description: '1.12.6 Área de depósito ou recipiente na área externa devidamente higienizado.' },
            '1.12.7': { type: 'N', description: '1.12.7 Existência de POP para manejo de resíduos.' },
            
            // Seção 2. EQUIPAMENTOS, MÓVEIS E UTENSÍLIOS
            '2.1.3': { type: 'I', description: '2.1.3 Equipamentos e utensílios construídos de material que não transmita substâncias tóxicas, odores nem sabores, e que sejam resistentes à corrosão e a repetidas operações de limpeza e desinfecção.' },
            '2.1.4': { type: 'N', description: '2.1.4 Em adequado estado de conservação e funcionamento.' },
            '2.1.5': { type: 'I', description: '2.1.5 Equipamentos de conservação dos alimentos (refrigeradores, congeladores) dotados de termômetros para monitoramento.' },
            '2.4.6': { type: 'N', description: '2.4.6 Utensílios de limpeza para as diversas áreas de manipulação são identificados e exclusivos para as áreas.' },
            '2.4.7': { type: 'N', description: '2.4.7 Responsáveis pela higienização utilizam uniforme adequado e EPIs quando necessário.' },

            // Seção 3. MANIPULADORES
            '3.1.1': { type: 'I', description: '3.1.1 Utilização de uniforme de trabalho de cor clara adequada à atividade e exclusivo para área de produção.' },
            '3.2.1': { type: 'I', description: '3.2.1 Manipuladores apresentam-se asseados, com cabelos protegidos com redes ou toucas, unhas curtas, sem esmalte, sem adornos (anéis, pulseiras, brincos, colares, relógios).' },
            '3.2.2': { type: 'I', description: '3.2.2 Manipuladores não espirram sobre os alimentos, não cospem, não tossem, não fumam, não manipulam dinheiro ou não praticam outros atos que possam contaminar o alimento.' },
            '3.2.3': { type: 'N', description: '3.2.3 Cartazes de orientação aos manipuladores sobre a correta lavagem das mãos e demais hábitos de higiene afixados em locais apropriados.' },
            '3.6.4': { type: 'N', description: '3.6.4 O programa de controle de saúde é documentado e registra o resultado dos exames e as condutas adotadas.' },

            // Seção 4. RECEPÇÃO MATÉRIAS-PRIMAS, INGREDIENTES E EMBALAGENS
            '4.2': { type: 'N', description: '4.2 O restaurante possui um POP para recebimento de matéria prima, ingredientes e embalagens.' },
            '4.3': { type: 'N', description: '4.3 O responsável pelo recebimento está devidamente capacitado.' },
            '4.5': { type: 'I', description: '4.5 São verificados a temperatura e o aspecto da embalagem dos produtos perecíveis no momento do recebimento.' },

            // Seção 5. ARMAZENAMENTO
            '5.3': { type: 'N', description: '5.3 Os alimentos (não perecíveis) estão dispostos em locais limpos e organizados, sobre estrados e/ou paletes, em quantidades aprovadas, distante do piso e das paredes, em quantidade suficiente, limpos e bem conservados.' },
            '5.4': { type: 'I', description: '5.4 Rede de frio em quantidade suficiente, equipamentos bem conservados, higienizados e com manutenção periódica.' },
            '5.6': { type: 'I', description: '5.6 São armazenados separadamente, não permitindo contaminação cruzada, ou absorção de odores e sabores.' },
            
            // Seção 6. ÁREA DE PREPARAÇÃO DE ALIMENTOS
            '6.1': { type: 'I', description: '6.1 Durante a preparação dos alimentos, são adotadas medidas a fim de minimizar o risco de contaminação cruzada, sendo tomadas medidas para evitar o contato direto ou indireto entre alimentos crus, semi-preparados e prontos para o consumo.' },
            '6.2': { type: 'I', description: '6.2 Matérias primas e ingredientes caracterizados como perecíveis são expostos à temperatura ambiente somente pelo tempo mínimo necessário para a preparação do alimento.' },
            '6.12': { type: 'I', description: '6.12 O porcionamento dos produtos são feitos sob refrigeração (máximo 5°C).' },
            '6.13': { type: 'I', description: '6.13 Alimentos submetidos ao descongelamento são mantidos em temperatura de refrigeração não sendo permitido o recongelamento.' },
            '6.14': { type: 'I', description: '6.14 Para conservação a quente, os alimentos preparados são submetidos a temperatura superior a 60°C por no máximo 6 horas.' },
            '6.20': { type: 'I', description: '6.20 O gelo para ser utilizado em alimentos e bebidas é fabricado a partir de água potável, isento de contaminantes e manuseado de forma correta e higiênica.' },
            '6.21': { type: 'N', description: '6.21 Alimentos preparados são armazenados adequadamente de maneira a minimizar a contaminação cruzada ou absorção de odores e/ou sabores.' },

            // Seção 7. DOCUMENTAÇÃO E REGISTRO
            '7.1.6': { type: 'N', description: '7.1.6 O manual de Boas Práticas está acessível aos responsáveis pela execução das operações.' },
            '7.1.7': { type: 'N', description: '7.1.7 Existência de documentação das ações corretivas a serem adotadas em caso de desvio das medidas de controle.' },
            '7.2.1.1': { type: 'N', description: '7.2.1.1 Higienização das instalações, equipamentos e utensílios: Existência de POP estabelecido para este item.' },
            '7.2.1.2': { type: 'N', description: '7.2.1.2 Higienização das instalações, equipamentos e utensílios: POP descrito está sendo cumprido.' },
            '7.2.2.1': { type: 'N', description: '7.2.2.1 Controle de potabilidade de água: Existência de POP estabelecido para este item.' },
            '7.2.2.2': { type: 'N', description: '7.2.2.2 Controle de potabilidade de água: POP descrito está sendo cumprido.' }
        };

        let totalScore = 0;
        let maxPossibleScore = 0;
        let criticalNonCompliance = []; // Array de IDs de itens críticos não conformes

        function getScoreValues(type) {
            switch(type) {
                case 'I': // Imprescindível
                    return { max: 2, conform: 2 };
                case 'N': // Necessário
                    return { max: 1, conform: 1 };
                case 'R': // Recomendável
                    return { max: 0.5, conform: 0.5 };
                // O tipo C (Crítico) é geralmente um item Imprescindível (I) ou Necessário (N)
                // com uma implicação de falha no sistema se NC. Para a pontuação, tratamos como I ou N.
                // Como não há um tipo 'C' no HTML, vamos assumir que os itens 'I' são críticos.
                default:
                    return { max: 0, conform: 0 };
            }
        }

        function updateScore(status, itemId) {
            const itemInfo = itemWeights[itemId];
            if (!itemInfo) return;

            const itemElement = document.querySelector(`.checklist-item-row[data-item-id="${itemId}"]`);
            
            // Recuperar e remover a pontuação anterior (se existir)
            const previousStatus = itemElement.dataset.status;
            let currentScore = parseFloat(itemElement.dataset.currentScore || 0);
            let currentMaxScore = parseFloat(itemElement.dataset.currentMaxScore || 0);

            totalScore -= currentScore;
            maxPossibleScore -= currentMaxScore;
            
            // Determinar nova pontuação e pontuação máxima
            let newScore = 0;
            let newMaxScore = 0;
            const scoreValues = getScoreValues(itemInfo.type);
            newMaxScore = scoreValues.max;

            // Se for 'C', a pontuação é a máxima. Se for 'NC', a pontuação é 0. Se for 'NA', a pontuação não conta para o total/máximo.
            if (status === 'C') {
                newScore = scoreValues.conform;
                itemElement.classList.remove('critical-item-highlight');
            } else if (status === 'NC') {
                newScore = 0;
                // Marcar itens Imprescindíveis (I) como críticos não conformes.
                if (itemInfo.type === 'I' || itemInfo.type === 'C') {
                    itemElement.classList.add('critical-item-highlight');
                } else {
                    itemElement.classList.remove('critical-item-highlight');
                }
            } else if (status === 'NA') {
                newMaxScore = 0; // Se NA, não contribui para o máximo.
                newScore = 0;
                itemElement.classList.remove('critical-item-highlight');
            }

            // Atualizar o total
            totalScore += newScore;
            maxPossibleScore += newMaxScore;

            // Salvar a nova pontuação no elemento para cálculos futuros
            itemElement.dataset.status = status;
            itemElement.dataset.currentScore = newScore;
            itemElement.dataset.currentMaxScore = newMaxScore;

            calculateOverallScore();
        }

        function calculateOverallScore() {
            let currentTotalScore = 0;
            let currentMaxPossibleScore = 0;
            let criticalNonCompliantItems = [];
            
            // Reiniciar os totais com base no DOM para garantir que todos os itens sejam considerados
            const allItems = document.querySelectorAll('.checklist-item-row');
            allItems.forEach(itemElement => {
                const itemId = itemElement.dataset.itemId;
                const itemInfo = itemWeights[itemId];
                if (!itemInfo) return;

                const status = itemElement.dataset.status;
                const scoreValues = getScoreValues(itemInfo.type);

                let newMaxScore = scoreValues.max;
                let newScore = 0;

                if (status === 'C') {
                    newScore = scoreValues.conform;
                } else if (status === 'NC') {
                    newScore = 0;
                    if (itemInfo.type === 'I' || itemInfo.type === 'C') {
                        criticalNonCompliantItems.push(itemId);
                    }
                } else if (status === 'NA') {
                    newMaxScore = 0;
                    newScore = 0;
                }

                currentTotalScore += newScore;
                currentMaxPossibleScore += newMaxScore;

                // Atualizar o data-attribute para o caso de ter sido inicializado (importante para o updateScore)
                itemElement.dataset.currentScore = newScore;
                itemElement.dataset.currentMaxScore = newMaxScore;
            });
            
            totalScore = currentTotalScore;
            maxPossibleScore = currentMaxPossibleScore;
            criticalNonCompliance = criticalNonCompliantItems;

            const percentage = (maxPossibleScore > 0) ? (totalScore / maxPossibleScore) * 100 : 0;
            const percentageRounded = percentage.toFixed(1);

            document.getElementById('totalScore').textContent = totalScore.toFixed(1);
            document.getElementById('maxPossibleScore').textContent = maxPossibleScore.toFixed(1);
            document.getElementById('compliancePercentage').textContent = percentageRounded;
            
            updateClassification(percentageRounded);
            updateCriticalItemsList();
        }

        function updateClassification(percentage) {
            const resultElement = document.getElementById('classificationResult');
            let classificationText = '';
            let bgColor = '';
            let textColor = '';

            if (criticalNonCompliance.length > 0) {
                classificationText = 'FALHA CRÍTICA';
                bgColor = 'bg-red-700';
                textColor = 'text-white';
            } else if (percentage > 90) {
                classificationText = 'ÓTIMO';
                bgColor = 'bg-green-700';
                textColor = 'text-white';
            } else if (percentage > 80) {
                classificationText = 'MUITO BOM';
                bgColor = 'bg-lime-500';
                textColor = 'text-gray-800';
            } else if (percentage > 70) {
                classificationText = 'BOM';
                bgColor = 'bg-yellow-500';
                textColor = 'text-gray-800';
            } else if (percentage > 60) {
                classificationText = 'REGULAR';
                bgColor = 'bg-orange-500';
                textColor = 'text-white';
            } else {
                classificationText = 'INSATISFATÓRIO';
                bgColor = 'bg-red-500';
                textColor = 'text-white';
            }

            resultElement.innerHTML = classificationText;
            resultElement.className = `text-2xl font-bold mt-1 text-center py-2 rounded-md ${bgColor} ${textColor}`;
        }

        function updateCriticalItemsList() {
            const container = document.getElementById('criticalItemsContainer');
            const list = document.getElementById('criticalItemsList');
            list.innerHTML = '';

            if (criticalNonCompliance.length > 0) {
                container.classList.remove('hidden');
                criticalNonCompliance.forEach(itemId => {
                    const itemDescription = itemWeights[itemId] ? itemWeights[itemId].description : `Item ${itemId} (descrição não encontrada)`;
                    const listItem = document.createElement('li');
                    listItem.textContent = itemDescription;
                    list.appendChild(listItem);
                });
            } else {
                container.classList.add('hidden');
            }
        }

        // Initialize scores and attach event listeners
        document.addEventListener('DOMContentLoaded', () => {
            const allRadioButtons = document.querySelectorAll('input[type="radio"]');
            allRadioButtons.forEach(radio => {
                // Adicionar o event listener que chama a função updateScore
                radio.addEventListener('change', (event) => {
                    // O nome do rádio é item_X_Y_Z, transformamos para o ID X.Y.Z
                    const itemId = event.target.name.replace('item_', '').replace(/_/g, '.');
                    updateScore(event.target.value, itemId);
                });
            });

            // Adicionar o atributo data-status inicial e forçar o cálculo inicial
            // Isso garante que o cálculo de maxPossibleScore esteja correto no início
            const allItems = document.querySelectorAll('.checklist-item-row');
            allItems.forEach(itemElement => {
                itemElement.dataset.status = '';
                itemElement.dataset.currentScore = 0;
                itemElement.dataset.currentMaxScore = 0;
            });

            // Set current date
            document.getElementById('currentDate').textContent = new Date().toLocaleDateString('pt-BR');

            // Initial calculation (all items unchecked)
            calculateOverallScore();
        });
    </script>
</body>
</html>

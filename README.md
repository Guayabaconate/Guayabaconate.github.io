<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>PRONAM - Hipertensión Arterial Sistémica</title>
    <!-- Tailwind CSS CDN for a clean and responsive style -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Import the Inter font for the text -->
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap');
        
        body {
            font-family: 'Inter', sans-serif;
            background-color: #fef2f2; /* bg-red-50 */
        }
        
        /* Styles for the side menu */
        .side-menu {
            position: fixed;
            top: 0;
            left: -100%;
            height: 100%;
            width: 80%;
            max-width: 320px;
            background-color: #fff;
            box-shadow: 2px 0 5px rgba(0,0,0,0.1);
            transition: left 0.3s ease-in-out;
            z-index: 50;
        }
        
        .side-menu.open {
            left: 0;
        }

        /* Styles for the overlay when the menu is open */
        .overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.5);
            opacity: 0;
            visibility: hidden;
            transition: opacity 0.3s ease-in-out, visibility 0.3s ease-in-out;
            z-index: 40;
        }

        .overlay.visible {
            opacity: 1;
            visibility: visible;
        }
        
        /* Styles for the back button */
        .back-button {
            position: fixed;
            bottom: 2rem;
            left: 2rem;
            opacity: 0;
            visibility: hidden;
            transition: opacity 0.3s ease-in-out, visibility 0.3s ease-in-out;
            z-index: 50;
        }

        .back-button.visible {
            opacity: 1;
            visibility: visible;
        }
    </style>
</head>
<body class="flex flex-col min-h-screen">

    <!-- Overlay to close the menu by clicking outside of it -->
    <div id="overlay" class="overlay"></div>

    <!-- Slide-out side menu -->
    <nav id="side-menu" class="side-menu p-6 overflow-y-auto">
        <div class="flex justify-end mb-4">
            <button id="close-menu-btn" class="text-gray-500 hover:text-red-600 transition-colors duration-200">
                <svg class="w-8 h-8" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"></path>
                </svg>
            </button>
        </div>
        <ul class="space-y-4 font-semibold text-gray-800">
            <li><a href="#" data-target="inicio" class="block py-2 px-4 rounded hover:bg-red-100 transition-colors duration-200">Inicio</a></li>
            <li><a href="#" data-target="introduccion" class="block py-2 px-4 rounded hover:bg-red-100 transition-colors duration-200">Introducción y Contexto</a></li>
            <li><a href="#" data-target="fisiopatologia" class="block py-2 px-4 rounded hover:bg-red-100 transition-colors duration-200">Fisiopatología</a></li>
            <li><a href="#" data-target="repercusión" class="block py-2 px-4 rounded hover:bg-red-100 transition-colors duration-200">Repercusión Clínica</a></li>
            <li><a href="#" data-target="tamizaje" class="block py-2 px-4 rounded hover:bg-red-100 transition-colors duration-200">Tamizaje y Medición</a></li>
            <li><a href="#" data-target="diagnostico" class="block py-2 px-4 rounded hover:bg-red-100 transition-colors duration-200">Diagnóstico y Tabla 1</a></li>
            <li><a href="#" data-target="tratamiento" class="block py-2 px-4 rounded hover:bg-red-100 transition-colors duration-200">Tratamiento y Tablas</a></li>
            <li><a href="#" data-target="emergencia" class="block py-2 px-4 rounded hover:bg-red-100 transition-colors duration-200">Urgencia y Emergencia Hipertensiva</a></li>
            <li><a href="#" data-target="grupos" class="block py-2 px-4 rounded hover:bg-red-100 transition-colors duration-200">Grupos Especiales</a></li>
            <li><a href="#" data-target="referencia" class="block py-2 px-4 rounded hover:bg-red-100 transition-colors duration-200">Criterios de Referencia</a></li>
            <li><a href="#" data-target="expertos" class="block py-2 px-4 rounded hover:bg-red-100 transition-colors duration-200">Grupo de Expertos</a></li>
            <li><a href="#" data-target="comite" class="block py-2 px-4 rounded hover:bg-red-100 transition-colors duration-200">Comité Ejecutivo PRONAM</a></li>
            <li><a href="#" data-target="glosario" class="block py-2 px-4 rounded hover:bg-red-100 transition-colors duration-200">Glosario de Abreviaturas</a></li>
        </ul>
    </nav>

    <!-- Fixed top navigation bar -->
    <header class="bg-red-900 text-white p-4 sticky top-0 z-40 shadow-lg flex items-center justify-between sm:justify-center">
        <!-- Hamburger menu button for mobile -->
        <button id="open-menu-btn" class="sm:hidden text-white hover:text-orange-400 transition-colors duration-200 mr-4">
            <svg class="w-8 h-8" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16m-7 6h7"></path>
            </svg>
        </button>
        <!-- Document title -->
        <a href="#" data-target="inicio" class="text-xl font-bold text-orange-400 hover:text-white transition-colors duration-200">PRONAM</a>
        <nav class="hidden sm:flex flex-wrap justify-center items-center gap-4 ml-8">
            <ul class="flex flex-wrap items-center gap-4 text-sm font-semibold">
                <li><a href="#" data-target="introduccion" class="hover:text-orange-400 transition-colors duration-200 px-2 py-1 rounded">Introducción</a></li>
                <li><a href="#" data-target="fisiopatologia" class="hover:text-orange-400 transition-colors duration-200 px-2 py-1 rounded">Fisiopatología</a></li>
                <li><a href="#" data-target="repercusión" class="hover:text-orange-400 transition-colors duration-200 px-2 py-1 rounded">Repercusión Clínica</a></li>
                <li><a href="#" data-target="tamizaje" class="hover:text-orange-400 transition-colors duration-200 px-2 py-1 rounded">Tamizaje</a></li>
                <li><a href="#" data-target="diagnostico" class="hover:text-orange-400 transition-colors duration-200 px-2 py-1 rounded">Diagnóstico</a></li>
                <li><a href="#" data-target="tratamiento" class="hover:text-orange-400 transition-colors duration-200 px-2 py-1 rounded">Tratamiento</a></li>
                <li><a href="#" data-target="emergencia" class="hover:text-orange-400 transition-colors duration-200 px-2 py-1 rounded">Emergencia Hipertensiva</a></li>
                <li><a href="#" data-target="grupos" class="hover:text-orange-400 transition-colors duration-200 px-2 py-1 rounded">Grupos Especiales</a></li>
                <li><a href="#" data-target="referencia" class="hover:text-orange-400 transition-colors duration-200 px-2 py-1 rounded">Criterios de Referencia</a></li>
                <li><a href="#" data-target="expertos" class="hover:text-orange-400 transition-colors duration-200 px-2 py-1 rounded">Expertos</a></li>
                <li><a href="#" data-target="comite" class="hover:text-orange-400 transition-colors duration-200 px-2 py-1 rounded">Comité Ejecutivo</a></li>
                <li><a href="#" data-target="glosario" class="hover:text-orange-400 transition-colors duration-200 px-2 py-1 rounded">Glosario</a></li>
            </ul>
        </nav>
    </header>

    <!-- Main content container for the pages -->
    <main id="main-content" class="flex-1 p-6 sm:p-8">
        
        <!-- Section: Inicio -->
        <div id="inicio" class="page-section max-w-4xl mx-auto">
            <section class="bg-white rounded-xl shadow-md p-6 sm:p-8">
                <header class="mb-6 text-center">
                    <h1 class="text-4xl sm:text-5xl font-extrabold text-red-800 mb-2 leading-tight">Bienvenido al Módulo de Hipertensión Arterial Sistémica</h1>
                </header>
                <div class="text-gray-600 leading-relaxed space-y-4 text-center">
                    <p>Este es el <strong>Protocolo Nacional de Atención Médica (PRONAM)</strong> para la Hipertensión Arterial Sistémica, un documento clave de la Secretaría de Salud del Gobierno de México. El material está diseñado para ayudarte a entender los fundamentos, los actores principales y el glosario de términos técnicos.</p>
                    <p>El documento sobre hipertensión fue desarrollado por el grupo de trabajo sobre el manejo de la presión arterial elevada y la hipertensión de la Sociedad Europea de Cardiología (ESC) y avalado por la Europ.</p>
                </div>
            </section>
        </div>
        
        <!-- Section: Introducción y Contexto -->
        <div id="introduccion" class="page-section hidden max-w-4xl mx-auto">
            <section class="bg-white rounded-xl shadow-md p-6 sm:p-8">
                <h2 class="text-3xl font-bold text-red-800 mb-4">Introducción y Contexto</h2>
                <div class="text-gray-600 leading-relaxed space-y-4">
                    <p>Las <strong>Enfermedades No Transmisibles (ENT)</strong> son la principal causa de muerte a nivel global, responsables de aproximadamente 41 millones de fallecimientos cada año. De estos, 15 millones ocurren en personas de 30 a 70 años.</p>

                    <p>En México, las ENT han sido la principal causa de morbimortalidad desde 2011, representando cerca del 70% de las muertes totales. Las ENT con mayor prevalencia son:</p>
                    <ul class="list-disc list-inside space-y-2 pl-4">
                        <li>Enfermedades cardiovasculares</li>
                        <li>Cáncer</li>
                        <li>Enfermedades respiratorias crónicas</li>
                        <li>Diabetes</li>
                    </ul>

                    <p>El Plan de Salud del Estado Mexicano (2019-2024) busca garantizar el acceso a servicios de salud de calidad. Para lograrlo, es crucial contar con instrumentos normativos como este protocolo que orienten las decisiones clínicas y de gestión.</p>

                    <p>La <strong>Hipertensión Arterial Sistémica (HAS)</strong> es un factor de riesgo clave para las enfermedades cardiovasculares y una de las causas más importantes de muerte prematura y discapacidad. Por ello, este <strong>Protocolo Nacional de Atención Médica (PRONAM)</strong> sobre HAS busca:</p>
                    <ul class="list-disc list-inside space-y-2 pl-4">
                        <li>Estandarizar la atención médica a nivel nacional.</li>
                        <li>Contribuir a la detección oportuna y al seguimiento correcto del padecimiento.</li>
                        <li>Reducir las complicaciones de la enfermedad.</li>
                        <li>Mejorar la calidad y esperanza de vida de la población mexicana.</li>
                    </ul>
                    <p>Este documento considera las particularidades del sistema de salud mexicano y las recomendaciones más actualizadas, como las de la Sociedad Europea de Cardiología (ESC) y la Sociedad Europea de Hipertensión (ESH).</p>
                </div>
            </section>
        </div>

        <!-- Section: Fisiopatología -->
        <div id="fisiopatologia" class="page-section hidden max-w-4xl mx-auto">
            <section class="bg-white rounded-xl shadow-md p-6 sm:p-8">
                <h2 class="text-3xl font-bold text-red-800 mb-4">Fisiopatología</h2>
                <div class="text-gray-600 leading-relaxed space-y-4">
                    <p>La hipertensión arterial se define como una elevación sostenida de la presión arterial por encima de los valores considerados normales. Su fisiopatología es un proceso complejo y multifactorial que involucra múltiples sistemas de regulación de la presión arterial. En la mayoría de los casos de hipertensión arterial primaria (esencial), la causa exacta es desconocida, pero se considera que es el resultado de la interacción de factores genéticos y ambientales. Los principales mecanismos fisiopatológicos incluyen:</p>
                    <ol class="list-decimal list-inside space-y-2 pl-4">
                        <li>Aumento de la resistencia vascular periférica, debido a una vasoconstricción anormal o a un remodelado de los vasos sanguíneos.</li>
                        <li>Aumento del gasto cardíaco, relacionado con un incremento en el volumen sanguíneo o la contractilidad del corazón.</li>
                        <li>Disfunción del sistema renina-angiotensina-aldosterona (SRAA), que regula el volumen de líquidos y el tono vascular. La activación excesiva de este sistema puede llevar a vasoconstricción y retención de sodio y agua.</li>
                        <li>Activación del sistema nervioso simpático, que provoca un aumento de la frecuencia cardíaca y la vasoconstricción, lo que incrementa la presión arterial.</li>
                        <li>Disfunción endotelial, que reduce la producción de sustancias vasodilatadoras (como el óxido nítrico) y aumenta la de sustancias vasoconstrictoras (como la endotelina).</li>
                        <li>Alteración en el manejo renal del sodio, que lleva a un mayor volumen sanguíneo y, por consiguiente, a un aumento de la presión arterial.</li>
                    </ol>
                </div>
            </section>
        </div>

        <!-- Section: Repercusión Clínica -->
        <div id="repercusión" class="page-section hidden max-w-4xl mx-auto">
            <section class="bg-white rounded-xl shadow-md p-6 sm:p-8">
                <h2 class="text-3xl font-bold text-red-800 mb-4">Repercusión Clínica</h2>
                <div class="text-gray-600 leading-relaxed space-y-4">
                    <p>La HAS no controlada es el principal factor de riesgo de las enfermedades cardiovasculares y cerebrovasculares, lo que explica la alta tasa de morbimortalidad asociada. La exposición prolongada a una presión arterial elevada causa daño progresivo en los órganos blanco. Estos efectos, a menudo asintomáticos en las etapas iniciales, incluyen:</p>
                    <ul class="list-disc list-inside space-y-2 pl-4">
                        <li><strong class="font-semibold">Cerebro:</strong> Enfermedad cerebrovascular (EVC) isquémica o hemorrágica, isquemia cerebral transitoria (ICT) y demencia vascular.</li>
                        <li><strong class="font-semibold">Corazón:</strong> Hipertrofia del ventrículo izquierdo (HVI), insuficiencia cardíaca, infarto agudo de miocardio (IAM) y enfermedad arterial coronaria.</li>
                        <li><strong class="font-semibold">Riñón:</strong> Enfermedad renal crónica (ERC) que puede progresar a enfermedad renal en etapa terminal.</li>
                        <li><strong class="font-semibold">Vasos sanguíneos:</strong> Aterosclerosis acelerada, aneurismas y disecciones arteriales.</li>
                        <li><strong class="font-semibold">Ojos:</strong> Retinopatía hipertensiva que puede llevar a la pérdida de la visión.</li>
                    </ul>
                    <p>La detección y el manejo temprano de la HAS son esenciales para prevenir o retrasar la aparición de estas complicaciones, reducir la carga de enfermedad, los años de vida ajustados por discapacidad (AVAD) y, en última instancia, mejorar la calidad de vida y la supervivencia de los pacientes.</p>
                </div>
            </section>
        </div>

        <!-- Section: Tamizaje y Medición -->
        <div id="tamizaje" class="page-section hidden max-w-4xl mx-auto">
            <section class="bg-white rounded-xl shadow-md p-6 sm:p-8">
                <h2 class="text-3xl font-bold text-red-800 mb-4">Tamizaje y Medición</h2>
                <div class="text-gray-600 leading-relaxed space-y-4">
                    <p>Se recomienda la toma de la presión arterial a todos los adultos mayores de 20 años cada año, y en caso de sospecha, iniciar el tratamiento farmacológico si es necesario.</p>
                    <p>Para la medición en el consultorio, se deben seguir los siguientes pasos:</p>
                    <ul class="list-disc list-inside space-y-2 pl-4">
                        <li>El paciente debe estar en reposo al menos 5 minutos, sentado con la espalda apoyada, los pies en el suelo, las piernas sin cruzar y el brazo a la altura del corazón.</li>
                        <li>Se debe utilizar un brazalete adecuado al tamaño del brazo.</li>
                        <li>La medición debe realizarse en ambos brazos en la primera consulta, para detectar cualquier diferencia significativa.</li>
                        <li>Se deben realizar al menos dos lecturas con un minuto de separación y promediarlas para obtener un valor más preciso.</li>
                    </ul>
                    <p>Se puede realizar Monitoreo Ambulatorio de Presión Arterial (MAPA) o de forma manual con un baumanómetro aneroide o digital validado.</p>
                </div>
            </section>
        </div>

        <!-- Section: Diagnóstico y Tabla 1 -->
        <div id="diagnostico" class="page-section hidden max-w-4xl mx-auto">
            <section class="bg-white rounded-xl shadow-md p-6 sm:p-8">
                <h2 class="text-3xl font-bold text-red-800 mb-4">Diagnóstico y Tabla 1</h2>
                <div class="text-gray-600 leading-relaxed space-y-4">
                    <p>El diagnóstico de la hipertensión arterial se basa en la medición de la presión arterial en el consultorio. Los valores se clasifican en categorías para determinar el grado de la enfermedad.</p>
                    <h3 class="text-xl font-semibold text-gray-800 mt-6 mb-2">Tabla 1: Clasificación de la Presión Arterial en Adultos según la ACC/AHA 2017</h3>
                    <div class="overflow-x-auto rounded-lg shadow-md mt-6">
                        <table class="min-w-full divide-y divide-gray-200">
                            <thead class="bg-gray-100">
                                <tr>
                                    <th scope="col" class="px-6 py-3 text-left text-xs font-bold text-gray-600 uppercase tracking-wider">Categoría</th>
                                    <th scope="col" class="px-6 py-3 text-left text-xs font-bold text-gray-600 uppercase tracking-wider">Presión Sistólica (mmHg)</th>
                                    <th scope="col" class="px-6 py-3 text-left text-xs font-bold text-gray-600 uppercase tracking-wider">Presión Diastólica (mmHg)</th>
                                </tr>
                            </thead>
                            <tbody class="bg-white divide-y divide-gray-200">
                                <tr>
                                    <td class="px-6 py-4 whitespace-nowrap text-sm font-medium text-gray-900">Normal</td>
                                    <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">&lt; 120</td>
                                    <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">y &lt; 80</td>
                                </tr>
                                <tr>
                                    <td class="px-6 py-4 whitespace-nowrap text-sm font-medium text-gray-900">Elevada</td>
                                    <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">120-129</td>
                                    <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">y &lt; 80</td>
                                </tr>
                                <tr>
                                    <td class="px-6 py-4 whitespace-nowrap text-sm font-medium text-gray-900">HTA Estadio 1</td>
                                    <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">130-139</td>
                                    <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">o 80-89</td>
                                </tr>
                                <tr>
                                    <td class="px-6 py-4 whitespace-nowrap text-sm font-medium text-gray-900">HTA Estadio 2</td>
                                    <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">≥ 140</td>
                                    <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">o ≥ 90</td>
                                </tr>
                            </tbody>
                        </table>
                    </div>
                </div>
            </section>
        </div>
        
        <!-- Section: Tratamiento y Tablas -->
        <div id="tratamiento" class="page-section hidden max-w-4xl mx-auto">
            <section class="bg-white rounded-xl shadow-md p-6 sm:p-8">
                <h2 class="text-3xl font-bold text-red-800 mb-4">Tratamiento</h2>
                <div class="text-gray-600 leading-relaxed space-y-4">
                    <p>El tratamiento de la HAS se enfoca en la modificación del estilo de vida y, si es necesario, en el tratamiento farmacológico.</p>
                    <p><strong class="font-semibold">Tratamiento no farmacológico:</strong></p>
                    <ul class="list-disc list-inside space-y-2 pl-4">
                        <li>Dieta saludable (dieta DASH).</li>
                        <li>Reducción de sodio en la dieta.</li>
                        <li>Ejercicio regular.</li>
                        <li>Moderación en el consumo de alcohol.</li>
                        <li>Control de peso.</li>
                    </ul>
                    <p><strong class="font-semibold">Tratamiento farmacológico:</strong></p>
                    <p>La selección del medicamento inicial y la estrategia de tratamiento deben individualizarse según el grado de HTA, la presencia de DOB, otros factores de riesgo cardiovascular y comorbilidades. Se recomienda iniciar con monoterapia si la presión es menor a 160/100 mmHg. Si la PA es mayor, se puede considerar la terapia combinada.</p>
                    <h3 class="text-xl font-semibold text-gray-800 mt-6 mb-2">Tabla 2: Opciones de Tratamiento Farmacológico</h3>
                    <div class="overflow-x-auto rounded-lg shadow-md">
                        <table class="min-w-full divide-y divide-gray-200">
                            <thead class="bg-gray-100">
                                <tr>
                                    <th class="px-6 py-3 text-left text-xs font-bold text-gray-600 uppercase tracking-wider">Clase de Medicamento</th>
                                    <th class="px-6 py-3 text-left text-xs font-bold text-gray-600 uppercase tracking-wider">Ejemplos</th>
                                    <th class="px-6 py-3 text-left text-xs font-bold text-gray-600 uppercase tracking-wider">Dosis (mg/día)</th>
                                    <th class="px-6 py-3 text-left text-xs font-bold text-gray-600 uppercase tracking-wider">Comentarios</th>
                                </tr>
                            </thead>
                            <tbody class="bg-white divide-y divide-gray-200">
                                <tr>
                                    <td class="px-6 py-4 whitespace-nowrap text-sm font-medium text-gray-900">IECA</td>
                                    <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">Captopril, Enalapril, Lisinopril</td>
                                    <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">25-150 (Captopril), 5-40 (Enalapril), 10-40 (Lisinopril)</td>
                                    <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">Medicamentos de primera línea.</td>
                                </tr>
                                <tr>
                                    <td class="px-6 py-4 whitespace-nowrap text-sm font-medium text-gray-900">ARA II</td>
                                    <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">Losartán, Valsartán, Irbesartán</td>
                                    <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">25-100 (Losartán), 80-320 (Valsartán), 75-300 (Irbesartán)</td>
                                    <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">Alternativa a IECA si hay intolerancia.</td>
                                </tr>
                                <tr>
                                    <td class="px-6 py-4 whitespace-nowrap text-sm font-medium text-gray-900">Diuréticos</td>
                                    <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">Hidroclorotiazida, Clortalidona</td>
                                    <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">12.5-50 (Hidroclorotiazida), 12.5-50 (Clortalidona)</td>
                                    <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">Eficaces, especialmente en ancianos.</td>
                                </tr>
                                <tr>
                                    <td class="px-6 py-4 whitespace-nowrap text-sm font-medium text-gray-900">Calcioantagonistas</td>
                                    <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">Amlodipino, Nifedipino</td>
                                    <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">2.5-10 (Amlodipino), 30-90 (Nifedipino de liberación prolongada)</td>
                                    <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">Eficaces en ancianos.</td>
                                </tr>
                            </tbody>
                        </table>
                    </div>
                </div>
            </section>
        </div>
        
        <!-- Section: Urgencia y Emergencia Hipertensiva -->
        <div id="emergencia" class="page-section hidden max-w-4xl mx-auto">
            <section class="bg-white rounded-xl shadow-md p-6 sm:p-8">
                <h2 class="text-3xl font-bold text-red-800 mb-4">Urgencia y Emergencia Hipertensiva</h2>
                <div class="text-gray-600 leading-relaxed space-y-4">
                    <p><strong class="font-semibold">Urgencia Hipertensiva:</strong> Elevación de la PA (>180/120 mmHg) sin evidencia de daño a órgano blanco agudo. El manejo es ambulatorio y el objetivo es reducir la PA de forma gradual en 24-48 horas. Se utiliza medicación oral.</p>
                    <p><strong class="font-semibold">Emergencia Hipertensiva:</strong> Elevación severa de la PA (>180/120 mmHg) con evidencia de daño a órgano blanco agudo y progresivo. Requiere hospitalización y tratamiento inmediato con medicamentos parenterales para reducir la PA en minutos u horas. Ejemplos de daño agudo: EVC, infarto al miocardio, edema pulmonar, disección aórtica, preeclampsia-eclampsia.</p>
                </div>
            </section>
        </div>
        
        <!-- Section: Grupos Especiales -->
        <div id="grupos" class="page-section hidden max-w-4xl mx-auto">
            <section class="bg-white rounded-xl shadow-md p-6 sm:p-8">
                <h2 class="text-3xl font-bold text-red-800 mb-4">Grupos Especiales</h2>
                <div class="text-gray-600 leading-relaxed space-y-4">
                    <p>El manejo de la hipertensión en ciertos grupos de pacientes requiere consideraciones especiales. Estos incluyen:</p>
                    <ul class="list-disc list-inside space-y-2 pl-4">
                        <li><strong class="font-semibold">Hipertensión en embarazadas:</strong> El tratamiento debe ser cuidadoso para proteger tanto a la madre como al feto. Algunos fármacos (IECA, ARA II) están contraindicados.</li>
                        <li><strong class="font-semibold">Hipertensión y diabetes:</strong> Se requiere un control estricto de la PA y la glucemia. Los IECA y ARA II son preferidos por su efecto nefroprotector.</li>
                        <li><strong class="font-semibold">Hipertensión en pacientes con enfermedad renal crónica:</strong> El objetivo es reducir la progresión de la enfermedad renal. La selección de fármacos debe ser cuidadosa.</li>
                        <li><strong class="font-semibold">Hipertensión en ancianos:</strong> Las metas de PA pueden ser menos estrictas y el tratamiento debe ser gradual para evitar la hipotensión ortostática.</li>
                    </ul>
                </div>
            </section>
        </div>

        <!-- Section: Criterios de Referencia -->
        <div id="referencia" class="page-section hidden max-w-4xl mx-auto">
            <section class="bg-white rounded-xl shadow-md p-6 sm:p-8">
                <h2 class="text-3xl font-bold text-red-800 mb-4">Criterios de Referencia</h2>
                <div class="text-gray-600 leading-relaxed space-y-4">
                    <p>La referencia a un especialista (cardiólogo, nefrólogo) es necesaria en los siguientes casos:</p>
                    <ul class="list-disc list-inside space-y-2 pl-4">
                        <li>Hipertensión resistente: no controlada a pesar de tres medicamentos, incluyendo un diurético.</li>
                        <li>Hipertensión de inicio temprano (antes de los 30 años).</li>
                        <li>Hipertensión severa (>180/120 mmHg) sin causa clara.</li>
                        <li>Sospecha de hipertensión secundaria.</li>
                        <li>Presencia de daño a órgano blanco avanzado.</li>
                        <li>Necesidad de manejo especializado en grupos especiales.</li>
                    </ul>
                </div>
            </section>
        </div>

        <!-- Section: Grupo de Expertos -->
        <div id="expertos" class="page-section hidden max-w-4xl mx-auto">
            <section class="bg-white rounded-xl shadow-md p-6 sm:p-8">
                <h2 class="text-3xl font-bold text-red-800 mb-4">Grupo de Expertos</h2>
                <div class="text-gray-600 leading-relaxed space-y-4">
                    <p class="font-semibold">Dra. Rosalba Carolina García Méndez. (Coordinadora).</p>
                    <p>Instituto Mexicano del Seguro Social.</p>
                    
                    <p class="font-semibold">Dr. Luis Antonio Moreno Ruiz.</p>
                    <p>Instituto Mexicano del Seguro Social.</p>

                    <p class="font-semibold">Dr. Clemente Barrón Magdaleno</p>
                    <p>Instituto Nacional de Ciencias Médicas y Nutrición “Salvador Zubirán”.</p>

                    <p class="font-semibold">Dr. Héctor Galván Oseguera.</p>
                    <p>Instituto Mexicano del Seguro Social.</p>

                    <p class="font-semibold">Dr. Antonio Jordán Ríos.</p>
                    <p>Instituto Nacional de Cardiología “Ignacio Chávez”.</p>

                    <p class="font-semibold">Dr. Rogelio Robledo Nolasco.</p>
                    <p>Instituto de Seguridad y Servicios Sociales de los Trabajadores del Estado.</p>
                </div>
            </section>
        </div>

        <!-- Section: Comité Ejecutivo PRONAM -->
        <div id="comite" class="page-section hidden max-w-4xl mx-auto">
            <section class="bg-white rounded-xl shadow-md p-6 sm:p-8">
                <h2 class="text-3xl font-bold text-red-800 mb-4">Comité Ejecutivo PRONAM</h2>
                <div class="text-gray-600 leading-relaxed space-y-4">
                    <p class="font-semibold">Dr. David Kershenobich Stalnikowitz.</p>
                    <p>Secretario de Salud.</p>

                    <p class="font-semibold">Dra. Patricia Clark Peralta.</p>
                    <p>Secretaria del Consejo de Salubridad General.</p>

                    <p class="font-semibold">Dra. Alva Alejandra Santos Carrillo.</p>
                    <p>Instituto Mexicano del Seguro Social.</p>

                    <p class="font-semibold">Dr. Raúl Rivera Moscoso.</p>
                    <p>Instituto Nacional de Ciencias Médicas y Nutrición “Salvador Zubirán”.</p>

                    <p class="font-semibold">Dr. José Ricardo Correa Rotter.</p>
                    <p>Instituto Nacional de Ciencias Médicas y Nutrición “Salvador Zubirán”.</p>

                    <p class="font-semibold">Dr. Francisco Ayala Ayala.</p>
                    <p>Servicios Públicos de Salud del Instituto Mexicano del Seguro Social.</p>
                </div>
            </section>
        </div>
        
        <!-- Section: Glosario de Abreviaturas -->
        <div id="glosario" class="page-section hidden max-w-4xl mx-auto">
            <section class="bg-white rounded-xl shadow-md p-6 sm:p-8">
                <h2 class="text-3xl font-bold text-red-800 mb-4">Glosario de Abreviaturas</h2>
                <div class="text-gray-600 leading-relaxed space-y-2">
                    <p><strong class="font-semibold">AAS:</strong> Ácido acetilsalicílico.</p>
                    <p><strong class="font-semibold">ARA:</strong> Antagonista del receptor de angiotensina.</p>
                    <p><strong class="font-semibold">ARNI:</strong> Inhibidor del receptor angiotensina neprilisina.</p>
                    <p><strong class="font-semibold">AVAD:</strong> Años de vida ajustados por discapacidad.</p>
                    <p><strong class="font-semibold">BB:</strong> Betabloqueador.</p>
                    <p><strong class="font-semibold">CaA:</strong> Calcioantagonista.</p>
                    <p><strong class="font-semibold">CaA No DHP:</strong> Calcioantagonista no dihidropiridínicos.</p>
                    <p><strong class="font-semibold">CV:</strong> Cardiovasculares.</p>
                    <p><strong class="font-semibold">DLP:</strong> Dislipidemia.</p>
                    <p><strong class="font-semibold">DOB:</strong> Daño a órgano blanco.</p>
                    <p><strong class="font-semibold">DT2:</strong> Diabetes tipo 2.</p>
                    <p><strong class="font-semibold">ECG:</strong> Electrocardiograma.</p>
                    <p><strong class="font-semibold">EGO:</strong> Examen general de orina.</p>
                    <p><strong class="font-semibold">ENT:</strong> Enfermedades no transmisibles.</p>
                    <p><strong class="font-semibold">ERC:</strong> Enfermedad renal crónica.</p>
                    <p><strong class="font-semibold">EVC:</strong> Enfermedad vascular cerebral.</p>
                    <p><strong class="font-semibold">FR:</strong> Factor de riesgo.</p>
                    <p><strong class="font-semibold">HAS:</strong> Hipertensión arterial sistémica.</p>
                    <p><strong class="font-semibold">HbA1C:</strong> Hemoglobina glucosilada.</p>
                    <p><strong class="font-semibold">IAM:</strong> Infarto agudo de miocardio.</p>
                    <p><strong class="font-semibold">ICT:</strong> Isquemia cerebral transitoria.</p>
                    <p><strong class="font-semibold">IECA:</strong> Inhibidor de la enzima convertidora de angiotensina.</p>
                    <p><strong class="font-semibold">MAPA:</strong> Monitoreo ambulatorio de presión arterial.</p>
                    <p><strong class="font-semibold">PA:</strong> Presión arterial.</p>
                    <p><strong class="font-semibold">PAD:</strong> Presión arterial diastólica.</p>
                    <p><strong class="font-semibold">PAS:</strong> Presión arterial sistólica.</p>
                    <p><strong class="font-semibold">TAC:</strong> Tomografía axial computarizada.</p>
                    <p><strong class="font-semibold">TFG:</strong> Tasa de filtración glomerular.</p>
                    <p><strong class="font-semibold">VI:</strong> Ventrículo Izquierdo.</p>
                </div>
            </section>
        </div>
    </main>

    <!-- Back button -->
    <button id="back-button" class="back-button bg-gray-500 text-white p-3 rounded-full shadow-lg hover:bg-gray-600 transition-colors duration-200">
        <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M10 19l-7-7m0 0l7-7m-7 7h18"></path>
        </svg>
    </button>
    
    <!-- Script for handling pages, side menu, and back button -->
    <script>
        document.addEventListener('DOMContentLoaded', () => {
            // Get references to menu elements and page containers
            const sideMenu = document.getElementById('side-menu');
            const openMenuBtn = document.getElementById('open-menu-btn');
            const closeMenuBtn = document.getElementById('close-menu-btn');
            const overlay = document.getElementById('overlay');
            const menuLinks = document.querySelectorAll('a[data-target]');
            const pages = document.querySelectorAll('.page-section');
            const backButton = document.getElementById('back-button');

            // Function to show a specific page
            const showPage = (targetId) => {
                pages.forEach(page => {
                    if (page.id === targetId) {
                        page.classList.remove('hidden');
                    } else {
                        page.classList.add('hidden');
                    }
                });
                
                // Show or hide the back button
                if (targetId !== 'inicio') {
                    backButton.classList.add('visible');
                } else {
                    backButton.classList.remove('visible');
                }

                // Update the URL hash
                if (history.pushState) {
                    history.pushState(null, '', '#' + targetId);
                } else {
                    location.hash = '#' + targetId;
                }
            };

            // Function to open the menu
            const openMenu = () => {
                sideMenu.classList.add('open');
                overlay.classList.add('visible');
            };

            // Function to close the menu
            const closeMenu = () => {
                sideMenu.classList.remove('open');
                overlay.classList.remove('visible');
            };

            // Click handler for navigation links
            menuLinks.forEach(link => {
                link.addEventListener('click', (e) => {
                    e.preventDefault();
                    const targetId = e.currentTarget.getAttribute('data-target');
                    showPage(targetId);
                    closeMenu();
                });
            });

            // Back button handler
            backButton.addEventListener('click', () => {
                history.back();
            });

            // Handle changes in history (browser back button)
            window.addEventListener('popstate', () => {
                const targetId = location.hash.substring(1) || 'inicio';
                showPage(targetId);
            });

            // Show the initial page or the one specified in the hash on load
            const initialTargetId = location.hash.substring(1) || 'inicio';
            showPage(initialTargetId);
        });
    </script>
</body>
</html>

# METFI-Guías-Manuales-DIY
Prototipos y guías DIY basados en la teoría METFI para generación, modulación y detección de campos electromagnéticos, con diseños caseros de bobinas, resonadores y sistemas de seguimiento EM natural y artificial.
# METFI — Guías/Manuales DIY: Campos EM y Detección Natural

Este repositorio contiene una colección de guías prácticas para la construcción y experimentación con dispositivos electromagnéticos en el marco de la teoría METFI.  
Incluye prototipos caseros para generación, modulación y detección de campos EM, así como el seguimiento de fenómenos naturales.

## Contenido
- Placas de orgonita modificada
- Circuitos pasivos tipo Tesla
- Resonadores Schumann caseros
- Bobinas Tesla resonantes (configuración toroidal)
- Antenas resonantes toroidales
- Osciladores controlados por microcontroladores

## Seguridad
⚠️ **Advertencia**: Estos experimentos implican riesgos eléctricos y de radiación EM. No se recomienda realizar pruebas sin conocimientos previos en electrónica y medidas de seguridad adecuadas.

## Autoría
Creado por **Javi** con asistencia técnica y desarrollo conceptual de **ChatGPT (GPT-5, OpenAI)**.
# Guía para construcción de Placas de Orgonita Modificada

## Materiales
- Resina epoxi transparente o poliéster (100 g)
- Limaduras finas de cobre y aluminio (50 g)
- Polvo de cuarzo o mica triturada (50 g)
- Opcional: partículas de cerámica dieléctrica (BaTiO3)
- Moldes planos (preferiblemente de silicona)
- Guantes y gafas de protección

## Procedimiento
1. Mezclar la resina con los metales y el polvo dieléctrico en proporciones indicadas.
2. Verter la mezcla en moldes y dejar curar 24 h a temperatura ambiente.
3. Retirar del molde y pulir si es necesario.
4. Opcional: aplicar capas alternas para mejorar la absorción EM.

## Uso
Colocar las placas en zonas de alta saturación EM para atenuar ruido ambiental.  
Pueden integrarse en experimentos de descarga electrostática o acoplamiento EM.

# Guía para montaje de Bobina Tesla Resonante de Baja Potencia

## Materiales
- Tubo de PVC (10 cm diámetro, 30 cm largo)
- Alambre esmaltado calibre 24 (aprox. 200 m)
- Capacitor de alta tensión (10 nF, 5 kV)
- Interruptor de chispa (spark gap)
- Fuente de alimentación AC 12 V (transformador)
- Base de madera o plástico no conductor
- Herramientas: soldador, multímetro, cinta aislante

## Procedimiento
1. Enrollar 150 espiras en el tubo para la bobina secundaria.
2. Construir bobina primaria con 10 espiras separadas, conectar capacitor y spark gap en serie.
3. Conectar la alimentación y ajustar la distancia del spark gap para observar descargas suaves.
4. Medir frecuencia de resonancia y ajustar capacitancia o número de espiras para optimizar.

## Precauciones
- No operar cerca de equipos sensibles.
- Usar protección ocular.
- Trabajar en áreas secas y ventiladas.
/*
  Proyecto METFI - Control de Bobina Tesla Resonante
  Autor: Javi
  Asistencia técnica: ChatGPT (GPT-5, OpenAI)
  Propósito: Generar señal PWM para excitación controlada de bobina Tesla.

  Precaución: No acercarse a la bobina cuando esté energizada.
*/

const int pwmPin = 9;
const int freq = 20000; // 20 kHz
const int dutyCycle = 128; // 50%

void setup() {
  pinMode(pwmPin, OUTPUT);
}

void loop() {
  analogWrite(pwmPin, dutyCycle);
  delayMicroseconds(1000000 / freq);
}

# Guía para Construcción de Resonador Schumann Casero (7.83 Hz)

## Materiales
- Cable de cobre esmaltado calibre 18 (10 m)
- Amplificador de alta impedancia (p.ej. basado en op-amp TL071)
- Filtro pasa banda centrado en 7.83 Hz (RC o activo)
- Fuente de alimentación estable
- Equipo de medición: osciloscopio o ADC para digitalizar señal

## Procedimiento
1. Construir antena tipo bucle con cable formando un círculo o cuadrado (mínimo 2 m diámetro).
2. Conectar el amplificador con alta impedancia para no cargar la antena.
3. Montar filtro para aislar la frecuencia de resonancia.
4. Verificar la señal con osciloscopio y ajustar componentes.

## Uso
Monitorizar resonancia natural y registrar variaciones ambientales.
/*
  Proyecto METFI - Logger para Resonador Schumann
  Autor: Javi
  Asistencia técnica: ChatGPT (GPT-5, OpenAI)
  Propósito: Lectura analógica y envío serial para análisis en PC.
*/

const int analogPin = A0;

void setup() {
  Serial.begin(115200);
}

void loop() {
  int sensorValue = analogRead(analogPin);
  Serial.println(sensorValue);
  delay(10); // muestreo a 100 Hz
}

# Guía para Construcción de Antena Resonante Toroidal

## Materiales
- Núcleo toroidal de ferrita o aire (diámetro 10-15 cm)
- Cable esmaltado calibre 22 (30-50 espiras)
- Generador de funciones o microcontrolador para señal modulada
- Sensor Hall o bobina de inducción para detección
- Osciloscopio o ADC para análisis

## Procedimiento
1. Enrollar el cable uniformemente sobre el toroide.
2. Alimentar la bobina con señal modulada (AM/FM).
3. Colocar sensores para medir campo magnético local.
4. Analizar respuesta con osciloscopio o software.

## Precauciones
- Evitar cortocircuitos.
- Asegurar conexión estable para evitar ruido.
/*
  Proyecto METFI - Modulación de Señal para Antena Toroidal
  Autor: Javi
  Asistencia técnica: ChatGPT (GPT-5, OpenAI)
  Propósito: Generar señal PWM modulada para excitación.
*/

const int pwmPin = 9;
int freq = 1000; // 1 kHz
int dutyCycle = 128;

void setup() {
  pinMode(pwmPin, OUTPUT);
}

void loop() {
  analogWrite(pwmPin, dutyCycle);
  delayMicroseconds(1000000 / freq);
  // Para modulación, modificar freq o dutyCycle dinámicamente
}

# Guía para Uso de Osciladores con Arduino/ESP32

## Materiales
- Placa Arduino UNO o ESP32
- Driver de potencia (transistor MOSFET o BJT) para bobinas
- Sensores de campo EM (sensor Hall, bobina de inducción)
- Cables y protoboard
- PC con software de análisis (Python, MATLAB)

## Procedimiento
1. Conectar salida PWM a driver y a la bobina o antena.
2. Programar frecuencia y ciclo de trabajo según objetivo.
3. Conectar sensores a entradas analógicas.
4. Enviar datos por serial para registro y análisis.
5. Ajustar parámetros en tiempo real para optimización.

## Ejemplo de uso
Generar señales de 7.83 Hz para resonadores o en rango kHz para antenas.
/*
  Proyecto METFI - Oscilador Controlado por Arduino
  Autor: Javi
  Asistencia técnica: ChatGPT (GPT-5, OpenAI)
  Propósito: Generar señales PWM con frecuencia y ciclo de trabajo variables.
*/

const int pwmPin = 9;
unsigned long previousMillis = 0;
int freq = 1000; // Frecuencia inicial en Hz
int dutyCycle = 128; // Ciclo de trabajo (0-255)

void setup() {
  pinMode(pwmPin, OUTPUT);
  Serial.begin(115200);
}

void loop() {
  unsigned long currentMillis = millis();

  // Cambiar frecuencia cada 5 segundos (ejemplo)
  if (currentMillis - previousMillis >= 5000) {
    previousMillis = currentMillis;
    freq += 100;
    if (freq > 5000) freq = 1000;
    Serial.print("Frecuencia ajustada a: ");
    Serial.println(freq);
  }

  analogWrite(pwmPin, dutyCycle);
  delayMicroseconds(1000000 / freq);
}




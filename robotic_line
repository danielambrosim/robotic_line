// ROBÔ SEGUIDOR DE LINHA - 5 SENSORES
// Autor: Daniel + ChatGPT
// Ajuste os pinos conforme a montagem do seu robô

// Sensores de linha
#define S1 A0  // Esquerda extrema
#define S2 A1  // Esquerda
#define S3 A2  // Centro
#define S4 A3  // Direita
#define S5 A4  // Direita extrema

// Motor esquerdo
#define ENA 5
#define IN1 6
#define IN2 7

// Motor direito
#define ENB 10
#define IN3 8
#define IN4 9

int velocidadeBase = 120;
int velocidadeCurva = 90;
int velocidadeForte = 150;

// Se o sensor detectar preto como 0, deixe true.
// Se detectar preto como 1, troque para false.
bool linhaPretaComoZero = true;

void setup() {
  pinMode(S1, INPUT);
  pinMode(S2, INPUT);
  pinMode(S3, INPUT);
  pinMode(S4, INPUT);
  pinMode(S5, INPUT);

  pinMode(ENA, OUTPUT);
  pinMode(IN1, OUTPUT);
  pinMode(IN2, OUTPUT);

  pinMode(ENB, OUTPUT);
  pinMode(IN3, OUTPUT);
  pinMode(IN4, OUTPUT);

  Serial.begin(9600);
}

void loop() {
  int s1 = lerSensor(S1);
  int s2 = lerSensor(S2);
  int s3 = lerSensor(S3);
  int s4 = lerSensor(S4);
  int s5 = lerSensor(S5);

  Serial.print(s1);
  Serial.print(" ");
  Serial.print(s2);
  Serial.print(" ");
  Serial.print(s3);
  Serial.print(" ");
  Serial.print(s4);
  Serial.print(" ");
  Serial.println(s5);

  // Linha no centro
  if (s3 == 1 && s2 == 0 && s4 == 0) {
    frente(velocidadeBase, velocidadeBase);
  }

  // Leve curva para esquerda
  else if (s2 == 1 || (s2 == 1 && s3 == 1)) {
    frente(velocidadeCurva, velocidadeForte);
  }

  // Leve curva para direita
  else if (s4 == 1 || (s4 == 1 && s3 == 1)) {
    frente(velocidadeForte, velocidadeCurva);
  }

  // Curva forte para esquerda
  else if (s1 == 1) {
    esquerdaForte();
  }

  // Curva forte para direita
  else if (s5 == 1) {
    direitaForte();
  }

  // Cruzamento ou linha larga
  else if (s1 == 1 && s2 == 1 && s3 == 1 && s4 == 1 && s5 == 1) {
    frente(velocidadeBase, velocidadeBase);
  }

  // Perdeu a linha
  else {
    parar();
  }
}

int lerSensor(int pino) {
  int leitura = digitalRead(pino);

  if (linhaPretaComoZero) {
    return leitura == 0 ? 1 : 0;
  } else {
    return leitura == 1 ? 1 : 0;
  }
}

void frente(int velEsq, int velDir) {
  digitalWrite(IN1, HIGH);
  digitalWrite(IN2, LOW);

  digitalWrite(IN3, HIGH);
  digitalWrite(IN4, LOW);

  analogWrite(ENA, velEsq);
  analogWrite(ENB, velDir);
}

void esquerdaForte() {
  digitalWrite(IN1, LOW);
  digitalWrite(IN2, HIGH);

  digitalWrite(IN3, HIGH);
  digitalWrite(IN4, LOW);

  analogWrite(ENA, velocidadeCurva);
  analogWrite(ENB, velocidadeForte);
}

void direitaForte() {
  digitalWrite(IN1, HIGH);
  digitalWrite(IN2, LOW);

  digitalWrite(IN3, LOW);
  digitalWrite(IN4, HIGH);

  analogWrite(ENA, velocidadeForte);
  analogWrite(ENB, velocidadeCurva);
}

void parar() {
  analogWrite(ENA, 0);
  analogWrite(ENB, 0);
}

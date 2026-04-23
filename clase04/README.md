## en esta clase, se presenta un sketch hecho en processing con datos propios recogidos. Incluyo estos datos en un archivo .csv en mi github ##

``` int[][] datos = {
{3,2,4,3,2,1,2}, // Martina
{2,3,2,4,3,2,1}, // Estefanny
{4,2,3,2,4,2,3}, // Ardillita
{1,1,2,1,2,1,1}, // Martina2
{3,4,3,2,3,2,4}, // Blancanieves
{0,0,0,0,0,0,0}, // Toto
{0,0,0,0,0,0,0} // Gloton
};

float t = 0;

void setup() {
size(800, 600);
noStroke();
}

void draw() {
background(180);

float y = 80;

for (int f = 0; f < datos.length; f++) {

float x = 100;

for (int c = 0; c < datos[f].length; c++) {

int valor = datos[f][c];

// 🎨 COLOR
if (valor == 1) fill(120, 80, 50);
else if (valor == 2) fill(255);
else if (valor == 3) fill(150);
else if (valor == 4) fill(180, 80, 20);
else fill(200, 60); // casi invisible

// 💥 MOVIMIENTO SEGÚN DATO
float intensidad = valor * 2; // más huevos = más movimiento

float movX = sin(t + f + c) * intensidad;
float movY = cos(t + c) * intensidad;

// 🌊 DEFORMACIÓN SEGÚN DATO
float deform = valor * 5;

dibujarBlob(
x + movX,
y + movY,
valor * 10,
deform,
t + f + c
);

x += 90;
}

y += 80;
}

t += 0.03;
}


// 🧬 FORMA ORGÁNICA CONTROLADA POR DATOS
void dibujarBlob(float x, float y, float tamaño, float deform, float offset) {

beginShape();

for (int i = 0; i < 16; i++) {

float ang = TWO_PI / 16 * i;

// ruido depende del valor
float ruido = noise(i * 0.2, offset) * deform;

float r = tamaño + ruido;

float px = x + cos(ang) * r;
float py = y + sin(ang) * r;

curveVertex(px, py); ```
}

endShape(CLOSE);
}

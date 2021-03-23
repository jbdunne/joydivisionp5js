var particles = [];
// amount of particles per row
var pPerRow = 15;
var cIndex = 150;
var noiseScale = 500;

function setup() {
  colors = [
    color(150, 150, 150, 150),
  ];

  createCanvas(
    window.innerWidth,
    window.innerHeight
  );
  background(0,0,0);

  seedParticles();
}

function draw() {
  particles.forEach(function(particle) {
    particle.move();
    particle.render();
  });
}

function seedParticles() {
  var wInterval = width / pPerRow;
  var hInterval = height / pPerRow;
  var paddingH = height * 3.80;

  for (var i = 0; i <= width; i+= wInterval) {
    for (var j = 0; j <= height; j += hInterval) {

      var c = Math.round(
        cIndex % colors.length
      );
      cIndex++;
      var particle = new Particle(
        // add guassian to randomly disperse starting points
        i + randomGaussian(-30, 40),
        j + randomGaussian(-30, 40),
        c
      );
      particles.push(particle);
    }
  }
}

function Particle(x, y, colorIndex) {
  this.position = createVector(x, y);
  this.color = colorIndex;

  this.move = function() {
    var angleNoise = noise(
      noise(this.position.x / noiseScale, this.position.y / noiseScale) * 10,
      noise(frameCount * noise(frameCount), frameCount / noise(frameCount)) * 0.03
    ) * noiseScale;

    var density = 1;

    this.position.x += cos(cos(angleNoise)) * (1.5 + (noise(frameCount))) * density;
    this.position.y += sin(sin(angleNoise)) * (1.5 + (noise(frameCount))) * density;
  }

  this.render = function() {
    stroke(colors[this.color]);
    point(
      this.position.x,
      this.position.y
    );
  }
}

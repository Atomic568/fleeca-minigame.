const shapeTypes = ['circle', 'square', 'triangle', 'hexagon', 'star'];
const pattern = [];
const selected = [];

function getRandomShape() {
  return shapeTypes[Math.floor(Math.random() * shapeTypes.length)];
}

function createGrid() {
  const grid = document.getElementById('grid');
  grid.innerHTML = '';
  for (let i = 0; i < 72; i++) {
    const shapeType = getRandomShape();
    const div = createShape(shapeType);
    div.onclick = () => selectShape(shapeType, div);
    grid.appendChild(div);
  }
}

function createShape(type) {
  const div = document.createElement('div');
  div.classList.add('shape', type);
  if (type === 'star') div.innerHTML = '★';
  return div;
}

function createPattern() {
  const patternDiv = document.getElementById('pattern');
  patternDiv.innerHTML = '';
  pattern.length = 0;
  for (let i = 0; i < 9; i++) {
    const shapeType = getRandomShape();
    pattern.push(shapeType);
    patternDiv.appendChild(createShape(shapeType));
  }
}

function selectShape(type, div) {
  if (div.classList.contains('selected')) return;

  if (selected.length < 9) {
    div.classList.add('selected');
    selected.push(type);
    updateSelected();
  }
}

function updateSelected() {
  const selDiv = document.getElementById('selected');
  selDiv.innerHTML = '';
  selected.forEach(type => {
    selDiv.appendChild(createShape(type));
  });
}

function checkPattern() {
  const result = document.getElementById('result');
  if (selected.length < 9) {
    result.textContent = 'Select 9 shapes!';
    return;
  }
  const match = selected.every((s, i) => s === pattern[i]);
  result.textContent = match ? '✅ Correct!' : '❌ Incorrect, try again!';
}

createGrid();
createPattern();

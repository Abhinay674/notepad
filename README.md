// Set up the scene, camera, and renderer
const scene = new THREE.Scene();
const camera = new THREE.PerspectiveCamera(75, window.innerWidth / window.innerHeight, 0.1, 1000);
const renderer = new THREE.WebGLRenderer();
renderer.setSize(window.innerWidth, window.innerHeight);
document.body.appendChild(renderer.domElement);

// Create objects in the scene
const geometry = new THREE.BoxGeometry(1, 1, 1);
const material = new THREE.MeshBasicMaterial({ color: 0x00ff00 });
const cube1 = new THREE.Mesh(geometry, material);
cube1.position.set(-2, 0, 0);
scene.add(cube1);

const cube2 = new THREE.Mesh(geometry, material);
cube2.position.set(2, 0, 0);
scene.add(cube2);

// Create a raycaster
const raycaster = new THREE.Raycaster();
const mouse = new THREE.Vector2();

// Selected object variable
let selectedObject = null;

// Handle mouse move event
function onMouseMove(event) {
  // Calculate normalized device coordinates
  mouse.x = (event.clientX / window.innerWidth) * 2 - 1;
  mouse.y = -(event.clientY / window.innerHeight) * 2 + 1;
}

// Handle mouse click event
function onMouseClick(event) {
  // Update the raycaster with the mouse coordinates
  raycaster.setFromCamera(mouse, camera);

  // Perform raycasting
  const intersects = raycaster.intersectObjects(scene.children);

  // Check if there are any intersections
  if (intersects.length > 0) {
    // Get the first intersected object
    selectedObject = intersects[0].object;
  } else {
    // If no intersection, reset selected object
    selectedObject = null;
  }
}

// Remove selected object
function removeSelectedObject() {
  if (selectedObject) {
    scene.remove(selectedObject);
    selectedObject = null;
  }
}

// Attach event listeners
window.addEventListener('mousemove', onMouseMove, false);
window.addEventListener('click', onMouseClick, false);

// Create delete button
const deleteButton = document.createElement('button');
deleteButton.innerText = 'Delete Selected Object';
deleteButton.addEventListener('click', removeSelectedObject);
document.body.appendChild(deleteButton);

// Update the camera position
camera.position.z = 5;

// Render the scene
function animate() {
  requestAnimationFrame(animate);
  renderer.render(scene, camera);
}
animate();

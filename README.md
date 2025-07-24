/**
* You work in an automated factory and your objective is to write the function that will dispatch the packages to the correct stack,
* according to their volume and mass.
* <p>
* - A package is <b>bulky</b> if its volume (Width x Height x Length) is greater than or equal to 1,000,000 cm³ or when one of
* its dimension is greater or equal than 150 cm.
* - A package is <b>heavy</b> when its mass is greater or equal than 20 kg.
* <p>
* You must dispatch the packages in the following stacks.
* - STANDARD: standard packages (those which are not bulky nor heavy) can be handled normally.
* - SPECIAL: packages that are either heavy or bulky can't be handled automatically.
* - REJECTED: packages that are <b>both</b> heavy and bulky are rejected.
* <p>
* Implementation
* <p>
* Implement the function <code>solve(width, height, length, mass)</code> (units are centimeter for the dimensions and kilogram for the mass). 
* This function must return a string: the name of the stack where the package should go.
*/
function solve(width: number, height: number, length: number, mass: number): string {
  const volume = width * height * length;
  const isHeavy = width >= 150 || height >= 150 || length >= 150;
  
  if (mass < 20 && (isHeavy || volume >= 1000000)) {
    return 'SPECIAL';
  } else if (mass >= 20) {
    if (volume >= 1000000 || isHeavy) {
      return 'REJECTED';
    }
    
    return 'SPECIAL';
  }
  
  return 'STANDARD';
}

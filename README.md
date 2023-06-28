const jsonArr = [
  {
    "key": "default",
    "paths": [
      "/v1/visicaptcha",
      "/v1/visicaptcha1",
      "/v1/visicaptcha3",
      "/v1/visicaptcha5"
    ]
  },
  {
    "key": "visible-test-v2-02-checkbox",
    "paths": [
      "/v1/visicaptcha2",
      "/v1/visicaptcha3"
    ]
  },
  {
    "key": "visible-test-v3-02-checkbox",
    "paths": [
      "/v1/visicaptcha4",
      "/v1/visicaptcha5"
    ]
  }
];

const searchString = "/v1/visicaptcha";
let foundKey = null;

for (let i = 0; i < jsonArr.length; i++) {
  const obj = jsonArr[i];
  const pathsArray = Array.from(obj.paths); // Convert paths property to an array
  let searchStringFound = false;
  for (let j = 0; j < pathsArray.length; j++) {
    if (pathsArray[j] === searchString) {
      searchStringFound = true;
      break;
    }
  }
  if (searchStringFound) {
    if (obj.key !== "default") {
      let otherKeyPresent = false;
      for (let k = 0; k < jsonArr.length; k++) {
        if (k !== i) {
          const otherPathsArray = Array.from(jsonArr[k].paths);
          if (otherPathsArray.includes(searchString)) {
            otherKeyPresent = true;
            break;
          }
        }
      }
      if (otherKeyPresent) {
        foundKey = obj.key;
        break;
      }
    } else {
      foundKey = obj.key;
    }
  }
}

console.log("Found key:", foundKey);












const jsonArr = [
  {
    "key": "default",
    "paths": [
      "/v1/visicaptcha",
      "/v1/visicaptcha1",
      "/v1/visicaptcha3",
      "/v1/visicaptcha5"
    ]
  },
  {
    "key": "visible-test-v2-02-checkbox",
    "paths": [
      "/v1/visicaptcha2",
      "/v1/visicaptcha3"
    ]
  },
  {
    "key": "visible-test-v3-02-checkbox",
    "paths": [
      "/v1/visicaptcha4",
      "/v1/visicaptcha5"
    ]
  }
];

const searchString = "/v1/visicaptcha";
let foundKey = null;

// Loop through each object in the jsonArr array
for (let i = 0; i < jsonArr.length; i++) {
  const obj = jsonArr[i];
  const pathsArray = Array.from(obj.paths); // Convert paths property to an array using Array.from()

  // Check if the searchString is present in the pathsArray
  let searchStringFound = false;
  for (let j = 0; j < pathsArray.length; j++) {
    if (pathsArray[j] === searchString) {
      searchStringFound = true;
      break;
    }
  }

  // If the searchString is found in the pathsArray
  if (searchStringFound) {
    // Check if the key is not "default"
    if (obj.key !== "default") {
      let otherKeyPresent = false;

      // Loop through the jsonArr array again to check other objects' paths arrays
      for (let k = 0; k < jsonArr.length; k++) {
        if (k !== i) {
          const otherPathsArray = Array.from(jsonArr[k].paths);

          // Check if the searchString is present in other objects' paths arrays
          if (otherPathsArray.includes(searchString)) {
            otherKeyPresent = true;
            break;
          }
        }
      }

      // If the searchString is found in other keys' paths arrays, assign the current key to foundKey
      if (otherKeyPresent) {
        foundKey = obj.key;
        break;
      }
    } else {
      // If the key is "default" and the searchString is found, assign "default" to foundKey
      foundKey = obj.key;
    }
  }
}

console.log("Found key:", foundKey);


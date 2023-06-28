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
  const pathsArray = obj.paths; // Assign the paths array directly

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
          const otherPathsArray = jsonArr[k].paths;
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

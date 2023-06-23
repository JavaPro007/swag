const searchString = "/v1/visicaptcha";
let foundKey = null;

for (let i = 0; i < jsonArr.length; i++) {
  const obj = jsonArr[i];
  if (obj.paths.includes(searchString)) {
    if (obj.key !== "default") {
      let otherKeyPresent = false;
      for (let j = 0; j < jsonArr.length; j++) {
        if (j !== i && jsonArr[j].paths.includes(searchString)) {
          otherKeyPresent = true;
          break;
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

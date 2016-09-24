# DynamicConstructor

function DynamicConstructor(obj) {
	for (var attr in obj) {
		if (typeof obj[attr] == "object") {
			this[attr] = new DynamicConstructor(obj[attr]);
		} else {
			this[attr] = obj[attr];
		}
	}
};




function DynamicConstructor(obj) {
  var dc = this;
  for (var attr in obj) { 
    if (typeof obj[attr] == "object") {
      if (Array.isArray(obj[attr])) {
        for (var element in obj[attr]) {
          if (typeof element == "object") {
            if (Array.isArray(element)) {
              element.push(new DynamicConstructor(element));
            } else {
              element = new DynamicConstructor(element);
            }
          } else {
            element.push(element);
          }
        } 
      } else {
        this[attr] = new DynamicConstructor(obj[attr]);
      } 
    } else { 
      this[attr] = obj[attr]; 
    } 
  } 
};

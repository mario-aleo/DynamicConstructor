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

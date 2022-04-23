# Class

2022-01-27

<br />
Why?
---

- Interface는 타입으로만 사용 가능하지만, 클래스로 선언하면 타입과 값으로 모두 사용할 수 있으므로 오류가 없다.

<br />
How?
---

```
class Square {
	constructor(width:number)
}

class Rectangle extends Square {

	constructor(width:number,height:number) {
		super(width);
	}
}

type Shape = Square | Rectangle;

function calculateArea(shape:Shape) {
	if(shape instanceof Rectangle) {
		shape; // Rectangle
		return shape.width * shape.height;
	} else {
		shape; // Square
		return shpae.width * shape.width;
	}
}
```
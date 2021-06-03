### Project 6

In this project, we used Promises, fetch, and node-fetch to analyze shapes

## Source Code 

    /*
    Grant Nelson
    P6
    5-19-21
    */

    class Shape {
        constructor(sides = []) { 
            this.sides = sides
        }

        perimeter = () => this.sides.length > 0 ? this.sides.reduce((a, c) => a + c): 0;
    }

    //console.log(new Shape([5, 10]).perimeter());  // 15
    //console.log(new Shape([1, 2, 3, 4, 5]).perimeter()); // 15
    //console.log(new Shape().perimeter()); // 0

    class Rectangle extends Shape {
        constructor(length = 0, width = 0) {
            super([length, width, length, width]);
            this.length = length;
            this.width = width;
        }

        area = () => this.length * this.width;
    }

    //console.log(new Rectangle(4, 4).perimeter());  // 16
    //console.log(new Rectangle(4, 4).area());  // 16
    //console.log(new Rectangle(5, 5).perimeter()); // 20
    //console.log(new Rectangle(5, 5).area()); // 25
    //console.log(new Rectangle().perimeter()); // 0
    //console.log(new Rectangle().area()); // 0

    class Triangle extends Shape {
        constructor(sideA = 0, sideB = 0, sideC = 0) {
            super([sideA, sideB, sideC]);
            this.sideA = sideA;
            this.sideB = sideB;
            this.sideC = sideC;
        }
        area() {
            const s = this.perimeter() / 2;
            let tArea = Math.sqrt(s * (s - this.sideA) * (s - this.sideB) * (s - this.sideC));
            return tArea;
        }
    } 

    //console.log(new Triangle(3, 4, 5).perimeter());  // 12
    //console.log(new Triangle(3, 4, 5).area());  // 6
    //console.log(new Triangle().perimeter()); // 0
    //console.log(new Triangle().area()); // 0

    // Array of sides arrays
    const data = [ [3, 4], [5, 5], [3, 4, 5], [10], [] ];

    function plural(a) {
        let multiple = "s"
      if (a < 1) {
        return multiple;
      }
      else if (a = 1) {
          return "";
      }
    }

    for (numSides of data) {

      let shapeObj = null;
      let area = 0;
      let perimeter = 0;

      switch (numSides.length) {

        case 2:
            shapeObj = new Rectangle(...numSides);
            perimeter = shapeObj.perimeter();
            area = shapeObj.area();
            console.log(`Rectangle with sides ${numSides} has perimeter of ${perimeter} and area of ${area}`);

            break;

        case 3:
            shapeObj = new Triangle(...numSides);
            perimeter = shapeObj.perimeter();
            area = new Triangle(...numSides).area();
            console.log(`Triangle with sides ${numSides} has perimeter of ${perimeter} and area of ${area}`);
            break;

        default:
            console.log(`Shape with ${numSides.length} side${plural(numSides.length)} unsupported`);
            break;
      }
    }

    //console.log(plural("0"));
    //console.log(plural("1"));

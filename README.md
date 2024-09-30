# estudio-javascript 
## LABORATORIO 1 DEL MODULO 3 -- PROGRAMACION FUNCIONAL

# Task 1: Build a function-based console log message generator-- generador de mensajes
function consoleStyler(color, background, fontSize, txt) {
    let message = "%c" + txt;
    let style = `color: ${color};`
    style += `background: ${background};`
    style += `font-size: ${fontSize};`
    
   console.log(message, style);
}
consoleStyler(`red`, `yellow`, `24px`, `style message`);
   
# Task 2: Build another console log message generator
function celebrateStyler(reason) {
 
   let fontStyle = "color: tomato; font-size: 50px";
    if (reason == "birthday") {
       console.log(`%cHappy birthday`, fontStyle);
    } else if (reason == "champions") {
        console.log(`%cCongrats on the title!`, fontStyle);
    } else {
        console.log(`%cCelebrate!`,fontStyle);
   }

}

celebrateStyler("birthday");
celebrateStyler("champions");
celebrateStyler("Celebrate!");

# Task 3: Run both the consoleStyler and the celebrateStyler functions
consoleStyler('#1d5c63','#ede6db','40px','Congrats!');

consoleStyler('#1d5c63','#ede6db','40px','birthday');

# Task 4: Insert a congratulatory and custom message
function styleAndCelebrate(color,background,fontSize,txt,reason) {
     consoleStyler(color, background, fontSize, txt);
     celebrateStyler(reason);
}
 styleAndCelebrate('ef7c8e','fae8e0','30px','¡Lo lograste!',
'campeones');


## LABORATORIO 2 MODULO 3 PROGRAMACION ORIENTADA A OBJETOS

class Person {
  constructor(name = "Tom", age = 20, energy = 100) {
    this.name = name;
    this.age = age;
    this.energy = energy;
  }

  sleep() {
    this.energy += 10;
  }

  doSomethingFun() {
    this.energy -= 10;
  }
}

class Worker extends Person {
  constructor(name, age, energy, xp = 0, hourlyWage = 10) {
    super(name, age, energy);
    this.xp = xp;
    this.hourlyWage = hourlyWage;
  }

  goToWork() {
    this.xp += 10;
  }
}

function intern() {
  let intern = new Worker("Bob", 21, 110, 0, 10);
  intern.goToWork();
  return intern;
}

function manager() {
  let manager = new Worker("Alice", 30, 120, 100, 30);
  
  manager.doSomethingFun();
  return manager;
}

## LABORATORIO 3 MODULO 3 -- ITERAR SOBRE UNA MATRIZ

// Task 1
var dairy = ['cheese', 'sour cream', 'milk', 'yogurt', 'ice cream', 'milkshake']

function logDairy() {
    for (prop of dairy) {
        console.log(prop);
    }
}
logDairy(); 

// Task 2
console.log("// Task 2");
const animal = {

canJump: true

};

const bird = Object.create(animal);

bird.canFly = true;

bird.hasFeathers = true;

function birdCan() {
    for (prop of Object.keys(bird)){
         console.log(prop+": "+bird[prop])
 
    }
}
birdCan();
// Task 3
console.log("//n Task 3");



function animalCan() {
    for (prop in (bird)) {
        console.log(prop+": "+bird[prop]);
    }
}

animalCan();

### LABORATORIO  DE MODULO 4 -- PRUEBA UNITARIAS O TEST JEST

## Jest es el framework de pruebas unitarias más popular en JavaScript

# archivo js numero 1 - nombre de archivo - timesTwo.js
# Task 1: Code the timesTwo function declaration// declaracion de la funcion
function timesTwo(a) {
    return a * 2;
}
module.exports = timesTwo;

# archivo de js numero 2 - nombre de archivo - package.json
 
{
  "name": "jest-testing",
  "version": "1.0.0",
  "description": "",
  "main": "timesTwo.js",
  "scripts": {
    "test": "jest"
  },
  "author": "",
  "license": "ISC"
}
# archivo de js numero 3 - nombre del archivo - timesTwo.test.js

const { default: TestRunner } = require("jest-runner");
const timesTwo = require('./timesTwo');

test('returns the number 20', () => {
    expect(timesTwo(10)).toBe(20);
})


## LABOTORIO DE MODULO 5
# factura lenon de platos
# Given variables
const dishData = [
    {
        name: "Italian pasta",
        price: 9.55
    },
    {
        name: "Rice with veggies",
        price: 8.65
    },
    {
        name: "Chicken with potatoes",
        price: 15.55
    },
    {
        name: "Vegetarian Pizza",
        price: 6.45
    },
]
const tax = 1.20;


# Implement getPrices()
function getPrices(taxBoolean) {
   
    for ( prop of dishData) {
        var finalPrice;
        if (taxBoolean == true) {
            finalPrice = prop.price * tax;
        
            
        } else if (taxBoolean == false) {
            finalPrice = prop.price;
        
        } else {
            console.log("You need to pass a boolean to the getPrices call!");
            return;// o break
                
        }
            
    
    
        console.log(`Dish: ${prop.name}`, `Price: $${finalPrice}`);
       
    } 

}
  
    


# Implement getDiscount()
    function getDiscount(taxBoolean, guests) {
        getPrices(taxBoolean);

          
    
        if (typeof guests == 'number' && guests > 0 && guests < 30) {
            var discount = 0;

            if ( guests < 5) {
                discount = 5;
            } else if (guests >= 5) {
                discount = 10;

            }
            if (typeof taxBoolean == 'boolean') {
                console.log(`Discount is: $${discount}`);
            }
        }
        else {
           console.log('The second argument must be a number between 0 and 30');
        }

  // console.log("\n");
    
    }



getDiscount(true, 2);
getDiscount(false, 10);


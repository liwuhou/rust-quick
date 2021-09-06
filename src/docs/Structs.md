# 数据结构

-   used to group multiple related items of mixed data types
-   elements are named (unlike tuples where they are ordered)
-   two kinds of structs (regular struct and tuple struct)

```rust
// tuple struct// used to store a collection of mixed data without named fields
// used to be distinguished as a specific type
// (not just a regular tuple)struct Signal(u8, bool, String);
// regular struct// struct names are capitalized
// like classes in JavaScript and OOP generallystruct Car {
    // fields of the struct
    model: String,
    year: String,
    used: bool,
}// method: functions/subroutines associated to a struct
// methods are defined within the context of a struct
// the first parameter of a method is the reference to a struct instanceimpl Car {
    // construct car
    fn new(m: &str, y: &str) -> Car {
        Car {
            model: m.to_string(),
            year: y.to_string(),
            used: false,
        }
    } // self is equivalent to "this" is JavaScript
    fn serialize(&self) -> String {
        format!(
            "model: {} - year: {} - used: {}",
            self.model, self.year, self.used
        )
    } // mutate state
    fn marked_used(&mut self) {
        self.used = true;
    }
}struct Position {
  latitude: f64,
  longitude: f64
}fn print_signal(s: &Signal) {
    println!("s1 is {}, {}, {}", s.0, s.1, s.2);
}fn main() {
    let mut pos_1 = Position {
        latitude: 27.299112,
        longitude: 95.387110,
    }; println!(
      "pos_1 is {:.3}, {:.3}",
      pos_1.latitude,
      pos_1.longitude
    ); pos_1.latitude = 23.1111;
    println!(
      "pos_1 is now {:.3}, {:.3}",
      pos_1.latitude,
      pos_1.longitude
    ); let mut s1 = Signal(0, true, String::from("ok")); // fields of a tuple struct are accessed like regular tuples values
    // using their index
    // remember tuple structs do not have named fields print_signal(&s1); s1.0 = 23;
    s1.1 = false;
    s1.2 = String::from("NETERR"); println!("s1 is now {}, {}, {}", s1.0, s1.1, s1.2); let car_1 = Car::new("QBC", "2133");
    println!("car_1 is a {} of {}", car_1.model, car_1.year); let is_used = if car_1.used == true {
        "used"
    } else {
        "brand new"
    };
    println!("car_1 is {}", is_used);
    println!("car_1 is {}", car_1.serialize()); let mut car_2 = Car::new("ZZ7", "2042");
    println!("car_2 is a {}", car_2.serialize()); car_2.marked_used();
    println!("car_2 is now {}", car_2.serialize());
}
```

Output
```
pos_1 is 27.299, 95.387
pos_1 is now 23.111, 95.387
s1 is 0, true, ok
s1 is now 23, false, NETERR
car_1 is a QBC of 2133
car_1 is brand new
car_1 is model: QBC - year: 2133 - used: false
car_2 is a model: ZZ7 - year: 2042 - used: false
car_2 is now model: ZZ7 - year: 2042 - used: true
```

More on structs:
```rust
// need to use debug and clone traits
// to be able to print the struct instance with debug operator
// to be able to clone an instance of the struct
// more on traits later#[derive(Debug, Clone)]
struct Spaceship {
    name: String,
    crew: u8,
    propellant: f64,
}// methods are defined within a impl blockimpl Spaceship {
    fn get_name(&self) -> &str {
      // transform string to string slice with borrow operator &self.name
    } fn add_fuel(&mut self, gallons: f64) {
        self.propellant += gallons;
    } // this is an associated function
    // associated to the struct data type
    // similar to method but no &self reference
    // used for functions related to the struct in general,
    // not a specific instance
    // (like class static methods in Object orientation)
    // commonly used to construct instances of struct fn new(name: &str) -> Spaceship {
      Spaceship {
        name: String::from(name),
        crew: 11,          // default value for all instances
        propellant: 0.0    // default value for all instances
      }
    }
}fn main() {
    let mut spaceship1 = Spaceship {
        name: String::from("spaceship1"),
        crew: 123,
        propellant: 1234567.654,
    }; // accessing field value println!("spaceship1 has {} members.", spaceship1.crew); spaceship1.crew = 99; println!(
        "After attack, spaceship1 has now {} members.",
        spaceship1.crew
    ); println!("spaceship1 is {:?}", spaceship1); // by default struct data is stored on the STACK
    // if struct contains HEAP-stored data (like a string),
    // the pointer is stored on the STACK and the data on the HEAP // create struct instance from fields of other instance
    //  (like spread operator in JS but two dots instead of three)
    // it is called struct update syntax
    // it allows to create new instances
    //  by copying the values of fields of an existing instance
    // (except for fields explicitly set in new instance) let spaceship2 = Spaceship {
        name: String::from("Galactos"),
        ..spaceship1
    }; println!("spaceship2 is {:?} members.", spaceship2); // when modifying the copied struct instance
    // it will not affect new instances after the copy
    // (unlike JavaScript references that are kept,
    // when spreading objects with arrays...) spaceship1.name = String::from("Battlestar"); spaceship1.crew = 78; assert_eq!(spaceship2.crew, 99); println!("spaceship1 is {:?}", spaceship1); println!("spaceship2 is {:?}", spaceship2); // to copy all fields, even the heap based ones,
    // you need to create a copy of the struct instance
    // otherwise when using struct update syntax it moves ownership of heap-based data
    // meaning that you could no longer use the associated fields from the copied instance let mut spaceship3 = Spaceship {
        // need to manually implement the clone trait
        // on the struct definition (see above) ..spaceship1.clone()
    }; println!("spaceship3 is {:?}", spaceship3); let name = spaceship3.get_name(); println!("name is {}", name); println!("spaceship3 propellant is {}", spaceship3.propellant);

    spaceship3.add_fuel(4567.113);

    println!(
      "After going to space refuel station, spaceship3 propellant is now {}",
      spaceship3.propellant
    ); // to call an assocaited function, use the path operator (::) let spaceship4 = Spaceship::new("Serenity"); assert_eq!(spaceship4.crew, 11);
}
```
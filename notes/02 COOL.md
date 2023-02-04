# Introduction to COOL

Compiling COOL

```
coolc filename.cl
```

This generates an object file to run

```
spim filename.s
```



The variables are defined and used only in ``let-in`` block

```javascript
class Main inherits IO {
    
    main() : Object {
        let hello : String <- "Hello ",
            world : String <- "World ",
            newline : String <- "\n"
        
        in 
            out_string(hello.concat(world.concat(newline)))
    };
};
```



Ordinary ``if-else`` block. Compare equality is achieved by ``=`` instead of ``==`` 

```bash
if (x=1) then
	something
else
	something
fi
```



Block below is similar to ``switch``, in the lecture it was used to convert class members depending on their types

```javascript
item : Object;

let string: String <-
    case item of 
        i: Int => i2a(i) // converts integer to ascii
        s: String => s;
        0: Object => {abort(); ""; }
    esac;
in
	something
```


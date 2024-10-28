    Primitive types

string      
bool    
number      

```variable "name"{        
    type = string     
    default = "xyz"           
}  ```      

    collection

list  ( ordered collection can be accessed by indices)            
```variable "lst"{
    type = list(string)
    default = [ "","" ]
}```


set  (unique list of elements)          
```variable "lsttpl"{
    type = tuple([string,number])
    default =  ["",4]
} ```      


map                 
```variable "mpvariable"{
    type = map(string)
    default = {
        name = "dev",
        last = "singh"
    }
}```           
object                   
```variable "obj"{
    type = object({
        name = string,
        age  = number
    })
    default = {
        name = "",
        age = 2
    }
}```



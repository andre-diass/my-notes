
## YAML

- the letters mean: ain´t a markup language
- it is a data format used to exchange data
- it’s similiar to XML and JSON
- I can store only data and not commands (such as in programming languages)
- this is know as data serialization
- data serialization is process of converting data objects into a complex data structure, into stream of bytes
    - yaml is a data serialization language

• Data Serialization: Translation of Object (Code + Data) into stream of bytes that saves the state of this object in a form that is transmittable. Using Serialization, data can be converted into code and code can be converted into data again.

### Data types

```yaml
# key value pairs
apple:"is a fruit"

# lists
- apple
- mango
- banana
- Apple (yaml is case sensitive)
---  #this dashs tell that these data structures are different documents. one above and one below
# block
cites:  # means that 'cities' is pointing to the list below
 - rio
 - macapa
 - belem
... # this tells that the document is finisihed

# keep in mind also that the data structure abobe can also be written as:
cities: [rio, macapa, belem]
{apple: "is a fruit"}

# strings
myself: Andre Dias
fruit: "apple"
job: 'software engineer'

# write a single line in multiple lines
message: >
this will
all be 
in a single line

# number
number: 123

#boolean:
booleanValueFalse: No # n, N, false, False, FALSE
booleanValueTrue: Yes # yes, y, Y
```

### Yaml Automatically Determines the data type if not specified

```yaml
name: Hammad
age: 20
graduate: no

```

### But you can specify a dataType

```yaml
variable: !!datatype value
age: !!int 20

```

### Some Common are

```yaml
zero: !!int 0
positiveNum: !!int 45
negativeNum: !!int -27
commaValue: !!int 245_000 #245,000

```

### Other Types

```yaml
PI: !!float 3.14
infinite: !!infinite .inf
not a num: !!nan .nan
booleanValue: !!boolean no
nameString: !!str Hammad
nullDataType: !!null null #null or NULL or ~

```

### Lists

```yaml
- Item1
- Item2
- Item3

```

### Nested Lists (YAML)

```yaml
-
 - Item1
 - Item2
 - Item3

-
 - Item1
 - Item2
 - Item3

```

### Nested lists (JSON)

```json
[
  [
    "Item1",
    "Item2",
    "Item3"
  ],
  [
    "Item1",
    "Item2",
    "Item3"
  ]
]
```

### Block Type / Object

```yaml
ObjectTypeKeyValue:
  KeyValue: Pair
  KeyValue2: Pair2

```

### Or

```yaml
ObjectTypeSimpleList: 
  -Item1
  -Item2
  -Item3

```

### Remember Indentation (one space) is very important here

```yaml
aboutTwoMultipleLine: |-
  I am a CS student
  Currently Learning DevOps
  and Android Dev

```

### Single Key but have two Values

```yaml
pairExample:
  - job: Student
  - job: Teacher

```

## Map, Pairs and Sets

```yaml
# key: value pairs are called maps
!!map

# nested mappings: map within an map
name: Kunal Kushwaha
role:
  age: 78
  job: student
  
# same as
name: Kunal Kushwaha
role: { age: 78, job: student}

# pairs: keys may have duplicate values
# !!pairs

pair example: !!pairs
 - job: student
 - job: teacher

# same as
pair example: !!pairs [job: student, job: teacher]
# this will be an array of hashtables

# !!set will allow you to have unique values
names: !!set
 ? Kunal
 ? Apoorv
 ? Rahul
```

### Dictionary(YAML)

```yaml
People:
 Hammad:
  - Role: Student
  - Age: 20
 Kunal:
  -Role: Teacher
  -Age: 78

```

### Dictionary (JSON)

```json
{
  "People": {
    "Hammad": [
      {
        "Role": "Student"
      },
      {
        "Age": 20
      }
    ],
    "Kunal": {
      "-Role": "Teacher",
      "-Age": 78
    }
  }
}
```

Nested (YAML)

```yaml
---
School:
- name: DPS
  pricipal: Someone
  Students:
  - rno: 12
    name: Kunal Kuswaha
    marks: 67
```

Nested (JSON)

```json
{
    "School": [
        {
            "name": "DPS",
            "pricipal": "Someone",
            "Students": [
                {
                    "rno": 12,
                    "name": "Kunal Kuswaha",
                    "marks":67
                }
            ]
        }
    ]
}
```

### Reusing Properties

`Likes: &likes
 - Fruites: Mango
 - Food: Biryani

Person1:
 -Name: Hammad
 <<: *likes`

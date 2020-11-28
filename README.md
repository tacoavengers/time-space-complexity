# time-space-complexity
time and space complexity

### What is Big O?

- It's a way for developers to describe how long an algorithm takes to run.  Developers need a way to compare the efficiences of different approaches to the same problem.

import math    
import random    
import time    
from datetime import datetime    
animals = ['Duck', 'Jackal', 'Hippo', 'Aardvark', 'Cat', 'Flamingo', 'Iguana', 'Giraffe', 'Elephant', 'Bear']
###
# O(1)
###
#### Return the name of all animals
```
def getAnimals():
  return animals
```
####
# O(n)
####
##### Returns the number of animals
```
def countAnimals():
    num_animals = 0
    for animal in animals:
        num_animals += 1
    return num_animals
```
##### Returns each animal with all letters lowercase
```
def getLowercaseAnimals():
    lowercase_animals = animals
    animal_index = 0
    for animal in animals:
        lowercase_animals[animal_index] = lowercase_animals[animal_index].lower()
        animal_index += 1
    return lowercase_animals
```
##### Given the name of a animal,return True if that animal is in the list, False otherwise
```
def hasAnimal(animal_name):
    num_comparisons = 0
    for animal in animals:
        num_comparisons += 1
        print(f"comparisons: {num_comparisons}")
        if animal == animal_name:
            return True
    return False
```
##### Given the name of a animal,return the animal's index if that animal is in the list, -1 otherwise
```
def findAnimal(animal_name):
    animal_index = 0
    for animal in animals:
        if animal == animal_name:
            return animal_index
        animal_index += 1
    return -1
```

##### Shuffle the order of the stored animals
```
def shuffleAnimals():
    num_animals = countAnimals()
    for i in range(num_animals):
        random_i = random.randrange(num_animals)
        temp_storage = animals[i]
        animals[i] = animals[random_i]
        animals[random_i] = temp_storage
```

###
# O(n^2)
###
animals = ['Duck', 'Jackal', 'Hippo', 'Aardvark', 'Cat', 'Flamingo', 'Iguana', 'Giraffe', 'Elephant', 'Bear']

#### Print a list of all possible animal pairs
```
def printAnimalPairs(animals):
    num_operations = 0
    for animal1 in animals:
        for animal2 in animals:
            num_operations += 1
            print (f"{num_operations}: {animal1} - {animal2}")

printAnimalPairs(animals)
```
###
# O(n^3)
###
#### Print a list of all possible animal triples
```
def printAnimalTriples():
    num_operations = 0
    for animal1 in animals:
        for animal2 in animals:
            for animal3 in animals:
                num_operations += 1
                print (f"{num_operations}: {animal1} - {animal2} - {animal3}")
```
###
# O(2^n)
###
# Given a list, return a list of all possible combination of animals
```
def getListOfAnimalCombos(l):
    list_length = len(l)
    if list_length == 0:
        return [ [] ]
    else:
        animalCombos = []
        previousCombos = getListOfAnimalCombos( l[1:] )
        for combo in previousCombos:
            animalCombos.append( combo )
            animalCombos.append( combo + [l[0]] )
        return animalCombos
```
###
# O(n!)
###
# Given a list,return a list of all possible arrangements of list items
```
def getAllArrangements(l):
    list_length = len(l)
    if list_length <= 1:
        return [l]
    else:
        arrangements = []
        previousArrangements = getAllArrangements( l[1:] )
        for previousArrangement in previousArrangements:
            for i in range(len(previousArrangement) + 1):
                arrangements.append( previousArrangement[i:] + [l[0]] + previousArrangement[:i] )
        return arrangements
```

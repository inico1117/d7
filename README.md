# d7
#format()
'{} is a {}'.format('This','placeholder')
'{0} can be {1}'.format('stings','formatted')
'{name} wants to eat {food}'.format(name='Bob',food='fish')

#dict
dict={'one':1,'two':2,'three':3}
dict.keys()
dict.values()
dict.items()
'one' in dict => True
1 in dict => False
dict.get('two') => 2
dict.get('four') => None
dict.get('two',5) => 2
dict.get('four',4) => 4
dict.get('four',7) => 7
dict.setdefault('five',5) => 5
dict.setdefault('five',6) => 5
dict() =>{'one':1,'two':2,'three':3,'five':5}

#set
set([1,2,2,7,4,5]) => (1,2,4,5,7)

set{4,2,3,3,5}
set => {2,3,4,5}

set.add(7)
set => {2,3,4,5,7}

other_set={1,3,4,6,8}
set&other_set => {3,4}
set|other_set => {1,2,3,4,5,6,7,8}
{1,2,3,4} - {2,3,5}  => {1,4}
{1,2,3,4} ^ {2,3,5}  => {1,4,5}

#for loops
for animal in ['dog','cat','monkey']:
    print('{} is an animal'.format(animal))
    
# *
def all_the_args(*args,**kws):
    print(args)
    print(kws)
all_the_args(1,2,a=3,b=4) => (1,2)
                             {a=3,b=4}

#function
def creat_adder(x):
    def adder(y):
        return x+y
    return adder

sum=create_adder(10)
sum(3) => 13

#map
list(map(sum,[1,2,3])) => [11,12,13]
list(map(lambda x,y:x**y,[2,4,6],[3,2,1])) => [8,16,6] 
list(map(max,[1,2,3],[4,2,1])) => [4,2,3]

#comprehension
[x for x in 'abcddeef' if x in 'abc'] => ['a','c','b']
{x for x in 'abcddeef' if x in 'abc'} => {'a','c','b'}
{x:x**2 for x in range(5)} => {0: 0, 1: 1, 2: 4, 3: 9, 4: 16}

#class
class Human(object):
    species='H.species'
    def __init__(self,name):
        self.name=name
    def say(self,msg):
        return ('%s:%s' %(self.name,msg))
    def get_species(cls):
        return cls.species
    def age(self):
        return self._age
    def age(self,age):
        self._age=age
 
#math
from math import ceil,floor
print(ceil(3.7)) => 4
print(floor(3.7)) => 3

#iterable
def double_numbers(iterable):
    double_arr=[]
    for i in iterable:
        double_arr.append(i+i)
    return double_arr
for value in double_numbers(range(100000)):
    print value
    if value>5:
        break
        
#join
def get_fruits():
    return ['Banana','Apple','Orange']
print(','.join(get_fruits()))

#wraps
from functools import wraps
def beg(target_function):
    @wraps(target_function)
    def wrapper(*args,**kwargs):
        msg,say_please=target_function(*args,**kwargs)
        if say_please():
            return '{} {}'.format(msg,'Please!I am poor(:')
        return msg
    return wrapper
    
@beg
def say(say_please=False):
    msg='Can you buy me a beer?'
    return msg,say_please
    
print(say()) => Can you buy me a beer?
print(say(say_please=False)) => Can you buy me a beer? Please!I am poor(:

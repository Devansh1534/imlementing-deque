# imlementing-deque
# implementation of deque programs by DSA mentor akash bhaiya

from os import *
from sys import *
from collections import *
from math import *


class Deque:
    def _init_(self, size):
        self.size=size
        self.dq=[0] * size
        self.f=-1
        self.r=-1


    # Pushes 'X' in the front of the deque. Returns True if it gets pushed into the deque, and False otherwise.
    def pushFront(self, x):
        # Write your code here
        if(self.isFull()):
            return False
        if(self.f==-1):
            self.f=0
            self.r=0
        else:
            self.f=(self.f-1+self.size)%self.size
        self.dq[self.f]=x
        return True


    # Pushes 'X' in the back of the deque. Returns True if it gets pushed into the deque, and False otherwise.
    def pushRear(self, x):
        if(self.isFull()):
            return False
        if(self.f==-1):
            self.f=0
        self.r=(self.r+1)%self.size
        self.dq[self.r]=x
        return True



    # Pops an element from the front of the deque. Returns -1 if the deque is empty, otherwise returns the popped element.
    def popFront(self):
        if(self.isEmpty()):
            return -1
        self.p=self.dq[self.f]
        if(self.f==self.r):
            self.f=-1
            self.r=-1
        else:
            self.f=(self.f+1)%self.size;
        return self.p


    # Pops an element from the back of the deque. Returns -1 if the deque is empty, otherwise returns the popped element.
    def popRear(self):
        if(self.isEmpty()):
            return -1
        self.w=self.dq[self.r]
        if(self.f==self.r):
            self.f=self.r=-1
        else:
            self.r=(self.r-1+self.size)%self.size;
        return self.w
        pass


    # Returns the first element of the deque. If the deque is empty, it returns -1.
    def getFront(self):
        # Write your code here
        if(self.isEmpty()):
            return -1
        return self.dq[self.f]
        pass


    # Returns the last element of the deque. If the deque is empty, it returns -1.
    def getRear(self):
        # Write your code here
        if(self.isEmpty()):
            return -1
        return self.dq[self.r]
        pass


    # Returns True if the deque is empty. Otherwise returns False.
    def isEmpty(self):
        # Write your code here
        if(self.f== -1 and self.r==-1):
            return True
        return False


    # Returns True if the deque is full. Otherwise returns False.
    def isFull(self):
        if(self.f==(self.r+1)%self.size):
            return True
        else:
            return False

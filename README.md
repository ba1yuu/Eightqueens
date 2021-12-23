# Eightqueens# -*- coding: utf-8 -*-
"""
Created on Thu Dec 23 15:10:13 2021

@author: User
"""

class solution(object):

    def eightqueens(self, n): 
        self.helper([-1]*n, 0, n)

    def helper(self, col, row, n):  
        if row == n:
            self.printSolution(col, n)      
            return

        for column  in range(n):
            col[row] = column         
            if self.isValid(col, row):
                self.helper(col, row + 1, n)

    def isValid(self, col, row):
        if len(set(col[:row + 1])) != len(col[:row + 1]):   
            return False
        
        for i in range(row):           
            if abs(col[i] - col[row]) == int(row - i):  
                return False
        return True

    def printSolution(self, col, n):
        for row in range(n):
            line = ""
            for column in range(n):
                if col[row] == column:
                    line += " Q\t"
                else:
                    line += " .\t "
            print(line, "\n")
        print('\n')
        
solution().eightqueens(8)
----------------------------------
https://zhuanlan.zhihu.com/p/71796190

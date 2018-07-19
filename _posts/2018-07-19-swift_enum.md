---
layout: post
current: post
cover: 
navigation: True
title: Gettysburg Address
date: 2018-07-19 13:18:00
tags:
class: post-template
subclass: 'post'
author: GermanWings
---


Swift의 enum을 이용하여 연산식 구현하기

indirect enum ArithmeticExpression {
    case number(Int)
    case addition(ArithmeticExpression, ArithmeticExpression)
    case multiplication(ArithmeticExpression, ArithmeticExpression)
}

let ten = ArithmeticExpression.number(10)
let four = ArithmeticExpression.number(4)
let sum = ArithmeticExpression.addition(ten, four)
let final = ArithmeticExpression.multiplication(sum,ArithmeticExpression.number(5))

print(final)

func eval(_ expression: ArithmeticExpression) -> Int {
    switch expression {
    case .number(let value):
        return value
    case .addition(let left, let right):
        return eval(left) + eval(right)
        
    case .multiplication(let left, let right):
        return eval(left) * eval(right)
    }
}

let result: Int = eval(final)
print(result)

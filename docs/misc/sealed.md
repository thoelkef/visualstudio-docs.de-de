---
title: "__sealed | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__sealed_cpp"
  - "__sealed"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "sealed-Schlüsselwort [C++]"
  - "__sealed-Schlüsselwort"
ms.assetid: 9e5f778a-4ad8-468d-9c44-783e576fb49b
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# __sealed
> [!NOTE]
>  Dieses Thema gilt nur für Version 1 von Managed Extensions für C\+\+. Diese Syntax sollte nur verwendet werden, um Code von Version 1 beizubehalten. Finden Sie unter [sealed](/visual-cpp/windows/sealed-cpp-component-extensions) Informationen zur Verwendung der entsprechenden Funktionalität in der neuen Syntax.  
  
 Verhindert, dass eine Methode überschrieben wird oder eine Klasse zur Basisklasse wird.  
  
## Syntax  
  
```  
  
__sealed   
class-specifier  
__sealed   
struct-specifier  
__sealed   
function-declarator  
  
```  
  
## Hinweise  
 Das `__sealed`\-Schlüsselwort gibt an, dass eine Klassenmethode nicht überschrieben werden kann oder dass eine Klasse keine Basisklasse sein kann.  
  
 Wenn Sie das `__sealed`\-Schlüsselwort verwenden, beachten Sie die folgenden Punkte:  
  
-   Eine virtuelle `__sealed`\-Methode kann nicht überschrieben werden.  
  
-   Wenn eine nicht virtuelle Membermethode als `__sealed` gekennzeichnet ist, wird die `__sealed`\-Qualifizierung ignoriert.  
  
-   Eine `__sealed`\-Methode kann nicht rein sein.  
  
-   Die **\_\_sealed** Schlüsselwort darf nicht mit der [\_\_interface](/visual-cpp/cpp/interface) Schlüsselwort.  
  
 Wenn eine Klasse \(oder Struktur\) mit `__sealed` markiert wurde, kann die Klasse nicht als Basisklasse verwendet werden. Zum Beispiel:  
  
```  
__sealed __gc class A {  
   // ...  
};  
// error: cannot derive from a sealed class  
__gc class B : public A { /* ...*/ };  
```  
  
> [!NOTE]
>  Das `__sealed`\-Schlüsselwort ist nicht zulässig, wenn es mit dem `__abstract`\-Schlüsselwort verwendet wird.  
  
## Beispiel  
 Im folgenden Beispiel wird eine versiegelte virtuelle Methode \(`f`\) deklariert. Die Funktion wird dann in `main()` überschrieben, was einen Compilerfehler verursacht:  
  
```  
// keyword__sealed.cpp  
// compile with: /clr:oldSyntax  
  
#using <mscorlib.dll>  
extern "C" int printf_s(const char*, ...);  
  
__gc struct I  
{  
    __sealed virtual void f()  
    {   
        printf_s("I::f()\n");   
    }  
    virtual void g()  
    {  
        printf_s("I::g()\n");  
    }  
};  
  
__gc struct A : I   
{  
    void f() // C3248 sealed function  
    {   
        printf_s("A::f()\n");   
    }     
    void g()  
    {  
        printf_s("A::g()\n");  
    }  
};  
  
int main()  
{  
    A* pA = new A;  
  
    pA->f();  
    pA->g();  
}  
```
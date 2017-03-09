---
title: "__gc | Microsoft Docs"
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
  - "__gc"
  - "__gc_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__gc-Typen"
  - "verwalteten Klassen [C++]"
  - "Verwaltete Klassen"
ms.assetid: 63b1e7ab-d1c8-4582-aa89-21bfddf694a9
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# __gc
> [!NOTE]
>  Dieses Thema gilt nur für Version 1 von Managed Extensions für C\+\+. Diese Syntax sollte nur verwendet werden, um Code von Version 1 beizubehalten. Finden Sie unter [Classes and Structs](/visual-cpp/windows/classes-and-structs-cpp-component-extensions) Informationen zur Verwendung der entsprechenden Funktionalität in der neuen Syntax.  
  
 Deklariert einen \_\_gc\-Typ.  
  
## Syntax  
  
```  
  
__gc  
array-specifier  
__gc   
class-specifier  
__gc   
struct-specifier  
__gc  
interface-specifier  
__gc  
pointer-specifier  
__gc new  
  
```  
  
## Hinweise  
 Ein \_\_gc\-Typ ist eine Erweiterung der C\+\+Programmiersprache, die die .NET Framework\-Programmierung vereinfacht, indem Sie Funktionen wie Interoperabilität und Garbage Collection bereitstellt.  
  
> [!NOTE]
>  Jede Memberfunktion einer abstrakten \_\_gc\-Klasse muss definiert werden, es sei denn, die Memberfunktion ist rein virtuell.  
  
 In verwalteten Erweiterungen für C\+\+ sind die Entsprechungen zu einer C\#\-Klasse und einer C\#\-Struktur wie folgt:  
  
|Verwaltete Erweiterungen für C\+\+|C\#|Weitere Informationen|  
|----------------------------------------|---------|---------------------------|  
|"\_\_gc struct" oder "\_\_gc class"|Klasse|[class](/dotnet/csharp/language-reference/keywords/class)\-Schlüsselwort|  
|"\_\_value struct" oder "\_\_value class"|struct|[struct](/dotnet/csharp/language-reference/keywords/struct)\-Schlüsselwort|  
  
## Beispiel  
 Im folgenden Beispiel wird eine verwaltete Klasse \(`X`\) mit einem öffentlichen Datenmember deklariert, der durch einen verwalteten Zeiger bearbeitet wird:  
  
```  
// keyword__gc.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
using namespace System;  
  
__gc class X {  
public:  
   int i;  
   int ReturnInt() { return 5; }  
};  
  
int main() {  
   // X is a __gc class, so px is a __gc pointer  
   X* px;  
   px = new X;   // creates a managed object of type X  
   Console::WriteLine(px->i);  
  
   px->i = 4;   // modifies X::i through px  
   Console::WriteLine(px->i);  
  
   int n = px->ReturnInt();   // calls X::ReturnInt through px  
   Console::WriteLine(n);  
}  
```  
  
## Ausgabe  
  
```  
0  
4  
5  
```
---
title: "__nogc | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__nogc_cpp"
  - "__nogc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__nogc-Typdeklarationen"
  - "Klassen [C++], nicht verwalteten Typ"
  - "nicht verwaltete Klassen, die Deklaration von"
  - "Nicht verwaltete Klassen"
ms.assetid: 3e7f1b09-0fc3-4a8f-9458-a22f7a38ce45
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# __nogc
> [!NOTE]
>  Dieses Thema gilt nur für Version 1 von Managed Extensions für C\+\+. Diese Syntax sollte nur verwendet werden, um Code von Version 1 beizubehalten. In der neuen Syntax ist es nicht erforderlich, einen Typ explizit als nicht verwaltet zu kennzeichnen.  
  
 Deklariert explizit einen nicht verwalteten Typ.  
  
## Syntax  
  
```  
  
__nogc   
class-specifier  
__nogc   
struct-specifier  
__nogc  
interface-specifier  
__nogc  
array-specifier  
__nogc  
pointer-specifier  
__nogc  
new  
  
```  
  
## Hinweise  
 Das `__nogc`\-Schlüsselwort wird verwendet, um explizit anzugeben, dass ein Objekt auf dem Standard\-C\+\+\-Heap zugewiesen ist. Dieses Schlüsselwort ist optional. Wenn Sie `__gc` oder `__nogc` nicht vor einer Klassendeklaration angeben, ist der Standardwert `__nogc`.  
  
 Objekte dieses Typs sind C\+\+\-Standardobjekten insofern ähnlich, als dass sie vom Standard\-C\+\+\-Heap zugewiesen sind und nicht den Einschränkungen eines verwalteten Objekts unterliegen.  
  
 Das `__nogc`\-Schlüsselwort wird auch verwendet, wenn ein Objekt vom Typ "\_\_value" explizit auf dem Standard\-C\+\+\-Heap zugewiesen ist:  
  
```  
// keyword__nogc.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
__value struct V {   
   int i;  
};  
int main() {  
   V * v = __nogc new V;  
   v->i = 10;  
   delete v;  
}  
```  
  
> [!NOTE]
>  Das `__nogc`\-Schlüsselwort kann auch auf Array\- und Zeigertypen angewendet werden.  
  
 Ein gc\-Zeiger kann kein Member einer `__nogc`\-Klasse sein. Richtlinien zum Einbetten eines Werttyps in eine `__nogc`\-Klasse finden Sie unter [\_\_value](../misc/value.md).  
  
## Beispiel  
 Im folgenden Beispiel wird eine nicht verwaltete Klasse deklariert \(`X`\) und ein Objekt instanziiert und geändert:  
  
```  
// keyword__nogc_2.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
using namespace System;  
  
__nogc class X {  
public:  
   int i;  
};  
  
int main() {  
   X* x;   // declares an unmanaged pointer of type X  
   x = new X();   // creates unmanaged object of type X on the C++ heap  
   Console::WriteLine(x->i);  
  
   x->i = 4;   // modifies unmanaged object  
   Console::WriteLine(x->i);  
  
   delete x;   // call C++ delete operator to clean up resource  
}  
```  
  
 **48378256 4**
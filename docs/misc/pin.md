---
title: "__pin | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__pin"
  - "__pin_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Festhalten von Zeigern, __pin-Schlüsselwort"
  - "Nicht verwaltete Typen"
  - "__pin-Schlüsselwort"
ms.assetid: 8b55c792-5654-4669-bb0e-a52100f4cabe
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# __pin
**Hinweis** Dieses Thema gilt nur für Version 1 von Managed Extensions für C\+\+. Diese Syntax sollte nur verwendet werden, um Code von Version 1 beizubehalten. Finden Sie unter [pin\_ptr \(C\+\+\/CLI\)](/visual-cpp/windows/pin-ptr-cpp-cli) Informationen zur Verwendung der entsprechenden Funktionalität in der neuen Syntax.  
  
 Verhindert, dass ein Objekt oder eingebettetes Objekt einer verwalteten Klasse von der Common Language Runtime während der Garbage Collection verschoben wird.  
  
## Syntax  
  
```  
  
__pin   
identifier  
  
```  
  
## Hinweise  
 Das `__pin`\-Schlüsselwort deklariert einen Zeiger auf ein Objekt oder ein eingebettetes Objekt einer verwalteten Klasse und verhindert, dass das Objekt während der Garbage Collection durch die Common Language Runtime verschoben wird. Dies ist hilfreich, wenn die Adresse einer verwalteten Klasse an eine nicht verwaltete Funktion übergeben wird, da während der Auflösung des nicht verwalteten Funktionsaufrufs keine unerwartete Adressänderung auftritt.  
  
 Ein fester Zeiger bleibt im lexikalischen Gültigkeitsbereich gültig. Sobald der feste Zeiger den Gültigkeitsbereich verlässt, wird das Objekt nicht mehr als fixiert betrachtet \(es sei denn, es gibt noch andere feste Zeiger, die auf oder in das Objekt zeigen\).  
  
 Der MSIL\-Code enthält kein "Blockbereich"\-Konzept. Alle lokalen Variablen sind im Gültigkeitsbereich der Funktion aktiviert. Um das System zu informieren, dass das Fixieren nicht mehr wirksam ist, generiert der Compiler Code, der dem festen Zeiger den Wert NULL zuweist. Dies können Sie auch selbstständig ausführen, wenn Sie das Objekt lösen müssen, ohne den Block zu verlassen.  
  
 Sie sollten den festen Zeiger nicht in einen nicht verwalteten Zeiger konvertieren und mit diesem nicht verwalteten Zeiger fortfahren, nachdem das Objekt nicht mehr fixiert ist \(nachdem sich der feste Zeiger nicht mehr im Gültigkeitsbereich befindet\). Im Gegensatz zu gc\-Zeigern können feste Zeiger in nicht verwaltete nogc\-Zeiger konvertiert werden. Allerdings liegt es in der Verantwortung des Benutzers, die Fixierung beizubehalten, während der nicht verwaltete Zeiger verwendet wird.  
  
 Es ist nicht empfehlenswert, einen festen Zeiger zu verwenden, um die Adresse einer Variablen abzurufen, und diese Adresse zu verwenden, nachdem der feste Zeiger sich nicht mehr im Gültigkeitsbereich befindet.  
  
```  
// keyword_pin_scope_bad.cpp  
// compile with: /clr:oldSyntax /LD  
#using <mscorlib.dll>  
__gc struct X {  
   int x;  
};  
  
int* Get_x( X* pX ) {  
   int __pin* px = &pX -> x;  
   return px;   // BE CAREFUL px goes of scope,   
                // so object pointed by it is no longer pinned,  
                // making the return value unsafe.  
}  
```  
  
 Das folgende Beispiel zeigt korrektes Verhalten:  
  
```  
// keyword_pin_scope_good.cpp  
// compile with: /clr:oldSyntax /LD  
#using <mscorlib.dll>  
__gc struct X {  
   int x;  
};  
  
int Get_x( X* pX ) {  
   int __pin* px = &pX -> x;  
   return *px;   // OK, value obtained from px before px out of scope  
}  
```  
  
## Beispiel  
 Im folgenden Beispiel wird das Objekt, auf das von `pG` gezeigt wird, fixiert, bis es sich außerhalb des gültigen Bereichs befindet:  
  
```  
// keyword__pin.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
#include <iostream>  
  
__gc class G {   
public:   
   int i;   
   G() {i = 0;};  
};  
  
class H {  
public:  
   // unmanaged function  
   void incr(int * i) {  
      (*i)++;   
      std::cout << *i << std::endl;  
   };  
};  
  
int main() {  
   G __pin * pG = new G;  // pG is a pinning pointer  
   H * h = new H;  
   // pointer to managed data passed as actual parameter of unmanaged   
   // function call  
   h->incr(& pG -> i);   
}  
```  
  
## Ausgabe  
  
```  
1  
```
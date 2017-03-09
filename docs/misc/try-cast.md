---
title: "__try_cast | Microsoft Docs"
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
  - "__try_cast"
  - "__try_cast_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__try_cast-Schlüsselwort"
  - "Umwandlungsfehler"
  - "Ausnahmen, die nicht erfolgreiche Umwandlungen"
  - "Auslösen von Ausnahmen, die nicht erfolgreiche Umwandlungen"
ms.assetid: e9e5da3a-f5b9-4915-b30a-a432e8574d03
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# __try_cast
**Hinweis** Dieses Thema gilt nur für Version 1 von Managed Extensions für C\+\+. Diese Syntax sollte nur verwendet werden, um Code von Version 1 beizubehalten. Finden Sie unter [safe\_cast](/visual-cpp/windows/safe-cast-cpp-component-extensions) Informationen zur Verwendung der entsprechenden Funktionalität in der neuen Syntax.  
  
 Führt die angegebene Umwandlung aus oder löst eine Ausnahme aus, wenn bei der Umwandlung ein Fehler auftritt.  
  
## Syntax  
  
```  
  
__try_cast <  
 type-id  
 >  
(  
expression   
)  
  
```  
  
## Hinweise  
 Das `__try_cast`\-Schlüsselwort \(mit ähnlichem Verhalten wie [dynamic\_cast](/visual-cpp/cpp/dynamic-cast-operator)\) unterstützt das automatische Auslösen einer Ausnahme \(vom Typ **System::InvalidCastException**\), wenn bei der angegebenen Umwandlungsoperation ein Fehler auftritt.  
  
 Das `__try_cast`\-Schlüsselwort kann während der Testphase Ihrer Anwendung verwendet werden. Bei möglichen Umwandlungsfehlern gibt es automatisch eine Warnung aus.  
  
 Wenn Sie Managed Extensions for C\+\+ portieren, ersetzen `__try_cast` Ruft mit [safe\_cast](/visual-cpp/windows/safe-cast-cpp-component-extensions).  
  
 `__try_cast` funktioniert nicht mit Umwandlungen eines Zeigers in Werttypen \([\_\_value](../misc/value.md)\), da es nicht möglich ist, die Typen zur Laufzeit zu überprüfen.  
  
## Beispiel  
 Im folgenden Beispiel wird versucht, einen Zeiger \(vom Typ `Derived`\) in einen anderen Zeiger \(vom Typ `MoreDerived`\) umzuwandeln. Wenn bei der Umwandlung ein Fehler auftritt, wird er vom catch\-Block abgefangen und gemeldet:  
  
```  
// keyword__try_cast.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
using namespace System;  
  
__gc struct Base {};   
__gc struct Derived : Base {};  
__gc struct MoreDerived : Derived {};  
  
int main() {  
   Base*bp = new Derived;  
   try {  
       MoreDerived* mdp = __try_cast<MoreDerived*>(bp);  
   }  
   catch(System::InvalidCastException*) {  
       Console::WriteLine("Could not cast 'bp' to MoreDerived*");  
   }  
}  
```  
  
## Ausgabe  
  
```  
Could not cast 'bp' to MoreDerived*  
```
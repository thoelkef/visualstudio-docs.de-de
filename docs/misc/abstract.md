---
title: "__abstract | Microsoft Docs"
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
  - "__abstract_cpp"
  - "__abstract"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "abstrakte Klassen [C++]"
  - "__abstract-Schlüsselwort"
ms.assetid: fc6eee5e-9f07-4438-97f7-f2e124263575
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# __abstract
> [!NOTE]
>  Dieses Thema gilt nur für Version 1 von Managed Extensions für C\+\+. Diese Syntax sollte nur verwendet werden, um Code von Version 1 beizubehalten. Finden Sie unter [abstract](/visual-cpp/windows/abstract-cpp-component-extensions) Informationen zur Verwendung der entsprechenden Funktionalität in der neuen Syntax.  
  
 Deklariert eine verwaltete Klasse, die nicht direkt instanziiert werden kann.  
  
## Syntax  
  
```  
  
__abstract   
class-specifier  
__abstract   
struct-specifier  
  
```  
  
## Hinweise  
 Das `__abstract`\-Schlüsselwort deklariert, dass die Zielklasse nur als Basisklasse einer anderen Klasse verwendet werden kann. Wird `__abstract` auf eine Klasse oder Struktur angewendet, bedeutet das nicht, dass das Resultat eine \_\_gc\-Klasse oder \_\_gc\-Struktur ist.  
  
 Im Unterschied zum C\+\+\-Begriff einer [abstrakten](/visual-cpp/cpp/abstract-classes-cpp) Basisklasse kann eine Klasse mit dem `__abstract`\-Schlüsselwort ihre Memberfunktionen definieren.  
  
> [!NOTE]
>  Das `__abstract`\-Schlüsselwort ist bei Verwendung mit dem `__value`\-Schlüsselwort oder dem `__sealed`\- Schlüsselwort nicht zulässig und bei Verwendung mit dem `__interface`\-Schlüsselwort redundant.  
  
## Beispiel  
 Im folgenden Beispiel wird die `Derived`\-Klasse von der abstrakten Basisklasse \(`Base`\) abgeleitet. Der Versuch der Instanziierung wird dann für beide durchgeführt, ist aber nur für `Derived` erfolgreich.  
  
```  
// keyword__abstract.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
  
__abstract __gc class Base {  
   int BaseFunction() {  
      return 0;  
   }  
};  
  
__gc class Derived: public Base {};  
  
int main() {  
   Base* MyBase = new Base();   // C3622 can't BAse is abstract  
   Derived* MyDerived = new Derived();  
}  
```
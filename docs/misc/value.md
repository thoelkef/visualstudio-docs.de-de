---
title: "__value | Microsoft Docs"
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
  - "__value_cpp"
  - "__value"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__value-Schlüsselwort"
  - "Deklarieren von Werttypen"
  - "__value-Schlüsselwort, syntax"
ms.assetid: b14b64f7-5db6-4e92-a144-fcbf67572b49
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# __value
> [!NOTE]
>  Dieses Thema gilt nur für Version 1 von Managed Extensions für C\+\+. Diese Syntax sollte nur verwendet werden, um Code von Version 1 beizubehalten. Finden Sie unter [Classes and Structs](/visual-cpp/windows/classes-and-structs-cpp-component-extensions) Informationen zur Verwendung der entsprechenden Funktionalität in der neuen Syntax.  
  
 Deklariert eine Klasse als \_\_value\-Typ.  
  
## Syntax  
  
```  
  
__value  
 class-specifier  
__value  
 struct-specifier  
__nogc  
array-specifier  
__nogc  
pointer-specifier  
  
```  
  
## Hinweise  
 Ein `__value`\-Typ unterscheidet sich von `__gc`\-Typen insoweit, als dass die `__value`\-Typvariablen ihre Daten direkt enthalten, während verwaltete Variablen auf ihre Daten verweisen, die im Common Language Runtime\-Heap gespeichert sind.  
  
 Für `__value`\-Typen gelten die folgenden Bedingungen:  
  
-   Das `__value`\-Schlüsselwort kann nicht auf eine Schnittstelle angewendet werden.  
  
-   Ein `__value`\-Typ kann von einer beliebigen Anzahl von Schnittstellen erben, aber nicht von anderen Typen oder von `__value`\-Typen.  
  
-   Ein `__value`\-Typ ist gemäß Definition versiegelt. Weitere Informationen finden Sie unter [\_\_sealed](../misc/sealed.md).  
  
-   Es ist zulässig, einen `__value`\-Typ überall dort zu verwenden, wo ein verwalteter Typ verwendet werden kann.  
  
> [!NOTE]
>  Das `__value`\-Schlüsselwort ist nicht zulässig, wenn es mit dem `__abstract`\-Schlüsselwort verwendet wird.  
  
 Ein `__value`\-Typ kann explizit mit einem **System::Object**\-Zeiger verknüpft sein. Dies wird als Boxing bezeichnet.  
  
 Die folgenden Richtlinien gelten für das Einbetten eines Werttyps innerhalb eines `__nogc`\-Typs:  
  
-   Der Werttyp muss **LayoutSequential** oder **LayoutExplicit** aufweisen.  
  
-   Der Werttyp darf keine gc\-Zeigermember aufweisen.  
  
-   Der Werttyp darf keine privaten Datenmember aufweisen.  
  
 In verwalteten Erweiterungen für C\+\+ sind die Entsprechungen zu einer C\#\-Klasse und einer C\#\-Struktur wie folgt:  
  
|Verwaltete Erweiterungen für C\+\+|C\#|Weitere Informationen|  
|----------------------------------------|---------|---------------------------|  
|\_\_gc struct<br /><br /> \- oder \-<br /><br /> \_\_gc class|Klasse|[class](/dotnet/csharp/language-reference/keywords/class)\-Schlüsselwort|  
|\_\_value struct<br /><br /> \- oder \-<br /><br /> \_\_value class|struct|[struct](/dotnet/csharp/language-reference/keywords/struct)\-Schlüsselwort|  
  
## Beispiel  
 Im folgenden Beispiel wird ein `__value`\-Typ \(`V`\) deklariert, dann werden zwei Instanzen des `__value`\-Typs bearbeitet:  
  
```  
// keyword__value.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
  
__value struct V {   
   int m_i;  
};  
  
int main() {  
   V v1, v2;  
   v1.m_i = 5;  
   v2 = v1;   // copies all fields of v1 to v2  
   v2.m_i = 6;   // does not affect v1.m_I  
}  
```
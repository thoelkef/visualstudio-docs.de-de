---
title: "CA2208: Argumentausnahmen korrekt instanziieren | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2208"
  - "InstantiateArgumentExceptionsCorrectly"
helpviewer_keywords: 
  - "CA2208"
  - "InstantiateArgumentExceptionsCorrectly"
ms.assetid: e2a48939-d9fa-478c-b2f9-3bdbce07dff7
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 19
---
# CA2208: Argumentausnahmen korrekt instanziieren
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|InstantiateArgumentExceptionsCorrectly|  
|CheckId|CA2208|  
|Kategorie \(Category\)|Microsoft.Usage|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## Ursache  
 Als mögliche Ursachen kommen folgende Situationen in Betracht:  
  
-   Es wird der \(parameterlose\) Standardkonstruktor eines Ausnahmetyps aufgerufen, der [System.ArgumentException](assetId:///System.ArgumentException?qualifyHint=True&autoUpgrade=True) entspricht oder davon abgeleitet wird.  
  
-   Es wird ein falsches Zeichenfolgenargument an den parametrisierten Konstruktor eines Ausnahmetyps übergeben, der [System.ArgumentException.](assetId:///System.ArgumentException.?qualifyHint=True&autoUpgrade=True) entspricht oder davon abgeleitet wird.  
  
## Regelbeschreibung  
 Statt den Standardkonstruktor aufzurufen, sollte einer der überladenen Konstruktoren aufgerufen werden, der zulässt, dass eine aussagekräftigere Ausnahmemeldung bereitgestellt wird.  Die Ausnahmemeldung sollte auf den Entwickler abzielen und die Fehlerbedingung und Wege zur Behebung oder Vermeidung der Ausnahme klar darlegen.  
  
 Die Signaturen der Konstruktoren von <xref:System.ArgumentException> und davon abgeleiteten Typen mit einer oder zwei Zeichenfolgen sind nicht konsistent in Bezug auf den `message`\-Parameter und den `paramName`\-Parameter.  Stellen Sie sicher, dass diese Konstruktoren mit den richtigen Zeichenfolgenargumenten aufgerufen werden.  Die Signaturen lauten wie folgt:  
  
 <xref:System.ArgumentException>\(string `message`\)  
  
 <xref:System.ArgumentException>\(string `message`, string `paramName`\)  
  
 <xref:System.ArgumentNullException>\(string `paramName`\)  
  
 <xref:System.ArgumentNullException>\(string `paramName`, string `message`\)  
  
 <xref:System.ArgumentOutOfRangeException>\(string `paramName`\)  
  
 <xref:System.ArgumentOutOfRangeException>\(string `paramName`, string `message`\)  
  
 <xref:System.DuplicateWaitObjectException>\(string `parameterName`\)  
  
 <xref:System.DuplicateWaitObjectException>\(string `parameterName`, string `message`\)  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, rufen Sie einen Konstruktor auf, der eine Meldung, einen Parameternamen oder beides annimmt, und stellen sicher, dass die Argumente für den Typ von <xref:System.ArgumentException>, der aufgerufen wird, korrekt sind.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Eine Warnung dieser Regel kann nur dann gefahrlos unterdrückt werden, wenn ein parametrisierter Konstruktor mit den richtigen Zeichenfolgenargumenten aufgerufen wird.  
  
## Beispiel  
 Im folgenden Beispiel wird ein Konstruktor veranschaulicht, der unordnungsgemäß eine Instanz des ArgumentNullException\-Typs instanziiert.  
  
 [!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/CPP/ca2208-instantiate-argument-exceptions-correctly_1.cpp)]
 [!code-cs[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/CSharp/ca2208-instantiate-argument-exceptions-correctly_1.cs)]
 [!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/VisualBasic/ca2208-instantiate-argument-exceptions-correctly_1.vb)]  
  
## Beispiel  
 Im folgenden Beispiel wird der oben erwähnte Verstoß korrigiert, indem die Konstruktorargumente vertauscht werden.  
  
 [!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/CPP/ca2208-instantiate-argument-exceptions-correctly_2.cpp)]
 [!code-cs[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/CSharp/ca2208-instantiate-argument-exceptions-correctly_2.cs)]
 [!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/VisualBasic/ca2208-instantiate-argument-exceptions-correctly_2.vb)]
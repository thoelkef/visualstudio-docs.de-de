---
title: "CA1506: &#220;berm&#228;&#223;ige Klassenkopplungen vermeiden | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "AvoidExcessiveClassCoupling"
  - "CA1506"
helpviewer_keywords: 
  - "AvoidExcessiveClassCoupling"
  - "CA1506"
ms.assetid: 9f0943c0-e802-4e3f-8798-2ab8653ddc80
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1506: &#220;berm&#228;&#223;ige Klassenkopplungen vermeiden
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidExcessiveClassCoupling|  
|CheckId|CA1506|  
|Kategorie \(Category\)|Microsoft.Maintainability|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Ein Typ oder eine Methode ist mit vielen anderen Typen gekoppelt.  
  
## Regelbeschreibung  
 Durch diese Regel wird die Klassenkopplung gemessen, indem die eindeutigen Typverweise, die ein Typ oder eine Methode enthält, gezählt werden.  
  
 Typen und Methoden mit einem hohen Grad an Klassenkopplung können schwer verwaltbar sein.  Es empfiehlt sich, Typen und Methoden zu verwenden, die lose Kopplung und hohe Kohäsion aufweisen.  
  
## Behandeln von Verstößen  
 Um diesen Verstoß zu behandeln, gestalten Sie den Typ oder die Methode um, um die Anzahl der Typen zu reduzieren, mit denen sie gekoppelt sind.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Schließen Sie diese Warnung aus, wenn ein Typ oder eine Methode trotz der großen Anzahl von Abhängigkeiten von anderen Typen als verwaltbar angesehen wird.  
  
## Siehe auch  
 [Verwaltbarkeitswarnungen](../code-quality/maintainability-warnings.md)   
 [Messen von Komplexität und Verwaltbarkeit verwalteten Codes](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)
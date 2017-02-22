---
title: "Verwaltbarkeitswarnungen | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.codeanalysis.maintainabilityrules"
helpviewer_keywords: 
  - "Warnungen, Verwaltbarkeit"
  - "Analysen für verwalteten Code (Warnungen), Verwaltbarkeitswarnungen"
  - "Verwaltbarkeitswarnungen"
ms.assetid: 537e70ca-a88c-49df-bfc7-0ee63bbe4f16
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Verwaltbarkeitswarnungen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Verwaltbarkeitswarnungen unterstützen die Bibliotheks\- und Anwendungswartung.  
  
## In diesem Abschnitt  
  
|Regel|**Beschreibung**|  
|-----------|----------------------|  
|[CA1500: Variablennamen sollten nicht mit Feldnamen übereinstimmen](../code-quality/ca1500-variable-names-should-not-match-field-names.md)|In einer Instanzenmethode wird ein Parameter oder eine lokale Variable deklariert, dessen bzw. deren Name mit dem Namen eines Instanzenfelds des deklarierenden Typs übereinstimmt. Dies führt zu Fehlern.|  
|[CA1501: Übermäßige Vererbung vermeiden](../code-quality/ca1501-avoid-excessive-inheritance.md)|Ein Typ ist in seiner Vererbungshierarchie mehr als vier Ebenen tief.  Tief verschachtelte Typenhierarchien können schwer zu verfolgen, verstehen und verwalten sein.|  
|[CA1502: Übermäßige Komplexität vermeiden](../code-quality/ca1502-avoid-excessive-complexity.md)|Diese Regel Komplexität ermöglicht Aussagen über die Anzahl linear unabhängiger Pfade in einer Methode, wobei die Anzahl der Pfade durch die Anzahl und Komplexität bedingter Verzweigungen bestimmt wird.|  
|[CA1504: Irreführende Feldnamen überprüfen](../code-quality/ca1504-review-misleading-field-names.md)|Der Name eines Instanzenfelds beginnt mit "s\_", oder der Name eines static\-Felds \(Shared\-Feld in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\) beginnt mit "m\_".|  
|[CA1505: Nicht wartbaren Code vermeiden](../code-quality/ca1505-avoid-unmaintainable-code.md)|Ein Typ oder eine Methode verfügt über einen niedrigen Wartbarkeitsindexwert.  Ein niedriger Wartbarkeitsindex zeigt an, dass ein Typ oder eine Methode wahrscheinlich schwer zu verwalten ist und geeignet für einen Neuentwurf wäre.|  
|[CA1506: Übermäßige Klassenkopplungen vermeiden](../code-quality/ca1506-avoid-excessive-class-coupling.md)|Durch diese Regel wird die Klassenkopplung gemessen, indem die eindeutigen Typverweise, die ein Typ oder eine Methode enthält, gezählt werden.|  
  
## Siehe auch  
 [Messen von Komplexität und Verwaltbarkeit verwalteten Codes](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)
---
title: "CA1505: Nicht wartbaren Code vermeiden | Microsoft Docs"
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
  - "AvoidUnmaintainableCode"
  - "CA1505"
helpviewer_keywords: 
  - "AvoidUnmaintainableCode"
  - "CA1505"
ms.assetid: 8292b268-5929-4221-b699-f9c414bcec5d
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1505: Nicht wartbaren Code vermeiden
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidUnmantainableCode|  
|CheckId|CA1505|  
|Kategorie \(Category\)|Microsoft.Maintainability|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## Ursache  
 Ein Typ oder eine Methode verfügt über einen niedrigen Wartbarkeitsindexwert.  
  
## Regelbeschreibung  
 Der Wartbarkeitsindex wird auf der Grundlage der folgenden Metriken berechnet: Codezeilen, Programmumfang und zyklomatische Komplexität.  Der Programmumfang ist ein Maßstab für die Schwierigkeit, einen Typ oder eine Methode zu verstehen, und basiert auf der Anzahl von Operatoren und Operanden im Code.  Zyklomatische Komplexität ist ein Maß der strukturellen Komplexität des Typs oder der Methode.  Sie können mehr zur Codemetrik unter [Messen von Komplexität und Verwaltbarkeit verwalteten Codes](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md) erfahren.  
  
 Ein niedriger Wartbarkeitsindex zeigt an, dass ein Typ oder eine Methode wahrscheinlich schwer zu verwalten ist und geeignet für einen Neuentwurf wäre.  
  
## Behandeln von Verstößen  
 Um diesen Verstoß zu behandeln, gestalten Sie den Typ oder die Methode um und unterteilen sie in kleinere präzisere Typen oder Methoden.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Schließen Sie diese Warnung aus, wenn ein Typ oder eine Methode trotz der umfangreichen Größe weiterhin als verwaltbar angesehen wird oder wenn der Typ oder die Methode nicht unterteilt werden kann.  
  
## Siehe auch  
 [Verwaltbarkeitswarnungen](../code-quality/maintainability-warnings.md)   
 [Messen von Komplexität und Verwaltbarkeit verwalteten Codes](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)
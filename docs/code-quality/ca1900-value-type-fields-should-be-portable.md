---
title: "CA1900: Werttypfelder sollten portabel sein | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1900"
  - "ValueTypeFieldsShouldBePortable"
helpviewer_keywords: 
  - "ValueTypeFieldsShouldBePortable"
  - "CA1900"
ms.assetid: 1787d371-389f-4d39-b305-12b53bc0dfb9
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 18
---
# CA1900: Werttypfelder sollten portabel sein
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ValueTypeFieldsShouldBePortable|  
|CheckId|CA1900|  
|Kategorie \(Category\)|Microsoft.Portability|  
|Unterbrechende Änderung|Unterbrechend – Wenn das Feld außerhalb der Assembly gesehen werden kann.<br /><br /> Nicht unterbrechend – Wenn das Feld nicht außerhalb der Assembly sichtbar ist.|  
  
## Ursache  
 Anhand dieser Regel wird überprüft, ob die mit explizitem Layout deklarierten Strukturen korrekt ausgerichtet werden, wenn sie auf 64\-Bit\-Betriebssystemen an nicht verwalteten Code gemarshallt werden.  IA\-64 lässt den Zugriff auf nicht korrekt ausgerichteten Speicher nicht zu, und der Vorgang führt zu einem Absturz, wenn der Verstoß nicht behoben wird.  
  
## Regelbeschreibung  
 Strukturen, die ein explizites Layout mit falsch ausgerichteten Feldern aufweisen, verursachen Abstürze unter 64\-Bit\-Betriebssystemen.  
  
## Behandeln von Verstößen  
 Alle Felder, die kleiner als 8 Bytes sind, müssen Offsets mit einem Vielfachen ihrer Größe aufweisen, und Felder, die mindestens 8 Bytes groß sind, müssen Offsets aufweisen, deren Größe ein Vielfaches von 8 ist.  Eine andere Lösung ist, bei Bedarf `LayoutKind.Sequential` statt `LayoutKind.Explicit` zu verwenden.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Diese Warnung sollte nur unterdrückt werden, wenn sie fälschlicherweise generiert wird.
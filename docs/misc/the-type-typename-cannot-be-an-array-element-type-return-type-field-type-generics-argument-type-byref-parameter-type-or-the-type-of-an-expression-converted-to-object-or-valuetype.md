---
title: "Der Typ &quot;&lt;Typname&gt;&quot; kann kein Arrayelementtyp, R&#252;ckgabetyp, Feldtyp, generischer Argumenttyp, ByRef-Parametertyp oder der Typ eines Ausdrucks sein, der in &quot;Object&quot; oder &quot;ValueType&quot; konvertiert wurde. | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc31396"
  - "BC31396"
helpviewer_keywords: 
  - "BC31396"
ms.assetid: 56998a2c-a705-482e-87ee-5eff707f8a48
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Der Typ &quot;&lt;Typname&gt;&quot; kann kein Arrayelementtyp, R&#252;ckgabetyp, Feldtyp, generischer Argumenttyp, ByRef-Parametertyp oder der Typ eines Ausdrucks sein, der in &quot;Object&quot; oder &quot;ValueType&quot; konvertiert wurde.
In einem Ausdruck wird eine Variable, ein Prozedurparameter, ein Typparameter, eine Funktionsrückgabe oder ein Array mit einem eingeschränkten Typ deklariert.  
  
 Die Common Language Runtime \(CLR\) macht bestimmte Typen ausschließlich für spezielle Sprachunterstützung verfügbar, und diese Typen sollten nicht als Datentypen in der Anwendung verwendet werden. Zu diesen Typen gehören die Strukturen <xref:System.ArgIterator>, <xref:System.RuntimeArgumentHandle> und <xref:System.TypedReference>.  
  
 **Fehler\-ID:** BC31396  
  
### So beheben Sie diesen Fehler  
  
-   Verwenden Sie die eingeschränkte Struktur nicht als deklarierten Datentyp.  
  
## Siehe auch  
 <xref:System.ArgIterator>   
 <xref:System.RuntimeArgumentHandle>   
 <xref:System.TypedReference>
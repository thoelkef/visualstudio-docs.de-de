---
title: "CA1401: P/Invokes d&#252;rfen nicht sichtbar sein | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "PInvokesShouldNotBeVisible"
  - "CA1401"
helpviewer_keywords: 
  - "CA1401"
  - "PInvokesShouldNotBeVisible"
ms.assetid: 0f4d96c1-f9de-414e-b223-4dc7f691bee3
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 17
---
# CA1401: P/Invokes d&#252;rfen nicht sichtbar sein
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|PInvokesShouldNotBeVisible|  
|CheckId|CA1401|  
|Kategorie \(Category\)|Microsoft.Interoperability|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Eine öffentliche oder geschützte Methode in einem öffentlichen Typ enthält das <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>\-Attribut \(in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] auch durch das `Declare`\-Schlüsselwort implementiert\).  
  
## Regelbeschreibung  
 Methoden, die mit dem <xref:System.Runtime.InteropServices.DllImportAttribute>\-Attribut gekennzeichnet sind \(oder Methoden, die in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] mithilfe des `Declare`\-Schlüsselworts definiert wurden\), greifen über Plattformaufrufdienste \(PInvokes\) auf nicht verwalteten Code zu.  Solche Methoden sollten nicht verfügbar gemacht werden.  Wenn diese Methoden privat oder intern bleiben, stellen Sie sicher, dass die Bibliothek nicht für Sicherheitsverletzungen verwendet werden kann, indem sie Aufrufern den Zugriff auf unverwaltete APIs gestattet, die sonst nicht aufgerufen werden könnten.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, ändern Sie die Zugriffsebene der Methode.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  
  
## Beispiel  
 Im folgenden Beispiel wird eine Methode deklariert, die gegen diese Regel verstößt.  
  
 [!code-vb[FxCop.Interoperability.DllImports#1](../code-quality/codesnippet/VisualBasic/ca1401-p-invokes-should-not-be-visible_1.vb)]
 [!code-cs[FxCop.Interoperability.DllImports#1](../code-quality/codesnippet/CSharp/ca1401-p-invokes-should-not-be-visible_1.cs)]
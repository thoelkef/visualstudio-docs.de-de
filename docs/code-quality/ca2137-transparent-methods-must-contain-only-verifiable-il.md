---
title: "CA2137: Transparente Methoden d&#252;rfen nur &#252;berpr&#252;fbare IL enthalten | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2137"
ms.assetid: cbaeb0e1-56b6-43b4-812a-596b2859c329
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2137: Transparente Methoden d&#252;rfen nur &#252;berpr&#252;fbare IL enthalten
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TransparentMethodsMustBeVerifiable|  
|CheckId|CA2137|  
|Kategorie \(Category\)|Microsoft.Security|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Eine Methode enthält nicht überprüfbaren Code oder gibt einen Typ nach Verweis zurück.  
  
## Regelbeschreibung  
 Diese Regel wird für Versuche durch sicherheitstransparenten Code ausgelöst, nicht überprüfbare MSIL \(Microsoft Intermediate Language\) auszuführen.  Die Regel enthält jedoch kein vollständiges IL\-Prüfmodul und verwendet stattdessen Heuristik, um die meisten Verletzungen der MSIL\-Überprüfung abzufangen.  
  
 Um sicher zu sein, dass der Code nur überprüfbare MSIL enthält, führen Sie [Peverify.exe \(PEVerify Tool\)](../Topic/Peverify.exe%20\(PEVerify%20Tool\).md) auf der Assembly aus.  Führen Sie PEVerify mit der **\/transparent**\-Option aus, die die Ausgabe auf ausschließlich nicht überprüfbare transparente Methoden beschränkt, die einen Fehler verursachen würden.  Wenn die \/transparent\-Option nicht verwendet wird, überprüft PEVerify auch wichtige Methoden, die nicht überprüfbaren Code enthalten können.  
  
## Behandeln von Verstößen  
 Um eine Verletzung dieser Regel zu korrigieren, markieren Sie die Methode mit dem <xref:System.Security.SecurityCriticalAttribute>\-Attribut oder dem <xref:System.Security.SecuritySafeCriticalAttribute>\-Attribut, oder entfernen Sie nicht den überprüfbaren Code.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  
  
## Beispiel  
 Für die Methode in diesem Beispiel wird nicht überprüfbarer Code verwendet, und sie sollte mit dem <xref:System.Security.SecurityCriticalAttribute>\-Attribut oder dem <xref:System.Security.SecuritySafeCriticalAttribute>\-Attribut markiert werden.  
  
 [!code-cs[FxCop.Security.CA2137.TransparentMethodsMustBeVerifiable#1](../code-quality/codesnippet/CSharp/ca2137-transparent-methods-must-contain-only-verifiable-il_1.cs)]
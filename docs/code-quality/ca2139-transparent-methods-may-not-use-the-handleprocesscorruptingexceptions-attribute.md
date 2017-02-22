---
title: "CA2139: Transparente Methoden d&#252;rfen das HandleProcessCorruptingExceptions-Attribut nicht verwenden | Microsoft Docs"
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
  - "CA2139"
ms.assetid: 45a0328a-add7-40f9-8934-dff59beb02b3
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2139: Transparente Methoden d&#252;rfen das HandleProcessCorruptingExceptions-Attribut nicht verwenden
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TransparentMethodsMustNotHandleProcessCorruptingExceptions|  
|CheckId|CA2139|  
|Kategorie \(Category\)|Microsoft.Security|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Eine transparente Methode wird mit dem <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute>\-Attribut markiert:  
  
## Regelbeschreibung  
 Diese Regel löst jede Methode aus, die transparent ist und versucht, eine Prozesse beschädigende Ausnahme mit dem <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute>\-Attribut zu behandeln.  Eine Ausnahme, die einen Prozess beschädigt, entspricht einer Ausnahme der CLR Version 4.0\-Ausnahmeklassifizierung, wie <xref:System.AccessViolationException>.  Das HandleProcessCorruptedStateExceptionsAttribute\-Attribut darf nur von sicherheitskritischen Methoden verwendet werden und wird ignoriert, wenn es für eine transparente Methode übernommen wird.  Diese Methode muss sicherheitskritisch oder sicherheitsgeschützt sein, um Prozesse beschädigende Ausnahmen behandeln zu können.  
  
## Behandeln von Verstößen  
 Um eine Verletzung dieser Regel zu korrigieren, entfernen Sie das <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute>\-Attribut, oder markieren Sie die Methode mit dem <xref:System.Security.SecurityCriticalAttribute>\-Attribut oder dem <xref:System.Security.SecuritySafeCriticalAttribute>\-Attribut.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  
  
## Beispiel  
 In diesem Beispiel wird eine transparente Methode mit dem <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute>\-Attribut markiert, und die Regel schlägt fehlt.  Die Methode sollte ebenfalls mit dem <xref:System.Security.SecurityCriticalAttribute>\-Attribut oder dem <xref:System.Security.SecuritySafeCriticalAttribute>\-Attribut markiert werden.  
  
 [!code-cs[FxCop.Security.CA2139.TransparentMethodsMustNotHandleProcessCorruptingExceptions#1](../code-quality/codesnippet/CSharp/ca2139-transparent-methods-may-not-use-the-handleprocesscorruptingexceptions-attribute_1.cs)]
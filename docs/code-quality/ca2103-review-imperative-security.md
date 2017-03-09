---
title: "CA2103: Imperative Sicherheit &#252;berpr&#252;fen | Microsoft Docs"
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
  - "CA2103"
  - "ReviewImperativeSecurity"
helpviewer_keywords: 
  - "CA2103"
  - "ReviewImperativeSecurity"
ms.assetid: d24fde71-bdf6-46c0-8965-9a73dc33c1aa
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2103: Imperative Sicherheit &#252;berpr&#252;fen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ReviewImperativeSecurity|  
|CheckId|CA2103|  
|Kategorie \(Category\)|Microsoft.Security|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Eine Methode verwendet imperative Sicherheit und erstellt möglicherweise die Berechtigung mit Zustandsinformationen oder Rückgabewerten, die sich ändern können, während die Forderung wirksam ist.  
  
## Regelbeschreibung  
 Bei Verwendung imperativer Sicherheit werden mithilfe verwalteter Objekte während der Codeausführung Berechtigungen und Sicherheitsaktionen festgelegt. Im Vergleich dazu werden beim Einsatz deklarativer Sicherheit Attribute verwendet, um Berechtigungen und Aktionen in Metadaten zu speichern.  Imperative Sicherheit ermöglicht großen Handlungsspielraum, weil die Festlegung des Zustands eines Berechtigungsobjekts und die Auswahl von Sicherheitsaktionen mithilfe von Informationen erfolgen kann, die erst zur Laufzeit zur Verfügung stehen.  Diese Flexibilität bringt mit sich aber auch das Risiko in sich, dass die Laufzeitdaten, die zur Festlegung des Berechtigungszustands verwendet werden, nicht unverändert bleiben, während die Aktion ausgeführt wird.  
  
 Verwenden Sie, wenn irgend möglich, deklarative Sicherheit.  Deklarative Anforderungen sind einfacher zu verstehen.  
  
## Behandeln von Verstößen  
 Überprüfen Sie die imperativen Sicherheitsforderungen, um sicherzustellen, dass der Zustand der Berechtigung nicht von Daten abhängt, die sich ändern können, während die Berechtigung verwendet wird.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Eine Warnung dieser Regel kann gefahrlos unterdrückt werden, wenn die Berechtigung nicht auf einer Änderung der Daten beruht.  Die imperative Forderung sollte jedoch in ihre deklarative Entsprechung geändert werden.  
  
## Siehe auch  
 [Secure Coding Guidelines](../Topic/Secure%20Coding%20Guidelines.md)   
 [Daten und Modellierung](../Topic/Data%20and%20Modeling%20in%20the%20.NET%20Framework.md)
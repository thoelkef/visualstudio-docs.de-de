---
title: "CA2108: Deklarative Sicherheit auf Werttypen &#252;berpr&#252;fen | Microsoft Docs"
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
  - "ReviewDeclarativeSecurityOnValueTypes"
  - "CA2108"
helpviewer_keywords: 
  - "CA2108"
  - "ReviewDeclarativeSecurityOnValueTypes"
ms.assetid: d62bffdd-3826-4d52-a708-1c646c5d48c2
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2108: Deklarative Sicherheit auf Werttypen &#252;berpr&#252;fen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ReviewDeclarativeSecurityOnValueTypes|  
|CheckId|CA2108|  
|Kategorie \(Category\)|Microsoft.Security|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## Ursache  
 Ein öffentlicher oder geschützter Werttyp wird durch [Daten und Modellierung](../Topic/Data%20and%20Modeling%20in%20the%20.NET%20Framework.md) oder [Link Demands](../Topic/Link%20Demands.md) geschützt.  
  
## Regelbeschreibung  
 Werttypen werden durch ihre Standardkonstruktoren zugeordnet und initialisiert, bevor andere Konstruktoren ausgeführt werden.  Wenn der Werttyp durch Demand oder LinkDemand geschützt wird und der Aufrufer nicht über die erforderlichen Berechtigungen verfügt, um die Sicherheitsüberprüfung zu bestehen, dann kann kein anderer Konstruktor als der Standardkonstruktor ausgeführt werden, und es wird eine Sicherheitsausnahme ausgelöst.  Der Werttyp wird nicht freigegeben. Er wird in dem Zustand belassen, der durch seinen Standardkonstruktor festgelegt wurde.  Es darf nicht davon ausgegangen werden, dass ein Aufrufer, der eine Instanz der Werttyps übergibt, dazu berechtigt ist, die Instanz zu erstellen oder darauf zuzugreifen.  
  
## Behandeln von Verstößen  
 Sie können einen Verstoß gegen diese Regel nur dann beheben, wenn Sie die Sicherheitsüberprüfung aus dem Typ entfernen und stattdessen Sicherheitsüberprüfungen auf Methodenebene ausführen.  Beachten Sie, dass mit dieser Art der Behebung eines Regelverstoßes Aufrufer mit unzureichenden Berechtigungen nicht daran gehindert werden, Instanzen des Werttyps abzurufen.  Sie müssen sicherstellen, dass eine Instanz des Werttyps im Standardzustand keine sicherheitsrelevanten Daten verfügbar macht und nicht auf schädliche Weise verwendet werden kann.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Eine Warnung dieser Regel kann unterdrückt werden, wenn jeder Aufrufer Instanzen des Werttyps in dessen Standardzustand abrufen kann, ohne die Sicherheit zu gefährden.  
  
## Beispiel  
 Im folgenden Beispiel wird eine Bibliothek veranschaulicht, die einen Werttyp enthält, der gegen diese Regel verstößt.  Beachten Sie, dass beim `StructureManager`\-Typ davon ausgegangen wird, dass ein Aufrufer, der eine Instanz der Werttyps übergibt, dazu berechtigt ist, die Instanz zu erstellen oder darauf zuzugreifen.  
  
 [!code-cs[FxCop.Security.DemandOnValueType#1](../code-quality/codesnippet/CSharp/ca2108-review-declarative-security-on-value-types_1.cs)]  
  
## Beispiel  
 Die folgende Anwendung veranschaulicht die Schwäche der Bibliothek.  
  
 [!code-cs[FxCop.Security.TestDemandOnValueType#1](../code-quality/codesnippet/CSharp/ca2108-review-declarative-security-on-value-types_2.cs)]  
  
 Folgende Ergebnisse werden zurückgegeben:  
  
  **Benutzerdefinierte Konstruktorstruktur: Anforderungsfehler.**  
**Neue Werte SecuredTypeStructure 100 100**  
**Neue Werte SecuredTypeStructure 200 200**   
## Siehe auch  
 [Link Demands](../Topic/Link%20Demands.md)   
 [Daten und Modellierung](../Topic/Data%20and%20Modeling%20in%20the%20.NET%20Framework.md)
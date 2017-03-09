---
title: "CA2114: Methodensicherheit sollte Superset des Typs sein | Microsoft Docs"
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
  - "MethodSecurityShouldBeASupersetOfType"
  - "CA2114"
helpviewer_keywords: 
  - "CA2114"
  - "MethodSecurityShouldBeASupersetOfType"
ms.assetid: 663f7aa4-8be5-4bd5-be92-4e9444f07077
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2114: Methodensicherheit sollte Superset des Typs sein
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|MethodSecurityShouldBeASupersetOfType|  
|CheckId|CA2114|  
|Kategorie \(Category\)|Microsoft.Security|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Ein Typ weist deklarative Sicherheit auf, wie auch eine seiner Methoden für die gleiche Sicherheitsaktion. Bei der Sicherheitsaktion handelt es sich nicht um [Link Demands](../Topic/Link%20Demands.md) oder [Inheritance Demands](http://msdn.microsoft.com/de-de/28b9adbb-8f08-4f10-b856-dbf59eb932d9), und die vom Typ überprüften Berechtigungen sind keine Teilmenge der Berechtigungen, die durch die Methode überprüft werden.  
  
## Regelbeschreibung  
 Eine Methode sollte bei der gleichen Aktion nicht sowohl auf Methodenebene als auch auf Typebene deklarative Sicherheit aufweisen.  Die beiden Überprüfungen werden nicht kombiniert; nur die Anforderung auf Methodenebene wird angewendet.  Wenn ein Typ z. B. die Berechtigung `X` und eine seiner Methoden die Berechtigung `Y` anfordert, benötigt der Code die Berechtigung `X` nicht, um die Methode auszuführen.  
  
## Behandeln von Verstößen  
 Überprüfen Sie den Code, um sicherzustellen, dass beide Aktionen erforderlich sind.  Wenn beide Aktionen erforderlich sind, stellen Sie sicher, dass die Aktion auf Methodenebene die auf Typebene festgelegte Sicherheit umfasst.  Wenn der Typ z. B. die Berechtigung `X` anfordert und seine Methode auch die Berechtigung `Y` anfordern muss, sollte die Methode `X` und `Y` explizit anfordern.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Eine Warnung dieser Regel kann gefahrlos unterdrückt werden, wenn für die Methode nicht die durch den Typ festgelegte Sicherheit benötigt wird.  Ein solches Szenario ist jedoch nicht der Normalfall und sollte Anlass sein, den Entwurf sorgfältig zu überprüfen.  
  
## Beispiel  
 Im folgenden Beispiel werden Umgebungsberechtigungen verwendet, um die Gefahren bei einem Verstoß gegen diese Regel zu veranschaulichen.  In diesem Beispiel erstellt der Anwendungscode eine Instanz des gesicherten Typs, bevor die durch den Typ verlangte Berechtigung verweigert wird.  In einem echten Bedrohungsszenario müsste die Anwendung eine Instanz des Objekts auf andere Weise erhalten.  
  
 Im folgenden Beispiel fordert die Bibliothek die Schreibberechtigung für einen Typ und die Leseberechtigung für eine Methode an.  
  
 [!code-cs[FxCop.Security.MethodLevelSecurity#1](../code-quality/codesnippet/CSharp/ca2114-method-security-should-be-a-superset-of-type_1.cs)]  
  
## Beispiel  
 Der folgende Anwendungscode veranschaulicht die Anfälligkeit der Bibliothek, da die Methode aufgerufen wird, obwohl sie die Sicherheitsanforderung auf Typebene nicht erfüllt.  
  
 [!code-cs[FxCop.Security.TestMethodLevelSecurity#1](../code-quality/codesnippet/CSharp/ca2114-method-security-should-be-a-superset-of-type_2.cs)]  
  
 Folgende Ergebnisse werden zurückgegeben:  
  
  **\[Alle Berechtigungen\] Persönliche Informationen: 16.6.1964 12:00:00**  
**\[Keine Schreibberechtigung \(von Typ gefordert\)\] Persönliche Informationen: 16.6.1964 12:00:00**  
**\[Keine Leseberechtigung \(von Methode gefordert\)\] Konnte nicht auf persönliche Informationen zugreifen: Fehler bei Anforderung.**   
## Siehe auch  
 [Secure Coding Guidelines](../Topic/Secure%20Coding%20Guidelines.md)   
 [Inheritance Demands](http://msdn.microsoft.com/de-de/28b9adbb-8f08-4f10-b856-dbf59eb932d9)   
 [Link Demands](../Topic/Link%20Demands.md)   
 [Daten und Modellierung](../Topic/Data%20and%20Modeling%20in%20the%20.NET%20Framework.md)
---
title: "CA2107: Verwendung von Deny und PermitOnly &#252;berpr&#252;fen | Microsoft Docs"
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
  - "CA2107"
  - "ReviewDenyAndPermitOnlyUsage"
helpviewer_keywords: 
  - "ReviewDenyAndPermitOnlyUsage"
  - "CA2107"
ms.assetid: 366f4a56-ae93-4882-81d0-bd0a55ebbc26
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2107: Verwendung von Deny und PermitOnly &#252;berpr&#252;fen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ReviewDenyAndPermitOnlyUsage|  
|CheckId|CA2107|  
|Kategorie \(Category\)|Microsoft.Security|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Eine Methode enthält eine Sicherheitsüberprüfung, welche die PermitOnly\-Sicherheitsaktion oder die Deny\-Sicherheitsaktion angibt.  
  
## Regelbeschreibung  
 Die [Using the PermitOnly Method](http://msdn.microsoft.com/de-de/8c7bdb7f-882f-45b7-908c-6cbaa1767649)\-Sicherheitsaktion und die <xref:System.Security.CodeAccessPermission.Deny%2A?displayProperty=fullName>\-Sicherheitsaktion sollten nur von Entwicklern mit sehr guten Kenntnissen der [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]\-Sicherheit verwendet werden.  Code, in dem diese Sicherheitsaktionen verwendet werden, sollte einer Sicherheitsüberprüfung unterzogen werden.  
  
 Deny ändert das Standardverhalten des Stackwalks, der als Reaktion auf eine Sicherheitsanforderung auftritt.  Es ermöglicht Ihnen die Angabe von Berechtigungen, die unabhängig von den tatsächlichen Berechtigungen der Aufrufer in der Aufrufliste während der Dauer der Deny\-Methode nicht gewährt werden dürfen.  Wenn der Stackwalk eine durch Deny gesicherte Methode erkennt und die angeforderte Berechtigung in den verweigerten Berechtigungen enthalten ist, erzeugt der Stackwalk einen Fehler.  PermitOnly ändert ebenfalls das Standardverhalten des  Stackwalks.  Durch diese Methode ist es möglich, im Code nur die Berechtigungen anzugeben, die gewährt werden können, wobei die Berechtigungen der Aufrufer nicht berücksichtigt werden.  Wenn der Stackwalk eine durch PermitOnly gesicherte Methode erkennt und die angeforderte Berechtigung nicht in den Berechtigungen enthalten ist, die mit PermitOnly angegeben werden, erzeugt der Stackwalk einen Fehler.  
  
 Code, der auf diesen Aktionen beruht, sollte wegen der begrenzten Einsatzmöglichkeiten und des komplizierten Verhaltens dieser Aktionen sorgfältig auf Sicherheitslücken überprüft werden.  Nehmen wir einmal die folgende Situation:  
  
-   [Link Demands](../Topic/Link%20Demands.md) werden durch Deny oder PermitOnly nicht beeinflusst.  
  
-   Wenn Deny oder PermitOnly in dem gleichen Stapelrahmen auftreten wie die Anforderung, die den Stackwalk auslöst, sind die Sicherheitsaktionen wirkungslos.  
  
-   Bei Werten, die zur Erstellung pfadbasierter Berechtigungen verwendet werden, gibt es in der Regel verschiedene Angabemöglichkeiten.  Durch die Verweigerung des Zugriffs auf eine Form des Pfads wird nicht der Zugriff auf alle Formen verweigert.  Wenn die Dateifreigabe \\\\Server\\Freigabe z. B. dem Netzlaufwerk X: zugeordnet ist, müssen Sie den Zugriff auf \\\\Server\\Freigabe\\Datei, X:\\Datei und alle übrigen Pfade verweigern, über die auf die Datei zugegriffen wird, um den Zugriff auf eine Datei der Freigabe zu verweigern.  
  
-   Ein <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName> kann einen Stackwalk beenden, bevor Deny oder PermitOnly erreicht wird.  
  
-   Wenn Deny eine Wirkung hat, beispielsweise wenn ein Aufrufer eine durch Deny blockierte Berechtigung besitzt, kann der Aufrufer unter Umgehung von Deny direkt auf die geschützte Ressource zugreifen.  Wenn der Aufrufer die verweigerte Berechtigung nicht besitzt, würde der Stackwalk ohne Deny dementsprechend fehlschlagen.  
  
## Behandeln von Verstößen  
 Jede Verwendung dieser Sicherheitsaktionen verursacht einen Verstoß.  Um einen Verstoß zu beheben, verwenden Sie diese Sicherheitsaktionen nicht.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie eine Warnung dieser Regel erst nach einer Sicherheitsüberprüfung.  
  
## Beispiel  
 Im folgenden Beispiel werden einige Einschränkungen von Deny veranschaulicht.  
  
 Die folgende Bibliothek enthält eine Klasse mit zwei Methoden, die bis auf die Sicherheitsanforderungen, die sie schützen, identisch sind.  
  
 [!code-cs[FxCop.Security.PermitAndDeny#1](../code-quality/codesnippet/CSharp/ca2107-review-deny-and-permit-only-usage_1.cs)]  
  
## Beispiel  
 Die folgende Anwendung veranschaulicht die Wirkungen von Deny auf die gesicherten Methoden der Bibliothek.  
  
 [!code-cs[FxCop.Security.TestPermitAndDeny#1](../code-quality/codesnippet/CSharp/ca2107-review-deny-and-permit-only-usage_2.cs)]  
  
 Folgende Ergebnisse werden zurückgegeben:  
  
  **Demand: Deny von Aufrufern hat keine Auswirkungen auf Demand mit der Assertionsberechtigung.**  
**LinkDemand: Deny von Aufrufern hat keine Auswirkungen auf LinkDemand mit der Assertionsberechtigung.**  
**LinkDemand: Deny von Aufrufern hat keine Auswirkungen auf mit LinkDemand geschütztem Code.**  
**LinkDemand: Dieser Deny hat keine Auswirkungen auf mit LinkDemand geschütztem Code.**   
## Siehe auch  
 <xref:System.Security.CodeAccessPermission.PermitOnly%2A?displayProperty=fullName>   
 <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName>   
 <xref:System.Security.CodeAccessPermission.Deny%2A?displayProperty=fullName>   
 <xref:System.Security.IStackWalk.PermitOnly%2A?displayProperty=fullName>   
 [Secure Coding Guidelines](../Topic/Secure%20Coding%20Guidelines.md)   
 [Overriding Security Checks](http://msdn.microsoft.com/de-de/4acdeff5-fc05-41bf-8505-7387cdbfca28)   
 [Using the PermitOnly Method](http://msdn.microsoft.com/de-de/8c7bdb7f-882f-45b7-908c-6cbaa1767649)
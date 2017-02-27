---
title: "CA2109: Sichtbare Ereignishandler &#252;berpr&#252;fen | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2109"
  - "ReviewVisibleEventHandlers"
helpviewer_keywords: 
  - "CA2109"
  - "ReviewVisibleEventHandlers"
ms.assetid: 8f8fa0ee-e94e-400e-b516-24d8727725d7
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 18
---
# CA2109: Sichtbare Ereignishandler &#252;berpr&#252;fen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ReviewVisibleEventHandlers|  
|CheckId|CA2109|  
|Kategorie \(Category\)|Microsoft.Security|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Eine öffentliche oder geschützte Ereignisbehandlungsmethode wurde erkannt.  
  
## Regelbeschreibung  
 Eine extern sichtbare Ereignisbehandlungsmethode stellt ein Sicherheitsproblem dar, das eine Überprüfung erfordert.  
  
 Ereignisbehandlungsmethoden sollten nur dann verfügbar gemacht werden, wenn dies absolut notwendig ist.  Ein Ereignishandler, ein Delegattyp, der die zur Verfügung gestellte Methode aufruft, kann einem beliebigen Ereignis hinzugefügt werden, solange die Signaturen des Handlers und des Ereignisses übereinstimmen.  Ereignisse können durch jeden beliebigen Code ausgelöst werden und werden häufig als Reaktion auf Benutzeraktionen wie das Klicken auf eine Schaltfläche durch hoch vertrauenswürdigen Systemcode ausgelöst.  Wenn Sie einer Ereignisbehandlungsmethode eine Sicherheitsüberprüfung hinzufügen, können Sie nicht verhindern, dass der Code einen Ereignishandler registriert, der die Methode aufruft.  
  
 Eine durch einen Ereignishandler aufgerufene Methode kann durch eine Anforderung nicht zuverlässig geschützt werden.  Sicherheitsanforderungen tragen dazu bei, Code vor nicht vertrauenswürdigen Aufrufern zu schützen, indem die in der Aufrufliste enthaltenen Aufrufer geprüft werden.  Code, mit dem einem Ereignis ein Ereignishandler hinzugefügt wird, ist nicht unbedingt zu dem Zeitpunkt in der Aufrufliste vorhanden, wenn die Methoden des Ereignishandlers ausgeführt werden.  Daher verfügt die Aufrufliste eventuell nur über hoch vertrauenswürdige Aufrufer, wenn die Ereignishandlermethode aufgerufen wird.  Dadurch verlaufen Anforderungen der Ereignishandlermethoden erfolgreich.  Zudem wird beim Aufruf der Methode möglicherweise die angeforderte Berechtigung gewährt.  Aus diesen Gründen kann das Risiko, das mit einem nicht behobenen Verstoß gegen diese Regel einhergeht, erst nach der Überprüfung der Ereignisbehandlungsmethode beurteilt werden.  Berücksichtigen Sie bei der Überprüfung des Codes folgende Punkte:  
  
-   Führt der Ereignishandler Vorgänge aus, die Risiken bergen oder ausgenutzt werden können, z. B. das Gewähren von Berechtigungen oder das Unterdrücken von Berechtigungen für nicht verwalteten Code?  
  
-   Welchen Sicherheitsrisiken ist der Code ausgesetzt und welche Sicherheitsrisiken gehen vom Code aus, wenn feststeht, dass er jederzeit nur mit hoch vertrauenswürdigen Aufrufern in der Aufrufliste ausgeführt werden kann?  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, überprüfen Sie die Methode, und stellen Sie folgende Überlegungen an:  
  
-   Können Sie die Ereignisbehandlungsmethode nichtöffentlich machen?  
  
-   Können Sie alle Funktionen aus dem Ereignishandler entfernen, die ein Risiko bergen?  
  
-   Wenn eine Sicherheitsanforderung auferlegt wird: Ist dies auch auf andere Weise möglich?  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie eine Warnung dieser Regel nur nach einer sorgfältigen Überprüfung, um sicherzustellen, dass der Code kein Sicherheitsrisiko darstellt.  
  
## Beispiel  
 Der folgende Code zeigt eine Ereignisbehandlungsmethode, die von bösartigem Code missbraucht werden kann.  
  
 [!code-cs[FxCop.Security.EventSecLib#1](../code-quality/codesnippet/CSharp/ca2109-review-visible-event-handlers_1.cs)]  
  
## Siehe auch  
 <xref:System.Security.CodeAccessPermission.Demand%2A?displayProperty=fullName>   
 <xref:System.EventArgs?displayProperty=fullName>   
 [Security Demands](http://msdn.microsoft.com/de-de/324c14f8-54ff-494d-9fd1-bfd20962c8ba)
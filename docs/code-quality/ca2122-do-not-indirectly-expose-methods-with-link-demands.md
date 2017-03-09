---
title: "CA2122: Methoden mit Linkaufrufen nicht indirekt verf&#252;gbar machen | Microsoft Docs"
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
  - "CA2122"
  - "DoNotIndirectlyExposeMethodsWithLinkDemands"
helpviewer_keywords: 
  - "CA2122"
  - "DoNotIndirectlyExposeMethodsWithLinkDemands"
ms.assetid: 3eda58e7-c6ec-41c3-8112-ae0841109c6a
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2122: Methoden mit Linkaufrufen nicht indirekt verf&#252;gbar machen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotIndirectlyExposeMethodsWithLinkDemands|  
|CheckId|CA2122|  
|Kategorie \(Category\)|Microsoft.Security|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## Ursache  
 Ein öffentlicher oder geschützter Member enthält [Link Demands](../Topic/Link%20Demands.md) und wird von einem Member aufgerufen, der keine Sicherheitsüberprüfungen ausführt.  
  
## Regelbeschreibung  
 Ein Linkaufruf überprüft nur die Berechtigungen des unmittelbaren Aufrufers.  Wenn ein Member `X` keine Sicherheitsanforderungen an seine Aufrufer stellt und Code aufruft, der durch einen Linkaufruf geschützt ist, kann ein Aufrufer ohne die notwendige Berechtigung `X` für den Zugriff auf den geschützten Member verwenden.  
  
## Behandeln von Verstößen  
 Fügen Sie dem Member gesicherten [Daten und Modellierung](../Topic/Data%20and%20Modeling%20in%20the%20.NET%20Framework.md) oder einen Linkaufruf hinzu, damit er auf den durch einen Linkaufruf geschützten Member keinen ungesicherten Zugriff mehr ermöglicht.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Um eine Warnung dieser Regel gefahrlos unterdrücken zu können, müssen Sie sicherstellen, dass der Code seinen Aufrufern keinen Zugriff auf Vorgänge oder Ressourcen gewährt, die auf destruktive Weise verwendet werden können.  
  
## Beispiel  
 In den folgenden Beispielen wird eine Bibliothek dargestellt, die gegen die Regel verstößt, sowie eine Anwendung, die die Schwachpunkte der Bibliothek aufzeigt.  Die Beispielbibliothek stellt zwei Methoden bereit, die zusammen gegen die Regel verstoßen.  Die `EnvironmentSetting`\-Methode wird durch einen Linkaufruf nach uneingeschränktem Zugriff auf Umgebungsvariablen gesichert.  Die `DomainInformation`\-Methode stellt keine Sicherheitsanforderungen an ihre Aufrufer, bevor `EnvironmentSetting` aufgerufen wird.  
  
 [!code-cs[FxCop.Security.UnsecuredDoNotCall#1](../code-quality/codesnippet/CSharp/ca2122-do-not-indirectly-expose-methods-with-link-demands_1.cs)]  
  
## Beispiel  
 Die folgende Anwendung ruft den ungesicherten Bibliotheksmember auf.  
  
 [!code-cs[FxCop.Security.TestUnsecuredDoNot1#1](../code-quality/codesnippet/CSharp/ca2122-do-not-indirectly-expose-methods-with-link-demands_2.cs)]  
  
 Folgende Ergebnisse werden zurückgegeben:  
  
  **Wert des ungesicherten Members: seattle.corp.contoso.com**   
## Siehe auch  
 [Secure Coding Guidelines](../Topic/Secure%20Coding%20Guidelines.md)   
 [Link Demands](../Topic/Link%20Demands.md)   
 [Daten und Modellierung](../Topic/Data%20and%20Modeling%20in%20the%20.NET%20Framework.md)
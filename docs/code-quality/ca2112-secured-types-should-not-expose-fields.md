---
title: "CA2112: Gesicherte Typen sollten keine Felder verf&#252;gbar machen. | Microsoft Docs"
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
  - "CA2112"
  - "SecuredTypesShouldNotExposeFields"
helpviewer_keywords: 
  - "CA2112"
  - "SecuredTypesShouldNotExposeFields"
ms.assetid: 9eb13a78-3487-49f2-81d1-3c3866db132f
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2112: Gesicherte Typen sollten keine Felder verf&#252;gbar machen.
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|SecuredTypesShouldNotExposeFields|  
|CheckId|CA2112|  
|Kategorie \(Category\)|Microsoft.Security|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Ein öffentlicher oder geschützter Typ enthält öffentliche Felder und wird durch [Link Demands](../Topic/Link%20Demands.md) gesichert.  
  
## Regelbeschreibung  
 Wenn Code auf eine Instanz eines Typs zugreifen muss, der durch einen Linkaufruf gesichert ist, muss der Code für den Zugriff auf die Felder des Typs nicht die Anforderungen des Linkaufrufs erfüllen.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, wandeln Sie die Felder in nicht\-öffentliche Felder um, und fügen Sie öffentliche Eigenschaften oder Methoden hinzu, die die Felddaten zurückgeben.  LinkDemand\-Sicherheitsüberprüfungen für Typen schützen den Zugriff auf die Eigenschaften und Methoden des Typs.  Die Codezugriffssicherheit gilt jedoch nicht für Felder.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Sowohl aufgrund der Sicherheitsaspekte und der Prinzipien für gute Entwürfe sollten Sie Verstöße beheben, indem Sie die öffentlichen Felder in nicht\-öffentliche Felder umwandeln.  Sie können eine Warnung dieser Regel unterdrücken, wenn das Feld keine Informationen enthält, die gesichert bleiben sollten und wenn Sie nicht auf den Inhalt des Felds angewiesen sind.  
  
## Beispiel  
 Das folgende Beispiel umfasst einen Bibliothekstyp \(`SecuredTypeWithFields`\) mit ungesicherten Feldern, einen Typ \(`Distributor`\), der Instanzen des Bibliothekstyps erstellen kann, und fälschlicherweise an Typen übergibt, die nicht berechtigt sind, die Instanzen zu erstellen, und Anwendungscode, der die Felder einer Instanz lesen kann, auch wenn er nicht über die Berechtigung verfügt, durch die der Typ gesichert wird.  
  
 Der folgende Bibliothekscode verstößt gegen die Regel.  
  
 [!code-cs[FxCop.Security.LinkDemandOnField#1](../code-quality/codesnippet/CSharp/ca2112-secured-types-should-not-expose-fields_1.cs)]  
  
## Beispiel  
 Die Anwendung kann wegen des Linkaufrufs, der den gesicherten Typ schützt, keine Instanz erstellen.  Die folgende Klasse gibt der Anwendung die Möglichkeit, eine Instanz des gesicherten Typs zu erhalten.  
  
 [!code-cs[FxCop.Security.LDOnFieldsDistributor#1](../code-quality/codesnippet/CSharp/ca2112-secured-types-should-not-expose-fields_2.cs)]  
  
## Beispiel  
 Die folgende Anwendung zeigt, wie Code ohne Zugriffsberechtigung für die Methoden eines gesicherten Typs auf dessen Felder zugreifen kann.  
  
 [!code-cs[FxCop.Security.TestLinkDemandOnFields#1](../code-quality/codesnippet/CSharp/ca2112-secured-types-should-not-expose-fields_3.cs)]  
  
 Folgende Ergebnisse werden zurückgegeben:  
  
  **Erstellen einer Instanz von SecuredTypeWithFields.**  
**Gesicherte Typfelder: 22, 33**  
**Ändern des Felds von gesichertem Typ...**  
**Zwischengespeicherte Objektfelder: 99, 33**   
## Verwandte Regeln  
 [CA1051: Sichtbare Instanzfelder nicht deklarieren](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)  
  
## Siehe auch  
 [Link Demands](../Topic/Link%20Demands.md)   
 [Daten und Modellierung](../Topic/Data%20and%20Modeling%20in%20the%20.NET%20Framework.md)
---
title: "CA2112: Gesicherte Typen sollten nicht verfügbar machen Felder | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2112
- SecuredTypesShouldNotExposeFields
helpviewer_keywords:
- SecuredTypesShouldNotExposeFields
- CA2112
ms.assetid: 9eb13a78-3487-49f2-81d1-3c3866db132f
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d60784b92d414b6a226605cd406378c1686529dd
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="ca2112-secured-types-should-not-expose-fields"></a>CA2112: Gesicherte Typen sollten keine Felder verfügbar machen.
|||  
|-|-|  
|TypeName|SecuredTypesShouldNotExposeFields|  
|CheckId|CA2112|  
|Kategorie|Microsoft.Security|  
|Unterbrechende Änderung|Breaking|  
  
## <a name="cause"></a>Ursache  
 Ein öffentlicher oder geschützter Typ enthält öffentliche Felder und wird durch gesichert eine [Verknüpfungsaufrufe](/dotnet/framework/misc/link-demands).  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Wenn Code auf eine Instanz eines Typs zugreifen muss, der durch einen Linkaufruf gesichert ist, muss der Code für den Zugriff auf die Felder des Typs nicht die Anforderungen des Linkaufrufs erfüllen.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, legen Sie die Felder nicht öffentliche und Hinzufügen von öffentlichen Eigenschaften oder Methoden, die die Felddaten zurückgeben. LinkDemand sicherheitsüberprüfungen Typen schützen Sie den Zugriff auf Eigenschaften und Methoden des Typs. Codezugriffssicherheit gilt jedoch nicht für Felder.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Sowohl auf Sicherheitsprobleme und guten Entwurf sollten Sie die Verstöße, indem Sie die öffentliche Felder Nonpublic machen reparieren. Sie können eine Warnung dieser Regel unterdrücken, wenn das Feld nicht gesichert bleiben sollten Informationen enthalten, und Sie verlassen Sie sich nicht auf den Inhalt des Felds.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel besteht aus einem Bibliothekstyp (`SecuredTypeWithFields`) mit unsicheren Feldern, einen Typ (`Distributor`), die Instanzen der Typ der Bibliothek erstellen und falsche übergibt Instanzen Typen verfügen nicht über die Berechtigung zu ihrer Erstellung und Programmierung Anwendung, die kann eine Instanz Lesen von Feldern, obwohl er nicht über die Berechtigung verfügt, die den Typ sichert.  
  
 Die folgenden Bibliothekscode verstößt gegen die Regel.  
  
 [!code-csharp[FxCop.Security.LinkDemandOnField#1](../code-quality/codesnippet/CSharp/ca2112-secured-types-should-not-expose-fields_1.cs)]  
  
## <a name="example"></a>Beispiel  
 Die Anwendung kann nicht aufgrund der Linkaufruf, der den gesicherten Typ schützt, eine Instanz erstellen. Die folgende Klasse ermöglicht der Anwendung auf eine Instanz des gesicherten Typs zu erhalten.  
  
 [!code-csharp[FxCop.Security.LDOnFieldsDistributor#1](../code-quality/codesnippet/CSharp/ca2112-secured-types-should-not-expose-fields_2.cs)]  
  
## <a name="example"></a>Beispiel  
 Die folgende Anwendung dargestellt, wie, ohne Berechtigungen für den Zugriff auf einen sicheren Typ Methoden, Code ihre Felder zugreifen kann.  
  
 [!code-csharp[FxCop.Security.TestLinkDemandOnFields#1](../code-quality/codesnippet/CSharp/ca2112-secured-types-should-not-expose-fields_3.cs)]  
  
 Folgende Ergebnisse werden zurückgegeben:  
  
 **Erstellen einer Instanz von SecuredTypeWithFields an.**  
**Gesicherte Typfelder: 22, 33**  
**Gesicherte Type-Feld wird geändert...**  
**Objektfelder zwischengespeichert: 99, 33**   
## <a name="related-rules"></a>Verwandte Regeln  
 [CA1051: Sichtbare Instanzfelder nicht deklarieren](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Verknüpfungsaufrufe](/dotnet/framework/misc/link-demands)   
 [Daten und Modellierung](/dotnet/framework/data/index)
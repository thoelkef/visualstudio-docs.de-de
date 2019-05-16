---
title: 'CA2112: Gesicherte Typen sollten keine Felder verfügbar | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2112
- SecuredTypesShouldNotExposeFields
helpviewer_keywords:
- SecuredTypesShouldNotExposeFields
- CA2112
ms.assetid: 9eb13a78-3487-49f2-81d1-3c3866db132f
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 17a52b952437ce136773d796972c6619a9733749
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "65687324"
---
# <a name="ca2112-secured-types-should-not-expose-fields"></a>CA2112: Gesicherte Typen sollten keine Felder verfügbar machen.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|SecuredTypesShouldNotExposeFields|
|CheckId|CA2112|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein öffentlicher oder geschützter Typ enthält öffentliche Felder und wird geschützt, indem eine [Verknüpfungsaufrufe](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d).

## <a name="rule-description"></a>Regelbeschreibung
 Wenn Code auf eine Instanz eines Typs zugreifen muss, der durch einen Linkaufruf gesichert ist, muss der Code für den Zugriff auf die Felder des Typs nicht die Anforderungen des Linkaufrufs erfüllen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, legen Sie die Felder als nicht öffentlich, und fügen Sie öffentliche Eigenschaften oder Methoden, die die Felddaten zurückgeben. LinkDemand-sicherheitsüberprüfungen für Typen Schützen des Zugriffs auf die Eigenschaften und Methoden des Typs. Codezugriffssicherheit gilt jedoch nicht auf Felder.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Für Sicherheitsprobleme und ein guter Entwurf sollten Sie Regelverstöße beheben, dazu nicht öffentlichen öffentliche Felder. Sie können eine Warnung dieser Regel unterdrücken, wenn das Feld keine Informationen enthält, die gesichert bleiben soll, und Sie verlassen sich nicht auf den Inhalt des Felds.

## <a name="example"></a>Beispiel
 Im folgende Beispiel besteht aus einem Typ "Klassenbibliothek" (`SecuredTypeWithFields`) für unsichere Felder, die einen Typ (`Distributor`), die Instanzen des Typs Bibliothek erstellen, falsche übergibt-Instanzen, um Typen sind nicht berechtigt, diese zu erstellen und Anwendungscode, der können eine Instanz der Felder zu lesen, obwohl sie nicht über die Berechtigung verfügt, die den Typ sichert.

 Der folgende Bibliothekscode verstößt gegen die Regel.

 [!code-csharp[FxCop.Security.LinkDemandOnField#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.LinkDemandOnField/cs/FxCop.Security.LinkDemandOnField.cs#1)]

## <a name="example"></a>Beispiel
 Die Anwendung kann nicht aufgrund der Linkaufruf, der den gesicherten Typ schützt, eine Instanz erstellen. Die folgende Klasse ermöglicht die Anwendung um eine Instanz des gesicherten Typs abzurufen.

 [!code-csharp[FxCop.Security.LDOnFieldsDistributor#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.LDOnFieldsDistributor/cs/FxCop.Security.LDOnFieldsDistributor.cs#1)]

## <a name="example"></a>Beispiel
 Die folgende Anwendung dargestellt, ohne Berechtigungen für den Zugriff auf eine gesicherte Typ-Methoden, Code die Felder zugreifen kann.

 [!code-csharp[FxCop.Security.TestLinkDemandOnFields#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestLinkDemandOnFields/cs/FxCop.Security.TestLinkDemandOnFields.cs#1)]

 Folgende Ergebnisse werden zurückgegeben:

 **Erstellen einer Instanz von SecuredTypeWithFields. ** 
 **Gesichertes-Feldern: 22, 33**
**gesicherte Typ-Feld ändern... ** 
 **Objektfelder zwischengespeichert: 99, 33**
## <a name="related-rules"></a>Verwandte Regeln
 [CA1051: Sichtbare Instanzfelder nicht deklarieren](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)

## <a name="see-also"></a>Siehe auch
 [Linkaufrufe](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) [Daten und Modellierung](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)

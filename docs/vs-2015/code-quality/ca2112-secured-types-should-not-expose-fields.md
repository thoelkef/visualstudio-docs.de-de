---
title: 'CA2112: gesicherte Typen sollten keine Felder verfügbar machen | Microsoft-Dokumentation'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 4267b4f55f78106a4d1e8f3b2f9b296be9ddf618
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546535"
---
# <a name="ca2112-secured-types-should-not-expose-fields"></a>CA2112: Gesicherte Typen sollten keine Felder verfügbar machen.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wert|
|-|-|
|TypName|SecuredTypesShouldNotExposeFields|
|CheckId|CA2112|
|Category|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein öffentlicher oder geschützter Typ enthält öffentliche Felder und wird durch einen [Link](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d)Aufruf gesichert.

## <a name="rule-description"></a>Beschreibung der Regel
 Wenn Code auf eine Instanz eines Typs zugreifen muss, der durch einen Linkaufruf gesichert ist, muss der Code für den Zugriff auf die Felder des Typs nicht die Anforderungen des Linkaufrufs erfüllen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, legen Sie die Felder als nicht öffentlich fest, und fügen Sie öffentliche Eigenschaften oder Methoden hinzu, die die Felddaten zurückgeben. LinkDemand-Sicherheitsüberprüfungen für Typen schützen den Zugriff auf die Eigenschaften und Methoden des Typs. Die Code Zugriffssicherheit gilt jedoch nicht für Felder.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Sowohl für Sicherheitsprobleme als auch für einen guten Entwurf sollten Verstöße behoben werden, indem die öffentlichen Felder nicht öffentlich gemacht werden. Sie können eine Warnung aus dieser Regel unterdrücken, wenn das Feld keine Informationen enthält, die geschützt bleiben sollen, und Sie sich nicht auf den Inhalt des Felds verlassen.

## <a name="example"></a>Beispiel
 Das folgende Beispiel besteht aus einem Bibliothekstyp ( `SecuredTypeWithFields` ) mit ungesicherten Feldern, einem Typ (), der `Distributor` Instanzen des Bibliotheks Typs erstellen kann, und irrtümlich übergibt Instanzen an Typen keine Berechtigung zum Erstellen dieser Felder und Anwendungscode, der die Felder einer Instanz lesen kann, auch wenn Sie nicht über die Berechtigung zum Sichern des Typs verfügt.

 Der folgende Bibliotheks Code verstößt gegen die Regel.

 [!code-csharp[FxCop.Security.LinkDemandOnField#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.LinkDemandOnField/cs/FxCop.Security.LinkDemandOnField.cs#1)]

## <a name="example"></a>Beispiel
 Die Anwendung kann aufgrund des Link Aufrufs, der den gesicherten Typ schützt, keine Instanz erstellen. Mit der folgenden Klasse kann die Anwendung eine Instanz des gesicherten Typs abrufen.

 [!code-csharp[FxCop.Security.LDOnFieldsDistributor#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.LDOnFieldsDistributor/cs/FxCop.Security.LDOnFieldsDistributor.cs#1)]

## <a name="example"></a>Beispiel
 Die folgende Anwendung veranschaulicht, wie der Code ohne Berechtigung für den Zugriff auf die Methoden eines gesicherten Typs auf seine Felder zugreifen kann.

 [!code-csharp[FxCop.Security.TestLinkDemandOnFields#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestLinkDemandOnFields/cs/FxCop.Security.TestLinkDemandOnFields.cs#1)]

 Folgende Ergebnisse werden zurückgegeben:

 **Erstellen einer Instanz von SecuredTypeWithFields.** 
 **Felder mit sichertem Typ: 22, 33** 
 **Feld des gesicherten Typs wird geändert...** 
 **Zwischengespeicherte Objekt Felder: 99, 33**
## <a name="related-rules"></a>Verwandte Regeln
 [CA1051: Sichtbare Instanzfelder nicht deklarieren.](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)

## <a name="see-also"></a>Weitere Informationen
 [Verknüpfen](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) von Anforderungs [Daten und Modellierung](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)

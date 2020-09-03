---
title: 'CA1402: über Ladungen in für COM sichtbaren Schnittstellen vermeiden | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidOverloadsInComVisibleInterfaces
- CA1402
helpviewer_keywords:
- AvoidOverloadsInComVisibleInterfaces
- CA1402
ms.assetid: 2724c1f9-d5d3-4704-b124-21c4d398e5df
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: b5c1e3af0e35bf92d72e853948c455893b417998
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85534939"
---
# <a name="ca1402-avoid-overloads-in-com-visible-interfaces"></a>CA1402: Überladungen in für COM sichtbaren Schnittstellen vermeiden.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|value|
|-|-|
|TypName|AvoidOverloadsInComVisibleInterfaces|
|CheckId|CA1402|
|Category|Microsoft. Interoperabilität|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Eine Component Object Model (com) sichtbare Schnittstelle deklariert überladene Methoden.

## <a name="rule-description"></a>Beschreibung der Regel
 Wenn für COM-Clients überladene Methoden verfügbar gemacht werden, behält nur die erste Methodenüberladung ihren Namen. Nachfolgende über Ladungen werden eindeutig umbenannt, indem an den Namen ein Unterstrich "_" angehängt wird, und eine ganze Zahl, die der Reihenfolge der Deklaration der Überladung entspricht. Beachten Sie z. b. die folgenden Methoden.

```
void SomeMethod(int valueOne);
void SomeMethod(int valueOne, int valueTwo, int valueThree);
void SomeMethod(int valueOne, int valueTwo);
```

 Diese Methoden werden für com-Clients wie folgt verfügbar gemacht.

```
void SomeMethod(int valueOne);
void SomeMethod_2(int valueOne, int valueTwo, int valueThree);
void SomeMethod_3(int valueOne, int valueTwo);
```

 Visual Basic 6 com-Clients können keine Schnittstellen Methoden implementieren, indem Sie einen Unterstrich im Namen verwenden.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, benennen Sie die überladenen Methoden so um, dass die Namen eindeutig sind. Alternativ können Sie die Schnittstelle für COM unsichtbar machen, indem Sie den Zugriff auf `internal` ( `Friend` in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ) ändern oder indem Sie das- <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> Attribut auf festlegen `false` .

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt eine Schnittstelle, die gegen die Regel verstößt, und eine Schnittstelle, die die Regel erfüllt.

 [!code-csharp[FxCop.Interoperability.OverloadsInterface#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.OverloadsInterface/cs/FxCop.Interoperability.OverloadsInterface.cs#1)]
 [!code-vb[FxCop.Interoperability.OverloadsInterface#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.OverloadsInterface/vb/FxCop.Interoperability.OverloadsInterface.vb#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1413: Nicht öffentliche Felder in für COM sichtbaren Werttypen vermeiden.](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)

 [CA1407: Statische Member in für COM sichtbaren Typen vermeiden.](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)

 [CA1017: Assemblys mit ComVisibleAttribute markieren.](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>Weitere Informationen
 Interoperabilität mit [Long-Datentyp](https://msdn.microsoft.com/library/b4770c34-1804-4f8c-b512-c10b0893e516) [von nicht verwaltetem Code](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)

---
title: 'CA1402: Überladungen in für COM sichtbaren Schnittstellen vermeiden | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- AvoidOverloadsInComVisibleInterfaces
- CA1402
helpviewer_keywords:
- AvoidOverloadsInComVisibleInterfaces
- CA1402
ms.assetid: 2724c1f9-d5d3-4704-b124-21c4d398e5df
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: ece9a444ac308003c56da1bd4f2ecf4433e2b4a9
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2018
ms.locfileid: "47589199"
---
# <a name="ca1402-avoid-overloads-in-com-visible-interfaces"></a>CA1402: Überladungen in für COM sichtbaren Schnittstellen vermeiden
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [CA1402: Überladungen in für COM sichtbaren Schnittstellen vermeiden](https://docs.microsoft.com/visualstudio/code-quality/ca1402-avoid-overloads-in-com-visible-interfaces).

|||
|-|-|
|TypeName|AvoidOverloadsInComVisibleInterfaces|
|CheckId|CA1402|
|Kategorie|Microsoft.Interoperability|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Einem Component Object Model (COM) Schnittstelle deklariert überladener Methoden.

## <a name="rule-description"></a>Regelbeschreibung
 Wenn für COM-Clients überladene Methoden verfügbar gemacht werden, behält nur die erste Methodenüberladung ihren Namen. Nachfolgende Überladungen werden eindeutig umbenannt, indem Sie auf den Namen anfügen, einen Unterstrich "_" und eine ganze Zahl, die Reihenfolge der Deklaration der Überladung entspricht. Betrachten Sie beispielsweise die folgenden Methoden aus.

```
void SomeMethod(int valueOne);
void SomeMethod(int valueOne, int valueTwo, int valueThree);
void SomeMethod(int valueOne, int valueTwo);
```

 Diese Methoden werden für COM-Clients wie folgt verfügbar gemacht.

```
void SomeMethod(int valueOne);
void SomeMethod_2(int valueOne, int valueTwo, int valueThree);
void SomeMethod_3(int valueOne, int valueTwo);
```

 Visual Basic 6-COM-Clients können keine Schnittstellenmethoden implementieren, mit einem Unterstrich im Namen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, benennen Sie die überladenen Methoden, sodass die Namen eindeutig sind. Sie können auch die Schnittstelle für COM sichtbar machen durch Ändern der Zugriff auf `internal` (`Friend` in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) oder durch Anwenden der <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> -Attributsatz auf `false`.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt eine Schnittstelle, die gegen die Regel verstößt und eine Schnittstelle, die die Regel erfüllt.

 [!code-csharp[FxCop.Interoperability.OverloadsInterface#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.OverloadsInterface/cs/FxCop.Interoperability.OverloadsInterface.cs#1)]
 [!code-vb[FxCop.Interoperability.OverloadsInterface#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.OverloadsInterface/vb/FxCop.Interoperability.OverloadsInterface.vb#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1413: Nicht öffentliche Felder in für COM sichtbaren Werttypen vermeiden](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)

 [CA1407: Statische Member in für COM sichtbaren Typen vermeiden](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)

 [CA1017: Assemblys mit ComVisibleAttribute markieren](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>Siehe auch
 [Interoperation mit nicht verwaltetem Code](http://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258) [Long-Datentyp](http://msdn.microsoft.com/library/b4770c34-1804-4f8c-b512-c10b0893e516)




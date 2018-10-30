---
title: 'CA1051: Sichtbare Instanzfelder nicht deklarieren'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1051
- DoNotDeclareVisibleInstanceFields
helpviewer_keywords:
- CA1051
- DoNotDeclareVisibleInstanceFields
ms.assetid: 2805376c-824c-462c-81d1-c51aaf7cabe7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f907b1d8626e8babc88137ed70cf6330386ab92a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49832198"
---
# <a name="ca1051-do-not-declare-visible-instance-fields"></a>CA1051: Sichtbare Instanzfelder nicht deklarieren

|||
|-|-|
|TypeName|DoNotDeclareVisibleInstanceFields|
|CheckId|CA1051|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein extern sichtbarer Typ verfügt über eine extern sichtbare Instanzfeld.

## <a name="rule-description"></a>Regelbeschreibung
 Ein Feld sollte primär als Implementierungsdetail verwendet werden. Felder sollten sein `private` oder `internal` und mithilfe von Eigenschaften verfügbar gemacht werden. Es ist einfach, eine Eigenschaft zuzugreifen, wie es ist, Zugriff auf ein Feld aus, und der Code in die Zugriffsmethoden einer Eigenschaft ändern kann, wie die Funktionen des Typs erweitern, ohne wichtige Änderungen. Führen Sie mit Zugriff auf ein Feld sind Eigenschaften, die nur den Wert des einem privaten oder internen Feld zurückgeben optimiert; nur sehr wenig Leistungsgewinn bezieht sich auf die Verwendung von extern sichtbaren Feldern Eigenschaften zur Verfügung.

 Bezieht sich auf die extern sichtbaren `public`, `protected`, und `protected internal` (`Public`, `Protected`, und `Protected Friend` in Visual Basic) Zugriffsebenen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, stellen Sie das Feld `private` oder `internal` und machen ihn mit einer extern sichtbaren Eigenschaft verfügbar.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Unterdrücken Sie keine Warnung dieser Regel. Extern sichtbare Feldern bieten keine Vorteile, die für die Eigenschaften nicht verfügbar sind. Darüber hinaus können nicht öffentlichen Felder geschützt werden, indem [Verknüpfungsaufrufe](/dotnet/framework/misc/link-demands). Finden Sie unter [CA2112: gesicherte Typen sollten keine Felder verfügbar](../code-quality/ca2112-secured-types-should-not-expose-fields.md).

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt einen Typ (`BadPublicInstanceFields`), die gegen diese Regel verstößt. `GoodPublicInstanceFields` Zeigt den korrigierten Code.

 [!code-csharp[FxCop.Design.TypesPublicInstanceFields#1](../code-quality/codesnippet/CSharp/ca1051-do-not-declare-visible-instance-fields_1.cs)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA2112: Gesicherte Typen sollten keine Felder verfügbar machen](../code-quality/ca2112-secured-types-should-not-expose-fields.md)

## <a name="see-also"></a>Siehe auch
 [Verknüpfungsaufrufe](/dotnet/framework/misc/link-demands)
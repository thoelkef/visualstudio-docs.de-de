---
title: 'CA1051: Sichtbare Instanzfelder nicht deklarieren.'
ms.date: 03/11/2019
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 455ab619f293981c5ebd3afba6336c63f2fe7f49
ms.sourcegitcommit: 0f44ec8ba0263056ad04d2d0dc904ad4206ce8fc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/06/2019
ms.locfileid: "70766056"
---
# <a name="ca1051-do-not-declare-visible-instance-fields"></a>CA1051: Sichtbare Instanzfelder nicht deklarieren.

|||
|-|-|
|TypeName|DoNotDeclareVisibleInstanceFields|
|CheckId|CA1051|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache

Ein Typ verfügt über ein nicht privates Instanzfeld.

Standardmäßig betrachtet diese Regel nur extern sichtbare Typen, aber dies ist [konfigurierbar](#configurability).

## <a name="rule-description"></a>Regelbeschreibung

Ein Feld sollte primär als Implementierungsdetail verwendet werden. Felder müssen oder `private` `internal` sein und sollten mithilfe von Eigenschaften verfügbar gemacht werden. Es ist so einfach, auf eine Eigenschaft zuzugreifen, da Sie auf ein Feld zugreifen kann. der Code in den Accessoren einer Eigenschaft kann sich ändern, wenn die Funktionen des Typs ohne wichtige Änderungen erweitert werden.

Eigenschaften, die nur den Wert eines privaten oder internen Felds zurückgeben, werden für die Ausführung mit dem Zugriff auf ein Feld optimiert. der Leistungsgewinn bei der Verwendung extern sichtbarer Felder anstelle von Eigenschaften ist minimal. *Extern sichtbar* bezieht sich `public`auf `protected`die Zugriffs `protected internal` Ebenen`Public`, `Protected`und ( `Protected Friend` , und in Visual Basic).

Darüber hinaus können öffentliche Felder nicht durch [Link](/dotnet/framework/misc/link-demands)Aufrufe geschützt werden. Weitere Informationen finden [Sie unter CA2112: Gesicherte Typen sollten keine Felder](../code-quality/ca2112-secured-types-should-not-expose-fields.md)verfügbar machen. (Link Aufrufe sind nicht auf .net Core-apps anwendbar.)

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, machen Sie `private` das `internal` Feld oder, und machen Sie es mithilfe einer extern sichtbaren Eigenschaft verfügbar.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?

Unterdrücken Sie diese Warnung nur, wenn Sie sicher sind, dass Consumer direkten Zugriff auf das Feld benötigen. Bei den meisten Anwendungen bieten verfügbar gemachte Felder keine Leistungs-oder wart barkeits Vorteile gegenüber Eigenschaften.

Consumer benötigen in den folgenden Situationen möglicherweise Feld Zugriff:

- in ASP.net-Web Forms Inhalts Steuerelementen
- Wenn die Zielplattform verwendet `ref` , um Felder zu ändern, wie z. b. Model-View-ViewModel (MVVM)-Frameworks für WPF und UWP

## <a name="configurability"></a>Konfigurierbarkeit

Wenn Sie diese Regel von [FxCop](install-fxcop-analyzers.md) Analyzer (und nicht mit der Legacy Analyse) ausführen, können Sie basierend auf ihrer Barrierefreiheit konfigurieren, für welche Teile Ihrer Codebasis diese Regel ausgeführt werden soll. Um z. b. anzugeben, dass die Regel nur für die nicht öffentliche API-Oberfläche ausgeführt werden soll, fügen Sie das folgende Schlüssel-Wert-Paar in eine Editor config-Datei in Ihrem Projekt ein:

```ini
dotnet_code_quality.ca1051.api_surface = private, internal
```

Sie können diese Option nur für diese Regel, für alle Regeln oder für alle Regeln in dieser Kategorie (Entwurf) konfigurieren. Weitere Informationen finden Sie unter [Konfigurieren von FxCop-Analysen](configure-fxcop-analyzers.md).

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt einen-Typ`BadPublicInstanceFields`(), der gegen diese Regel verstößt. `GoodPublicInstanceFields`zeigt den korrigierten Code an.

[!code-csharp[FxCop.Design.TypesPublicInstanceFields#1](../code-quality/codesnippet/CSharp/ca1051-do-not-declare-visible-instance-fields_1.cs)]

## <a name="related-rules"></a>Verwandte Regeln

- [CA2112: Gesicherte Typen sollten keine Felder verfügbar machen.](../code-quality/ca2112-secured-types-should-not-expose-fields.md)

## <a name="see-also"></a>Siehe auch

- [Link Aufrufe](/dotnet/framework/misc/link-demands)

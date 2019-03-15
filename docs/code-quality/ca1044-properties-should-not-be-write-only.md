---
title: 'CA1044: Eigenschaften sollten nicht lesegeschützt sein.'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- PropertiesShouldNotBeWriteOnly
- CA1044
helpviewer_keywords:
- CA1044
- PropertiesShouldNotBeWriteOnly
ms.assetid: 8386bf3a-b161-4841-bf8b-92591595aea9
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 374bc4e9252dc07bde1f056aaf542811953fd69d
ms.sourcegitcommit: f7c401a376ce410336846835332a693e6159c551
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/14/2019
ms.locfileid: "57868187"
---
# <a name="ca1044-properties-should-not-be-write-only"></a>CA1044: Eigenschaften sollten nicht lesegeschützt sein.

|||
|-|-|
|TypeName|PropertiesShouldNotBeWriteOnly|
|CheckId|CA1044|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache

Eine Eigenschaft verfügt über einen Set-Accessor, jedoch nicht mit einem Get-Accessor.

Diese Regel nur sucht standardmäßig an öffentliche Typen, aber dies ist [konfigurierbare](#configurability).

## <a name="rule-description"></a>Regelbeschreibung

Erhalten bieten Sie Accessoren Lesezugriff auf eine Eigenschaft und gewähren Sie Set-Zugriffsmethoden Schreibzugriff. Obwohl eine schreibgeschützte Eigenschaft akzeptabel und oft erforderlich ist, verhindern die Entwurfsrichtlinien die Verwendung von Eigenschaften, die nur geschrieben werden können. Dies ist, da einen Benutzer einen Wert festlegen zu lassen, und klicken Sie dann verhindert, dass des Benutzers anzeigen des Werts wird keine Sicherheit geboten. Außerdem kann der Zustand freigegebener Objekte ohne Lesezugriff nicht angezeigt werden, wodurch ihre Nützlichkeit eingeschränkt wird.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, fügen Sie einen Get-Accessor der Eigenschaft ein. Auch wenn das Verhalten einer nur-Schreiben-Eigenschaft erforderlich ist, sollten Sie konvertieren diese Eigenschaft in eine Methode.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken

Es wird empfohlen, Sie keine Warnungen, die von dieser Regel unterdrücken.

## <a name="configurability"></a>Konfigurierbarkeit

Wenn Sie diese Regel aus ausführen, [FxCop-Analysen](install-fxcop-analyzers.md) (und nicht über die Analyse von statischem Code), können Sie konfigurieren, welche Teile Ihrer Codebasis, um die Ausführung dieser Regel auf, um basierend auf deren Barrierefreiheit. Z. B. um anzugeben, dass die Regel nur für die nicht öffentlichen API-Oberfläche ausgeführt werden soll, fügen Sie die folgenden Schlüssel-Wert-Paar in einer editorconfig-Datei in Ihrem Projekt:

```
dotnet_code_quality.ca1044.api_surface = private, internal
```

Sie können diese Option, die für diese eine Regel, für alle Regeln oder für alle Regeln in dieser Kategorie (Entwurf) konfigurieren. Weitere Informationen finden Sie unter [konfigurieren FxCop-Analysetools](configure-fxcop-analyzers.md).

## <a name="example"></a>Beispiel

Im folgenden Beispiel `BadClassWithWriteOnlyProperty` ist ein Typ mit einer nur-Schreiben-Eigenschaft. `GoodClassWithReadWriteProperty` enthält den korrigierten Code.

[!code-vb[FxCop.Design.PropertiesNotWriteOnly#1](../code-quality/codesnippet/VisualBasic/ca1044-properties-should-not-be-write-only_1.vb)]
[!code-csharp[FxCop.Design.PropertiesNotWriteOnly#1](../code-quality/codesnippet/CSharp/ca1044-properties-should-not-be-write-only_1.cs)]
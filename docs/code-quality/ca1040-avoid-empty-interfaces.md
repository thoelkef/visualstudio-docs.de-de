---
title: 'CA1040: Leere Schnittstellen vermeiden.'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1040
- AvoidEmptyInterfaces
helpviewer_keywords:
- AvoidEmptyInterfaces
- CA1040
ms.assetid: 120a741b-5fd1-4836-8453-7857e0cd0380
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 25e798dac05213d8f66fe7ba3c7a737a71f6030e
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2019
ms.locfileid: "65842240"
---
# <a name="ca1040-avoid-empty-interfaces"></a>CA1040: Leere Schnittstellen vermeiden.

|||
|-|-|
|TypeName|AvoidEmptyInterfaces|
|CheckId|CA1040|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache

Die Schnittstelle keine Member deklarieren oder zwei oder mehr Schnittstellen implementieren.

Diese Regel nur sucht standardmäßig an extern sichtbare Schnittstellen. Dies ist jedoch [konfigurierbare](#configurability).

## <a name="rule-description"></a>Regelbeschreibung

Schnittstellen definieren Member, die ein Verhalten oder einen Verwendungsvertrag bereitstellen. Die durch die Schnittstelle beschriebene Funktionalität kann von jedem Typ übernommen werden, unabhängig davon, an welcher Stelle der Typ in der Vererbungshierarchie steht. Ein Typ implementiert eine Schnittstelle, indem er Implementierungen für die Member der Schnittstelle bereitstellt. Eine leere Schnittstelle definiert keine Member. Aus diesem Grund ist es keinen Vertrag zu definieren, der implementiert werden können.

Wenn es sich bei Ihrem Entwurf leerer enthält Schnittstellen, die Typen implementieren sollen, verwenden Sie wahrscheinlich eine Schnittstelle als eine Markierung oder eine Möglichkeit, eine Gruppe von Typen zu identifizieren. Diese Identifikation zur Laufzeit erfolgt, ist die richtige Vorgehensweise zu diesem Zweck ein benutzerdefiniertes Attribut zu verwenden. Verwenden Sie das Vorhandensein oder Abwesenheit des Attributs, oder die Eigenschaften des Attributs, um die Zieltypen zu identifizieren. Wenn die ID zum Zeitpunkt der Kompilierung erfolgen muss, ist es akzeptabel, eine leere Schnittstelle verwenden.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Entfernen Sie die Schnittstelle, oder fügen Sie Mitglieder hinzu. Wenn die leere Schnittstelle zum Bezeichnen eines Satz von Typen verwendet wird, ersetzen Sie die Schnittstelle mit einem benutzerdefinierten Attribut.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken

Es ist sicher, unterdrücken Sie eine Warnung dieser Regel aus, wenn die Schnittstelle verwendet wird, um einen Satz von Typen zum Zeitpunkt der Kompilierung zu identifizieren.

## <a name="configurability"></a>Konfigurierbarkeit

Wenn Sie diese Regel aus ausführen, [FxCop-Analysen](install-fxcop-analyzers.md) (und nicht über die Analyse von statischem Code), können Sie konfigurieren, welche Teile Ihrer Codebasis, um die Ausführung dieser Regel auf, um basierend auf deren Barrierefreiheit. Z. B. um anzugeben, dass die Regel nur für die nicht öffentlichen API-Oberfläche ausgeführt werden soll, fügen Sie die folgenden Schlüssel-Wert-Paar in einer editorconfig-Datei in Ihrem Projekt:

```ini
dotnet_code_quality.ca1040.api_surface = private, internal
```

Sie können diese Option, die für diese eine Regel, für alle Regeln oder für alle Regeln in dieser Kategorie (Entwurf) konfigurieren. Weitere Informationen finden Sie unter [konfigurieren FxCop-Analysetools](configure-fxcop-analyzers.md).

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt eine leere Schnittstelle.

[!code-csharp[FxCop.Design.InterfacesNotEmpty#1](../code-quality/codesnippet/CSharp/ca1040-avoid-empty-interfaces_1.cs)]
[!code-cpp[FxCop.Design.InterfacesNotEmpty#1](../code-quality/codesnippet/CPP/ca1040-avoid-empty-interfaces_1.cpp)]
[!code-vb[FxCop.Design.InterfacesNotEmpty#1](../code-quality/codesnippet/VisualBasic/ca1040-avoid-empty-interfaces_1.vb)]
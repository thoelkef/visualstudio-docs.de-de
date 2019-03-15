---
title: 'CA1030: Nach Möglichkeit Ereignisse verwenden.'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- UseEventsWhereAppropriate
- CA1030
helpviewer_keywords:
- CA1030
- UseEventsWhereAppropriate
ms.assetid: ea051367-deeb-40f9-9b65-eb818f1e133a
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1054fa7b884c23edb76248cba17bab41cc64246f
ms.sourcegitcommit: f7c401a376ce410336846835332a693e6159c551
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/14/2019
ms.locfileid: "57867431"
---
# <a name="ca1030-use-events-where-appropriate"></a>CA1030: Nach Möglichkeit Ereignisse verwenden.

|||
|-|-|
|TypeName|UseEventsWhereAppropriate|
|CheckId|CA1030|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache

Namen einer Methode beginnt mit einer der folgenden:

- AddOn
- RemoveOn
- Auslösen
- Auslösen

Diese Regel nur sucht standardmäßig an extern sichtbare Methoden, dies ist jedoch [konfigurierbare](#configurability).

## <a name="rule-description"></a>Regelbeschreibung

Diese Regel erkennt Methoden, deren Namen normalerweise für Ereignisse verwendet würden. Ereignisse befolgen das Entwurfsmuster "Beobachter" oder "Veröffentlichen-Abonnieren"; Sie werden verwendet, wenn eine Zustandsänderung bei einem Objekt auf andere Objekte übertragen werden muss. Wenn eine Methode als Reaktion auf eine klar definierte Zustandsänderung hin aufgerufen wird, sollte die Methode von einem Ereignishandler aufgerufen werden. Objekte, die die Methode aufrufen, sollten Ereignisse auslösen, statt die Methode direkt aufzurufen.

Einige allgemeine Beispiele für Ereignisse werden in Benutzeroberflächenanwendungen gefunden, in denen eine Benutzeraktion wie das Klicken auf eine Schaltfläche führt dazu, ein Segment des Codes dass ausgeführt. Das Ereignismodell für die .NET Framework ist nicht auf Benutzeroberflächen beschränkt; Sie sollten überall dort verwendet werden, mit denen Sie kommunizieren müssen, dass Zustandsänderungen auf eine oder mehrere Objekte.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Wenn die Methode aufgerufen wird, wenn sich der Zustand eines Objekts ändert, sollten Sie den Entwurf ändern, verwenden Sie das Ereignismodell für .NET.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken

Unterdrücken Sie eine Warnung dieser Regel, wenn die Methode nicht mit dem .NET Ereignismodell funktioniert.

## <a name="configurability"></a>Konfigurierbarkeit

Wenn Sie diese Regel aus ausführen, [FxCop-Analysen](install-fxcop-analyzers.md) (und nicht über die Analyse von statischem Code), können Sie konfigurieren, welche Teile Ihrer Codebasis, um die Ausführung dieser Regel auf, um basierend auf deren Barrierefreiheit. Z. B. um anzugeben, dass die Regel nur für die nicht öffentlichen API-Oberfläche ausgeführt werden soll, fügen Sie die folgenden Schlüssel-Wert-Paar in einer editorconfig-Datei in Ihrem Projekt:

```
dotnet_code_quality.ca1030.api_surface = private, internal
```

Sie können diese Option, die für diese eine Regel, für alle Regeln oder für alle Regeln in dieser Kategorie (Entwurf) konfigurieren. Weitere Informationen finden Sie unter [konfigurieren FxCop-Analysetools](configure-fxcop-analyzers.md).
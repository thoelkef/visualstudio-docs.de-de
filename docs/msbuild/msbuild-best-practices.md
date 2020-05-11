---
title: Best Practices für MSBuild | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- best practices, MSBuild
- MSBuild, best practices
ms.assetid: 90ef8693-e921-410a-a377-fe4d13f58c48
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 91b2e157ee64f5e4d91bc75a5d6f8d65d4312862
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/18/2020
ms.locfileid: "78263148"
---
# <a name="msbuild-best-practices"></a>Best Practices für MSBuild

Es werden die folgenden bewährten Methoden zum Schreiben von MSBuild-Skripts empfohlen:

- Standardwerte für Eigenschaften werden am besten mit dem `Condition`-Attribut verarbeitet und nicht durch Deklarieren einer Eigenschaft, deren Standardwert in der Befehlszeile überschrieben werden kann. Verwenden Sie beispielsweise

```xml
<MyProperty Condition="'$(MyProperty)' == ''">
   MyDefaultValue
</MyProperty>
```

- Im Allgemeinen sollte die Verwendung von Platzhaltern bei der Auswahl von Elementen vermieden werden. Geben Sie stattdessen Dateien explizit an. Dies wird empfohlen, weil MSBuild bei den meisten Projekttypen Platzhalter zu verschiedenen Zeitpunkten erweitert, z. B. beim Hinzufügen oder Entfernen von Elementen. Dies kann zu unerwartetem Verhalten führen. Eine Ausnahme stellen .NET Core-Projekte im SDK-Stil dar, die Platzhalter ordnungsgemäß verarbeiten.

## <a name="see-also"></a>Siehe auch

- [Weiterführende Konzepte](../msbuild/msbuild-advanced-concepts.md)

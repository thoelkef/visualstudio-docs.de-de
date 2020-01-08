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
ms.openlocfilehash: b1aee1a6ae3abc06846523df9470ad75d316a50b
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592086"
---
# <a name="msbuild-best-practices"></a>Best Practices für MSBuild
Es werden die folgenden bewährten Methoden zum Schreiben von MSBuild-Skripts empfohlen:

- Standardwerte für Eigenschaften werden am besten mit dem `Condition`-Attribut verarbeitet und nicht durch Deklarieren einer Eigenschaft, deren Standardwert in der Befehlszeile überschrieben werden kann. Verwenden Sie beispielsweise

```xml
<MyProperty Condition="'$(MyProperty)' == ''">
   MyDefaultValue
</MyProperty>
```

- Vermeiden Sie beim Auswählen von Elementen den Einsatz von Platzhaltern. Geben Sie stattdessen Dateien explizit an. Dies erleichtert das Auffinden von Fehlern, die beim Hinzufügen oder Löschen von Dateien auftreten können.

## <a name="see-also"></a>Siehe auch
- [Weiterführende Konzepte](../msbuild/msbuild-advanced-concepts.md)

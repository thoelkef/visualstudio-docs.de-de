---
title: Best Practices für MSBuild | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- best practices, MSBuild
- MSBuild, best practices
ms.assetid: 90ef8693-e921-410a-a377-fe4d13f58c48
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8f32626f02e0381ab285d1d6ae1b3127022da438
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/17/2018
ms.locfileid: "39078198"
---
# <a name="msbuild-best-practices"></a>Best Practices für MSBuild
Es werden die folgenden bewährten Methoden zum Schreiben von MSBuild-Skripts empfohlen:  
  
-   Standardwerte für Eigenschaften werden am besten mit dem `Condition`-Attribut verarbeitet und nicht durch Deklarieren einer Eigenschaft, deren Standardwert in der Befehlszeile überschrieben werden kann. Verwenden Sie beispielsweise  
  
```xml
<MyProperty Condition="'$(MyProperty)' == ''">
   MyDefaultValue
</MyProperty>
```
  
-   Vermeiden Sie beim Auswählen von Elementen den Einsatz von Platzhaltern. Geben Sie stattdessen Dateien explizit an. Dies erleichtert das Auffinden von Fehlern, die beim Hinzufügen oder Löschen von Dateien auftreten können.  
  
## <a name="see-also"></a>Siehe auch  
 [Weiterführende Konzepte](../msbuild/msbuild-advanced-concepts.md)

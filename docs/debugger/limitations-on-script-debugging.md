---
title: Einschränkungen beim Skriptdebugging | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- ASPX breakpoint mapping, limitations
- script debugging, limitations
- breakpoint mapping, limitations
ms.assetid: 280eead5-693c-47af-967f-dfe9d23f84db
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cad7008213e0e20b010842b99c9c7be2a39b3bd5
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56687561"
---
# <a name="limitations-on-script-debugging"></a>Einschränkungen beim Skriptdebugging
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] unterstützt das Debuggen von clientseitigem Skript. Dabei gelten die in diesem Artikel erörterten Einschränkungen.

## <a name="limitations-on-breakpoint-mapping-with-client-side-script"></a>Einschränkungen beim Zuordnen von Haltepunkten mit clientseitigem Skript
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ermöglicht es Ihnen, einen Haltepunkt in einer serverseitigen ASPX- oder HTML-Datei festzulegen, die zur Laufzeit in eine clientseitige Datei transformiert wird. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ordnet den Haltepunkt aus der serverseitigen Datei einem entsprechenden Haltepunkt in der clientseitigen Datei zu. Dies unterliegt den folgenden Einschränkungen:

-   Haltepunkte müssen innerhalb von `<script>`-Blöcken festgelegt werden. Haltepunkte in eingebetteten Skripts oder `<% %>`-Blöcken können nicht zugeordnet werden.

-   Die Browser-URL für die Seite muss den Seitennamen enthalten. Beispielsweise http://microsoft.com/default.apsx. Zuordnung von Haltepunkten kann keine Umleitung von einer Adresse erkennen, z. B. http://microsoft.com die Standardseite.

-   Der Haltepunkt muss in der Seite festgelegt werden, die in der Browser-URL angegeben ist, und nicht in einer ASPX-Steuerelementdatei (ascx), Masterseite oder einer anderen auf dieser Seite enthaltenen Datei. Haltepunkte in eingeschlossenen Seiten können nicht zugeordnet werden.

-   Haltepunkte in `<script defer=true>`-Blöcken können nicht zugeordnet werden.

-   Bei Haltepunkten in `<script id="">`-Blöcken wird das `id`-Attribut bei der Zuordnung von Haltepunkten ignoriert.

## <a name="breakpoint-mapping-and-duplicate-lines"></a>Zuordnung von Haltepunkten und doppelte Zeilen
 Um die entsprechende Stelle in serverseitigen und clientseitigen Skripts zu finden, wird der Code durch den Algorithmus für die Zuordnung von Haltepunkten zeilenweise überprüft. Beim Algorithmus wird davon ausgegangen, dass jede Zeile einmal vorkommt. Wenn mindestens zwei Zeilen denselben Code enthalten und Sie einen Haltepunkt für eine dieser doppelten Zeilen festlegen, wird vom Algorithmus für die Zuordnung von Haltepunkten möglicherweise die falsche Entsprechung in der clientseitigen Datei ausgewählt. Um das zu verhindern, fügen Sie der Zeile mit dem festgelegten Haltepunkt einen Kommentar hinzu. Beispiel:

```csharp
i++ ;
i ++; // I added a comment, so this line is now unique
i ++;
```

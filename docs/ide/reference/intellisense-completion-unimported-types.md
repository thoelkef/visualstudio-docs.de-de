---
title: IntelliSense-Vervollständigung für nicht importierte Typen
description: So verwenden Sie die IntelliSense-Vervollständigung für Typen, die Sie noch nicht per `using`-Direktive importiert haben.
ms.date: 06/20/2019
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: f313cfa8520e4c13b310be0f9223466c529ca18f
ms.sourcegitcommit: 16bcaca215de75479695738d3c2d703c78c3500e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/21/2019
ms.locfileid: "67312909"
---
# <a name="intellisense-completion-for-unimported-types"></a>IntelliSense-Vervollständigung für nicht importierte Typen

Dieses Refactoring gilt für:

- C#

**Beschreibung:** IntelliSense bietet eine Vervollständigung für nicht importierte Typen.

**Hintergrund:** Sie möchten einen Typ hinzufügen, für den bereits eine Abhängigkeit in Ihrem Projekt besteht, aber die Importanweisung wurde Ihrer Datei noch nicht hinzugefügt. 

**Vorteile**: Sie müssen die Importanweisung nicht manuell zu Ihrer Datei hinzufügen.

## <a name="how-to"></a>Vorgehensweise

1. Sobald Sie damit beginnen, einen Typ zu verwenden, für den eine Abhängigkeit in Ihrem Projekt besteht, unterbreitet IntelliSense Ihnen Vorschläge.
2. Drücken Sie die **TABULATORTASTE**. 

   Die Importanweisung wird zu Ihrer Datei hinzugefügt.

   ![IntelliSense-Vervollständigung für nicht importierte Typen](media/intellisense-completion-unimported-types.png)

## <a name="see-also"></a>Siehe auch

- [Refactoring](../refactoring-in-visual-studio.md)

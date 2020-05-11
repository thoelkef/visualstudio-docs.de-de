---
title: IntelliSense-Vervollständigung für nicht importierte Typen
description: So verwenden Sie die IntelliSense-Vervollständigung für Typen, die Sie noch nicht per `using`-Direktive importiert haben.
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 04ea7c94d3dd24c1a511544adca9bfac3370cd71
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094265"
---
# <a name="intellisense-completion-for-unimported-types"></a>IntelliSense-Vervollständigung für nicht importierte Typen

Dieses Refactoring gilt für:

- C#

- Visual Basic

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

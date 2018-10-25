---
title: Problembehandlung für Codemetrikfehler
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: troubleshooting
ms.assetid: f2fdb995-4888-4246-85dc-7bacadd45968
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ef7078b09b1bf2382e1c91878995772d80bfa625
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49853960"
---
# <a name="troubleshooting-code-metrics-issues"></a>Problembehandlung für Codemetrikfehler
Beim Sammeln von Codemetriken stoßen Sie möglicherweise auf folgende Probleme:

-   [Änderung in der Berechnung von Codekomplexität in Visual Studio 2010](#Changes_in_Visual_Studio_2010_code_complexity_calculations)

##  <a name="Changes_in_Visual_Studio_2010_code_complexity_calculations"></a> Änderung in der Berechnung von Codekomplexität in Visual Studio 2010
 Die Codekomplexitätsmetrik, die in [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] berechnet wurde, kann sich in folgenden Szenarios für die gleiche Funktion von der Metrik unterscheiden, die von früheren Versionen von [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] berechnet wurde:

- Die Funktion enthält mindestens einen Catch-Block. In früheren Versionen von [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] waren Catch-Blöcke nicht in der Berechnung enthalten. Bei [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] wird die Komplexität jedes einzelnen Catch-Blocks zu der Komplexität der Funktion hinzugefügt.

- Die Funktion enthält eine switch-Anweisung (Select Case in Visual Basic). Unterschiede der Compiler zwischen [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] und früheren Versionen können bei manchen switch-Anweisungen, die Fall-Through-Fälle beinhalten, unterschiedlichen MSIL-Code generieren.

## <a name="see-also"></a>Siehe auch
 [Messen von Komplexität und Verwaltbarkeit verwalteten Codes](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)
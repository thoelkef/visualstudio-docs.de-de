---
title: Vorschau der Codeänderungen
ms.date: 12/16/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
f1_keywords:
- vs.codefix.previewchanges
ms.workload:
- multiple
ms.openlocfilehash: be664e48694ad1d0ea88a95a6b72e0355454d9db
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53832991"
---
# <a name="preview-changes-window"></a>Fenster „Vorschau der Änderungen“

Wenn Sie verschiedene *Schnellaktionen* oder *Refactoring*-Tools in Visual Studio verwenden, ist es oftmals möglich, die Änderungen, die an Ihrem Projekt vorgenommen werden sollen, vor dem Akzeptieren in der Vorschau anzuzeigen. Dies erfolgt im Fenster **Vorschau der Änderungen**.  Beispielsweise sehen Sie hier das Fenster **Vorschau der Änderungen** mit den Änderungen, die bei einem Umbenennen-Refactoring in einem C#-Projekt eintreten werden:

![Vorschau der Änderungen](media/previewchanges.png)

In der oberen Hälfte des Fensters sind die einzelnen Zeilen, die geändert werden sollen, jeweils mit einem Kontrollkästchen zu sehen. Sie können die Kontrollkästchen einzeln aktivieren oder deaktivieren, wenn Sie das Refactoring selektiv nur auf bestimmte Zeilen anwenden möchten.

In der unteren Fensterhälfte wird der formatierte zu ändernde Code mit hervorgehobenen betroffenen Bereichen angezeigt. Beim Auswählen einer bestimmten Zeile in der oberen Fensterhälfte wird die entsprechende Zeile in der unteren Hälfte hervorgehoben. Dadurch können Sie schnell zur betroffenen Zeile springen und den umgebenden Code betrachten.

Klicken Sie nach dem Überprüfen der Änderungen auf die Schaltfläche **Übernehmen**, um diese Änderungen zu committen, oder klicken Sie auf **Abbrechen**, um den Code ungeändert zu lassen.

## <a name="see-also"></a>Siehe auch

- [Refactoring in Visual Studio](../ide/refactoring-in-visual-studio.md)
- [Schnelle Aktionen](../ide/quick-actions.md)

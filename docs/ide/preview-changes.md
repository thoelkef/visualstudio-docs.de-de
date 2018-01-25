---
title: "Vorschau von Codeänderungen in Visual Studio | Microsoft-Dokumentation"
ms.custom: 
ms.date: 12/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords: vs.codefix.previewchanges
ms.workload: multiple
ms.openlocfilehash: 00e2f681a3c010b8a922c00bf9d79de749880186
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/13/2018
---
# <a name="preview-changes-window"></a>Fenster „Vorschau der Änderungen“

Wenn Sie verschiedene *Schnellaktionen* oder *Refactoring*-Tools in Visual Studio verwenden, ist es oftmals möglich, die Änderungen, die an Ihrem Projekt vorgenommen werden sollen, vor dem Akzeptieren in der Vorschau anzuzeigen. Dies erfolgt im Fenster **Vorschau der Änderungen**.  Beispielsweise sehen Sie hier das Fenster **Vorschau der Änderungen** mit den Änderungen, die bei einem Umbenennen-Refactoring in einem C#-Projekt eintreten werden:

![Vorschau der Änderungen](media/previewchanges.png)

In der oberen Hälfte des Fensters sind die einzelnen Zeilen, die geändert werden sollen, jeweils mit einem Kontrollkästchen zu sehen. Sie können die Kontrollkästchen einzeln aktivieren oder deaktivieren, wenn Sie das Refactoring selektiv nur auf bestimmte Zeilen anwenden möchten.

In der unteren Fensterhälfte wird der formatierte zu ändernde Code mit hervorgehobenen betroffenen Bereichen angezeigt. Beim Auswählen einer bestimmten Zeile in der oberen Fensterhälfte wird die entsprechende Zeile in der unteren Hälfte hervorgehoben. Dadurch können Sie schnell zur betroffenen Zeile springen und den umgebenden Code betrachten.

Klicken Sie nach dem Überprüfen der Änderungen auf die Schaltfläche **Übernehmen**, um diese Änderungen zu committen, oder klicken Sie auf **Abbrechen**, um den Code ungeändert zu lassen.

## <a name="see-also"></a>Siehe auch

[Refactoring in Visual Studio](../ide/refactoring-in-visual-studio.md)  
[Schnellaktionen](../ide/quick-actions.md)

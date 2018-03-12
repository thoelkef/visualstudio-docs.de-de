---
title: "Hilfefenster in R Tools für Visual Studio | Microsoft-Dokumentation"
description: "Die Hilfe für R ist in Form des Befehls „?“ direkt in das interaktive Fenster in Visual Studio integriert ."
ms.custom: 
ms.date: 001/24/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
dev_langs:
- R
ms.tgt_pltfrm: 
ms.topic: get-started-article
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- data-science
ms.openlocfilehash: 2adaa5713018071ee94c14e2cb35959c256eb1d1
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/09/2018
---
# <a name="help-in-r-tools-for-visual-studio"></a>Hilfe in R Tools für Visual Studio

Die Hilfe für R ist direkt in das interaktive Fenster in Visual Studio integriert. Wenn Sie den `?`-Befehl verwenden, z.B. `?mtcars`, erscheint die Hilfe aus der R-Dokumentation in einem Visual Studio-Fenster:

![Hilfefenster in Visual Studio](media/help-window.png)

> [!Tip]
> So wie alle anderen Fenster in Visual Studio kann das Hilfefenster beliebig angeordnet und angedockt werden. Weitere Informationen finden Sie unter [Anpassen von Fensterlayouts in Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md).
>
> Sie können Ergebnisse der Hilfe in einem Browser öffnen, indem Sie das Menü **R Tools > Optionen** anklicken und die Eigenschaft **Browser der R-Hilfe** auf `External` festzulegen. Weitere Informationen finden Sie unter [Optionen](options-for-r-tools-in-visual-studio.md).

Verwenden Sie den `??`-Befehl, gefolgt von einem Suchbegriff, um die Hilfe zu durchsuchen. Verwenden Sie Anführungszeichen, wenn der Suchbegriff Leerzeichen enthält:

```R
??"Motor Trend"
```

![Die Suchergebnisse der Hilfe](media/help-search1.png)

Das Hilfefenster verfügt auch über ein Sucheingabefeld, über das Sie weitere Suchen direkt in der R-Dokumentation durchführen können:

![Suchergebnisse der Hilfe über das Eingabefeld](media/help-search2.png)

## <a name="integrated-help-lookup"></a>Integrierte Hilfeansicht

Entwickler durchsuchen für Hilfe bei den Funktionsnamen, Datasets und anderen Elementen häufig die R-Dokumentation. R-Tools für Visual Studio (RTVS) optimiert den Prozess, indem Hilfeansichten direkt in den Editor und in interaktive Fenster integriert werden.

- Durch Drücken der F1-TASTE wird während eines Vorgangs mit automatischer Vervollständigung eine Liste von Hilfeergebnissen erstellt, die mit der Teilzeichenfolge übereinstimmen.
- Führen Sie einen Rechtsklick auf einen Suchbegriff (z.B. eine Funktion) aus, und wählen Sie den Befehl **Help on** (Hilde zu) aus, um die Hilfe für diese Funktion aufzurufen. Sie können **Hilfe zu** auch für jede Auswahl aufrufen.

    ![Aufrufen der Hilfe über ein Kontextmenü, das mit einem Rechtsklick aufgerufen wird](media/help-right-click.png)

> [!Tip]
> Um die integrierte Hilfe in einem Browser zu öffnen, wählen Sie **R Tools > Optionen** aus, und legen Sie **F1-Webbrowser** auf `External` fest. Weitere Informationen finden Sie unter [Optionen](options-for-r-tools-in-visual-studio.md).

## <a name="integrated-stackoverflow-search"></a>Integrierte StackOverflow-Suche

Entwickler suchen zusätzlich zur Suche in der R-Dokumentation oft in StackOverflow, während Sie Code schreiben. RTVS optimiert ebenso diesen Prozess. Führen Sie einen Rechtsklick auf einen Begriff oder eine Auswahl aus und wählen Sie den Befehl (STRG+F1) **Search web for** (Web durchsuchen) aus. Visual Studio öffnet dann ein Fenster mit den auf StackOverflow beschränkten Suchbegriffen:

![Websuchergebnisse in Visual Studio](media/help-web-search-results.png)

Sie können die angefügte Zeichenfolge, `R site:stackoverflow`, über die Option **R Tools > Optionen > F1 Web search string** (Zeichenfolge der F1-Websuche) ändern:

![Ändern der Option „Zeichenfolge der F1-Websuche“](media/options-dialog.png)

Wenn Sie die Ergebnisse lieber im Browser anzeigen lassen möchten, verändern Sie die Option **F1 Webbrowser** (F1-Webbrowser) wie in [Optionen](options-for-r-tools-in-visual-studio.md) beschrieben.
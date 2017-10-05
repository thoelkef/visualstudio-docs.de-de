---
title: "Hilfefenster in R Tools für Visual Studio | Microsoft-Dokumentation"
ms.custom: 
ms.date: 6/29/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.devlang: r
ms.tgt_pltfrm: 
ms.topic: get-started-article
ms.assetid: ef9c04d4-0d5e-405a-842e-8d47fa0e8781
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 712cc780388acc5e373f71d51fc8f1f42adb5bed
ms.openlocfilehash: 2542682ecab54235a236a93c9906185547017c4c
ms.contentlocale: de-de
ms.lasthandoff: 07/12/2017

---

# <a name="help-in-r-tools-for-visual-studio"></a>Hilfe in R Tools für Visual Studio

Die Hilfe für R ist direkt in das interaktive Fenster in Visual Studio integriert. Wenn Sie den `?`-Befehl verwenden, z.B. `?mtcars`, erscheint die Hilfe aus der R-Dokumentation in einem Visual Studio-Fenster:

![Hilfefenster in Visual Studio](media/help-window.png)

> [!Tip]
> So wie alle anderen Fenster in Visual Studio kann das Hilfefenster beliebig angeordnet und angedockt werden. Weitere Informationen finden Sie unter [Anpassen von Fensterlayouts in Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md).
>
> Sie können Ergebnisse der Hilfe in einem Browser öffnen, indem Sie das Menü **R Tools > Optionen** anklicken und die Eigenschaft **Browser der R-Hilfe** auf `External` festzulegen. Weitere Informationen finden Sie unter [Optionen](options.md).

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
> Um die integrierte Hilfe in einem Browser zu öffnen, wählen Sie **R Tools > Optionen** aus, und legen Sie **F1-Webbrowser** auf `External` fest. Weitere Informationen finden Sie unter [Optionen](options.md).

## <a name="integrated-stackoverflow-search"></a>Integrierte StackOverflow-Suche

Entwickler suchen zusätzlich zur Suche in der R-Dokumentation oft in StackOverflow, während Sie Code schreiben. RTVS optimiert ebenso diesen Prozess. Führen Sie einen Rechtsklick auf einen Begriff oder eine Auswahl aus und wählen Sie den Befehl (STRG+F1) **Search web for** (Web durchsuchen) aus. Visual Studio öffnet dann ein Fenster mit den auf StackOverflow beschränkten Suchbegriffen:

![Websuchergebnisse in Visual Studio](media/help-web-search-results.png)

Sie können die angefügte Zeichenfolge, `R site:stackoverflow`, über die Option **R Tools > Optionen > F1 Web search string** (Zeichenfolge der F1-Websuche) ändern:

![Ändern der Option „Zeichenfolge der F1-Websuche“](media/options-dialog.png)

Wenn Sie die Ergebnisse lieber im Browser anzeigen lassen möchten, verändern Sie die Option **F1 Webbrowser** (F1-Webbrowser) wie in [Optionen](options.md) beschrieben.

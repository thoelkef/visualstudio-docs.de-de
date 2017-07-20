---
title: "Hilfefenster in R Tools für Visual Studio | Microsoft-Dokumentation"
ms.custom: 
ms.date: 4/26/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ef9c04d4-0d5e-405a-842e-8d47fa0e8781
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 7a873df77756e5a957d327049566c8e0db1f3a8a
ms.openlocfilehash: 6644ea68ae691e8467828ff699245fef4e485971
ms.contentlocale: de-de
ms.lasthandoff: 05/12/2017

---


# <a name="help-in-r-tools-for-visual-studio"></a>Hilfe in R Tools für Visual Studio

Die Hilfe für R ist direkt in das interaktive Fenster in Visual Studio integriert. Wenn Sie den `?`-Befehl verwenden, z.B. `?mtcars`, erscheint die Hilfe aus der R-Dokumentation in einem Visual Studio-Fenster:

![Hilfefenster in Visual Studio](media/help-window.png)

> [!Tip]
> So wie alle anderen Fenster in Visual Studio kann das Hilfefenster beliebig angeordnet und angedockt werden. Weitere Informationen finden Sie unter [Anpassen von Fensterlayouts in Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md).
>
> Sie können Ergebnisse der Hilfe auch in einem Browser öffnen, anstatt das Menü **R Tools > Optionen** auszuwählen und die Eigenschaft **Browser der R-Hilfe** auf `External` festzulegen. Weitere Informationen finden Sie unter [Optionen](options.md).

Verwenden Sie den `??`-Befehl, und geben Sie den gesuchten Begriff in Anführungszeichen ein, wenn dieser Leerzeichen enthält, um die Hilfe zu durchsuchen:

```R
??"Motor Trend"
```

![Die Suchergebnisse der Hilfe](media/help-search1.png)

Das Hilfefenster verfügt auch über ein Sucheingabefeld, über das Sie weitere Suchen direkt in der R-Dokumentation durchführen können:

![Suchergebnisse der Hilfe über das Eingabefeld](media/help-search2.png)

## <a name="integrated-help-lookup"></a>Integrierte Hilfeansicht

Da Entwickler oft in der R-Dokumentation nach Hilfe zu Funktionsnamen, Datasets und anderen Elementen suchen, optimiert R Tools für Visual Studio den Prozess, indem Hilfeansichten direkt in den Editor und das interaktive Fenster integriert werden.

- Durch Drücken der F1-TASTE wird während eines Vorgangs mit automatischer Vervollständigung eine Liste von Hilfeergebnissen erstellt, die mit der Teilzeichenfolge übereinstimmen.
- Führen Sie einen Rechtsklick auf einen Suchbegriff (z.B. eine Funktion) aus, und wählen Sie den Befehl **Hilfe zu** aus, oder drücken Sie alternativ F1, um die Hilfe für diese Funktion aufzurufen. Sie können **Hilfe zu** auch für jede Auswahl aufrufen.

    ![Aufrufen der Hilfe über ein Kontextmenü, das mit einem Rechtsklick aufgerufen wird](media/help-right-click.png)

> [!Tip]
> Um die integrierte Hilfe in einem Browser zu öffnen, wählen Sie **R Tools > Optionen** aus, und legen Sie **F1-Webbrowser** auf `External` fest. Weitere Informationen finden Sie unter [Optionen](options.md).

## <a name="integrated-stackoverflow-search"></a>Integrierte StackOverflow-Suche

Entwickler suchen zusätzlich zur Suche in der R-Dokumentation oft in StackOverflow, während Sie Code schreiben. RTVS optimiert ebenso diesen Prozess. Wenn Sie auf einen Begriff oder eine Auswahl rechtsklicken und den Befehl **Search web for** (Web durchsuchen) auswählen oder alternativ nur STRG+F1 drücken, wird ein Visual Studio-Fenster geöffnet (oder ein Browser, wenn Sie die **F1-Webbrowser**-Option geändert haben), das Suchergebnisse für diesen Begriff enthält, der standardmäßig auf StackOverflow beschränkt wird.

![Websuchergebnisse in Visual Studio](media/help-web-search-results.png)

Sie können die angefügte Zeichenfolge, `R site:stackoverflow`, über die Option **R Tools > Optionen > F1 Web search string** (Zeichenfolge der F1-Websuche) ändern:

![Ändern der Option „Zeichenfolge der F1-Websuche“](media/options-dialog.png)

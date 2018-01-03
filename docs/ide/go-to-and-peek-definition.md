---
title: "„Gehe zu Definition“ und „Definition einsehen“ | Microsoft-Dokumentation"
ms.custom: 
ms.date: 10/04/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code editor, go to definition
- code editor, peek definition
- go to definition
- peek definition
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: db67f01ff2a58ee856e4588df8770fc4edef8ca2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="go-to-definition-and-peek-definition"></a>„Gehe zu Definition“ und „Definition einsehen“  
Durch die Funktionen „Gehe zu Definition“ und „Definition einsehen“ können Sie die Definition eines Typs oder Members einfach anzeigen.

## <a name="go-to-definition"></a>Gehe zu Definition  
Die Funktion „Gehe zu Definition“ navigiert zur Quelle eines Typs oder Members und öffnet die Ergebnisse in einer neuen Registerkarte. Wenn Sie die Tastatur verwenden, platzieren Sie den Textcursor an einer beliebigen Stelle innerhalb des Symbols, und drücken Sie **F12**. Wenn Sie die Maus verwenden, klicken Sie entweder im Kontextmenü auf **Gehe zu Definition**, oder verwenden Sie die unten beschriebene Funktionalität **STRG+Klick**.  

### <a name="ctrl-click-go-to-definition"></a>„Gehe zu Definition“ mit STRG+Klick  
In Visual Studio 2017 Version 15.4 gibt es eine einfachere Möglichkeit für Mausbenutzer, um schnell auf „Gehe zu Definition“ zuzugreifen. Symbole werden anklickbar, wenn Sie **STRG** drücken und auf den Typ oder Member zeigen. Drücken Sie die Taste **STRG**, und klicken Sie auf ein Symbol, um schnell zu dessen Definition zu navigieren. So einfach ist das!

![Animation: „Gehe zu Definition“ per Mausklick](../ide/media/click_gotodef.gif)

Die Zusatztaste für **Gehe zu Definition** per Mausklick können Sie ändern, indem Sie zu **Extras** > **Optionen** > **Text-Editor** > **Allgemein** navigieren und aus der Dropdownliste **Zusatztaste verwenden** entweder **ALT** oder **STRG+ALT** auswählen. Sie können **Gehe zu Definition** per Mausklick auch deaktivieren, indem Sie das Kontrollkästchen **Mausklick zum Wechseln zur Definition aktivieren** deaktivieren.  

![Aktivieren des Mausklicks zum Wechsel zur Definition](../ide/media/editor_options_mouse_click_gotodef.png)  

## <a name="peek-definition"></a>Peek-Definition
Die Funktion „Definition einsehen“ ermöglicht eine Vorschau der Definition eines Typs, ohne Ihre Position im Editor verlassen zu müssen. Wenn Sie die Tastatur verwenden, platzieren Sie den Textcursor an einer beliebigen Stelle innerhalb des Typs oder Members, und drücken Sie **ALT+F12**. Wenn Sie die Maus verwenden, können Sie im Kontextmenü auf **Definition einsehen** klicken. In Visual Studio 2017 Version 15.4 und höher gibt es eine neue Möglichkeit, um eine Definition mithilfe der Maus einzusehen. Navigieren Sie zunächst zu **Extras** > **Optionen** > **Text-Editor** > **Allgemein**. Wählen Sie die Option **Definition in der Vorschauansicht öffnen** aus, klicken Sie auf **OK**, und schließen Sie das Dialogfeld **Optionen**.  

![Festlegen der Option, Definitionen per Mausklick einzusehen](../ide/media/editor_options_peek_view.png)  

Drücken Sie dann **STRG** (bzw. die Zusatztaste, die in **Optionen** ausgewählt ist), und klicken Sie auf den Typ oder Member.  

![Animation: „Definition einsehen“](../ide/media/peek_definition.gif)

Wenn Sie im Popupfenster eine andere Definition einsehen möchten, können Sie einen Brotkrumenpfad beginnen, in dem Sie mithilfe der Kreise und Pfeile navigieren können, die oberhalb des Popups angezeigt werden.  

Weitere Informationen finden Sie unter [Gewusst wie: Anzeigen und Bearbeiten von Code mithilfe von „Definition einsehen“ (Alt+F12)](how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md).  

## <a name="see-also"></a>Siehe auch  
[Navigieren im Code](../ide/navigating-code.md)  
[Gewusst wie: Anzeigen und Bearbeiten von Code mithilfe von "Definition einsehen" (Alt+F12)](how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md)  

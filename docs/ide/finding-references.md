---
title: Suchen von Verweisen im Code | Microsoft-Dokumentation
ms.custom: 
ms.date: 09/26/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code editor, find all references
- find all references
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4a402d8541f7056ebcb57885197d001b39c8d9b0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="finding-references-in-your-code"></a>Suchen von Verweisen im Code  
Mithilfe des Befehls **Alle Verweise suchen** können Sie in Ihrer gesamten Codebasis die Stellen finden, an denen auf bestimmte Codeelemente verwiesen wird. Den Befehl **Alle Verweise suchen** finden Sie im Kontextmenü (Rechtsklick) des Elements, für das Sie Verweise suchen möchten. Wenn Sie eine Tastatur verwenden, können Sie einfach **UMSCHALT+F12** drücken.  

Die Ergebnisse werden in einem Toolfenster mit der Bezeichnung **'*element*' references** (<Element>-Verweise) angezeigt, wobei *element* der Name des gesuchten Elements ist. Mit einer Symbolleiste im **Verweisfenster** können Sie Folgendes tun:  
- Den Suchbereich über ein Dropdown-Listenfeld ändern. Sie können auswählen, nur in geänderten Dokumenten bis hin zur gesamten Projektmappe zu suchen.  
- Das ausgewählte Verweiselement durch Auswählen der Schaltfläche **Kopieren** kopieren.  
- Schaltflächen auswählen, um zum nächsten oder vorherigen Element in der Liste zu wechseln. Drücken Sie dazu alternativ die Tasten **F8** und **UMSCHALT+F8**.  
- Alle Filter auf den zurückgegebenen Ergebnissen durch Auswählen der Schaltflächen **Alle Filter löschen** entfernen.  
- Ändern, wie zurückgegebene Elemente gruppiert werden, indem Sie eine Einstellung im Dropdown-Listenfeld **Gruppieren nach:** auswählen.  
- Das Fenster der aktuellen Suchergebnisse beibehalten, indem Sie auf die Schaltfläche **Ergebnisse beibehalten** drücken. Wenn Sie diese Schaltfläche auswählen, verbleiben die aktuellen Suchergebnisse in diesem Fenster und neue Suchergebnisse erscheinen in einem neuen Toolfenster.  
- Zeichenfolgen innerhalb der Suchergebnisse suchen, indem Sie Text in das Feld **Suche: Alle Verweise suchen** eingeben.  

Sie können auch mit dem Mauszeiger auf ein Suchergebnis zeigen, um eine Vorschau des Verweises einzublenden.  

![Toolfenster „Alle Verweise suchen“](../ide/media/vside_findallreferences.png)  

### <a name="navigate-to-references"></a>„Navigieren zu“-Verweise
Mithilfe der folgenden Methoden können Sie zu den **Verweisen** im entsprechenden Fenster wechseln:  

- Drücken Sie **F8**, um zum nächsten Verweis zu springen, oder **UMSCHALT+F8**, um zum vorherigen Verweis zu wechseln.  
- Drücken Sie auf einem Verweis die **EINGABETASTE**, oder führen Sie einen Doppelklick aus, um zu der entsprechenden Stelle im Code zu wechseln.  
- Wählen Sie im Kontextmenü eines Verweises den Befehl **Gehe zu vorheriger Position** oder **Gehe zu nächster Position** aus.  
- Wählen Sie den **Pfeil nach oben** und den **Pfeil nach unten** aus (falls sie im Dialogfeld „Optionen“ aktiviert sind). Um diese Funktionalität zu aktivieren, klicken Sie im Menü auf **Extras** > **Optionen** > **Umgebung** > **Registerkarten und Fenster** > **Vorschauregisterkarte** und anschließend auf die Felder **Das Öffnen neuer Dateien in der Vorschauregisterkarte zulassen** und **Vorschau der ausgewählten Dateien in "Ergebnisse suchen" anzeigen**.  

### <a name="change-reference-groupings"></a>Änderung von Verweisgruppierungen  
Standardmäßig werden Verweise vom Projekt dann per Definition gruppiert. Sie können diese Gruppierungsreihenfolge jedoch ändern, indem Sie im Dropdown-Listenfeld auf der Symbolleiste die Einstellung **Gruppieren nach:** ändern. Sie können sie beispielsweise von der Standardeinstellung **Projekt, dann Definition** in **Definition, dann Projekt** ändern.  

**Definition** und **Projekt** sind die beiden verwendeten Standardgruppierungen, aber Sie können andere hinzufügen, indem Sie den Befehl **Gruppierung** im Kontextmenü des ausgewählten Elements auswählen. Das Hinzufügen weiterer Gruppen kann hilfreich sein, wenn Ihre Projektmappe viele Dateien und Pfade enthält.  

## <a name="see-also"></a>Siehe auch  
[Navigieren im Code](../ide/navigating-code.md)  
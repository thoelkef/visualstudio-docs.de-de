---
title: Anzeigen von Datenwerten in DataTips im Code-Editor | Microsoft Docs
ms.custom: 
ms.date: 07/14/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugging [Visual Studio], DataTips
- DataTips tool
ms.assetid: ffa7bd18-439b-4685-a9b3-c7884b5de41f
caps.latest.revision: "38"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2eb975b5d4c1f3450ca18b1ea0da3cd3b7fb6375
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="view-data-values-in-datatips-in-the-code-editor"></a>Anzeigen von Datenwerten in DataTips, im Code-editor
DataTips stellen eine praktische Möglichkeit dar, um beim Debuggen Informationen über Variablen im Programm anzuzeigen. Sie können DataTips nur im Unterbrechungsmodus verwenden und nur mit Variablen, die sich im aktuellen Gültigkeitsbereich der Ausführung befinden.
  
### <a name="to-display-a-datatip"></a>Einen DataTip angezeigt.  
  
1. Festlegen eines Haltepunkts und das Debuggen starten (drücken Sie **F5**).

2. Wenn im Debugger angehalten wird, platzieren Sie den Mauszeiger auf eine beliebige Variable im aktuellen Bereich.
  
     Ein DataTip wird angezeigt.
  
3.  Der DataTip verschwindet, wenn Sie den Mauszeiger fortbewegen. Um den DataTip anzuheften, sodass dieser geöffnet bleibt, klicken Sie auf die **an Quelle heften** Symbol oder mit der rechten Maustaste auf eine Variable aus, klicken Sie dann auf **an Quelle heften**.

    ![Anheften eines Datentipps](../debugger/media/dbg-tips-data-tips-pinned.png "PinningDataTip")

    > [!NOTE]
    > DataTips werden immer in dem Kontext ausgeführt, in dem die Ausführung angehalten wird, und nicht an der Stelle, auf die der Cursor zeigt. Wenn Sie in einer anderen Funktion auf eine Variable mit dem Namen einer Variablen im aktuellen Kontext zeigen, wird der Wert der Variablen in der anderen Funktion als der Wert der Variablen im aktuellen Kontext angezeigt.
  
### <a name="to-unpin-a-datatip-and-make-it-float"></a>So lösen Sie einen DataTip und zeigen diesen unverankert an  
  
-   Klicken Sie in einem angehefteten DataTip auf das **von Quelle lösen** Symbol.  
  
     Das Pinsymbol ändert sich in die gelöste Position. Der DataTip wird nun unverankert über allen geöffneten Fenstern angezeigt. Der unverankerte DataTip wird geschlossen, wenn die Debugsitzung endet.  
  
### <a name="to-repin-a-floating-datatip"></a>So heften Sie einen unverankerten DataTip wieder an  
  
-   Klicken Sie in einem DataTip auf das Pinsymbol.  
  
     Das Pinsymbol ändert sich in die angeheftete Position. Wenn sich der DataTip außerhalb eines Quellcodefensters befindet, wird das Pinsymbol deaktiviert, und der DataTip kann nicht angeheftet werden.  
  
### <a name="to-close-a-datatip"></a>So schließen Sie einen DataTip  
  
-   Platzieren Sie den Mauszeiger über einem DataTip, und klicken Sie dann auf die **schließen** Symbol.  
  
### <a name="to-close-all-datatips"></a>So schließen Sie alle DataTips  
  
-   Auf der **Debuggen** Menü klicken Sie auf **alle DataTips löschen**.  
  
### <a name="to-close-all-datatips-for-a-specific-file"></a>So schließen Sie alle DataTips für eine bestimmte Datei  
  
-   Auf der **Debuggen** Menü klicken Sie auf **Löschen aller angehefteten DataTips an** *Datei*.  
  
## <a name="expand-and-edit-information"></a>Erweitern Sie Informationen anzeigen und bearbeiten  
 Mithilfe von DataTips können Sie ein Array, eine Struktur oder ein Objekt erweitern, um deren Member anzuzeigen. Sie können mit einem DataTip auch den Wert einer Variablen bearbeiten.  
  
#### <a name="to-expand-a-variable-to-see-its-elements"></a>So erweitern Sie eine Variable, um ihre Elemente anzuzeigen  
  
-   Platzieren Sie in einem DataTip den Mauszeiger über die  **+**  Zeichen vor dem Variablennamen.  
  
    Die Variable wird erweitert, und die Elemente werden in Strukturansicht angezeigt.

    ![Anzeigen von einem Datentipp](../debugger/media/dbg-tour-data-tips.gif "einen Datentipp anzeigen")
  
    Bei erweiterter Variable können Sie mit den Pfeiltasten der Tastatur nach oben und unten navigieren. Sie können auch die Maus verwenden.  
  
#### <a name="to-edit-the-value-of-a-variable-using-a-datatip"></a>So bearbeiten Sie den Wert einer Variablen mit einem DataTip  
  
1.  Klicken Sie in einem DataTip auf den Wert. Für schreibgeschützte Werte ist diese Funktion deaktiviert.  
  
2.  Geben Sie einen neuen Wert ein, und drücken Sie die EINGABETASTE.  
  
## <a name="making-a-datatip-transparent"></a>Transparentes Darstellen eines DataTips  
 Wenn Sie den Code hinter einem DataTip sehen möchten, können Sie dazu den DataTip vorübergehend transparent machen. Dies gilt nicht für DataTips, die angeheftet oder unverankert sind.  
  
#### <a name="to-make-a-datatip-transparent"></a>So machen Sie einen DataTip transparent  
  
-   Drücken Sie in einem DataTip STRG.  
  
     Der DataTip bleibt so lange transparent, wie Sie STRG gedrückt halten.  
  
## <a name="visualize-complex-data-types"></a>Visualisieren von komplexen Datentypen  
 Wenn ein Lupensymbol neben einem Variablennamen in mindestens einem DataTip angezeigt wird [Schnellansichten](../debugger/create-custom-visualizers-of-data.md), wie z. B. die [Zeichenfolge Schnellansichten](../debugger/string-visualizer-dialog-box.md), stehen für die Variablen dieses Datentyps. Mit der Schnellansicht lassen sich Informationen noch übersichtlicher (in der Regel über eine grafische Darstellung) anzeigen.
  
#### <a name="to-view-the-contents-of-a-variable-using-a-visualizer"></a>So zeigen Sie den Inhalt einer Variablen mithilfe der Schnellansicht an  
  
-   Klicken Sie auf das Lupensymbol ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "Schnellansicht Symbol") um die Standardschnellansicht für den Datentyp auszuwählen.  
  
     - oder -   
  
     Klicken Sie auf den Popup-Pfeil neben der Schnellansicht, und wählen Sie aus der Liste eine dem Datentyp entsprechende Schnellansicht aus.  
  
     Die Informationen werden in einer Schnellansicht angezeigt.  
  
## <a name="add-information-to-a-watch-window"></a>Hinzufügen von Daten zu einem Überwachungsfenster  
 Wenn Sie den Vorgang fortzusetzen, um eine Variable in einer Listenansicht zu beobachten möchten, können Sie die Variable zum Hinzufügen der **Überwachen** aus einem DataTip.  
  
#### <a name="to-add-a-variable-to-the-watch-window"></a>So fügen Sie dem Überwachungsfenster eine Variable hinzu  
  
-   Mit der rechten Maustaste in eines DataTips, und klicken Sie dann auf **Überwachung hinzufügen**.  
  
     Die Variable wird hinzugefügt, um die **Überwachen** Fenster. Wenn Sie eine Edition verwenden, die mehrere unterstützt **Überwachen** Windows, die Variable wird hinzugefügt, um **Überwachen 1.**  
  
## <a name="import-and-export-datatips"></a>Importieren und Exportieren von DataTips  
 Sie können DataTips in eine XML-Datei exportieren, die Sie gemeinsam mit Kollegen verwenden oder in einem Text-Editor bearbeiten können.  
  
#### <a name="to-export-datatips"></a>So exportieren Sie DataTips  
  
1.  Klicken Sie im Menü Debuggen auf **DataTips exportieren**.  
  
     Die **DataTips exportieren** Dialogfeld wird angezeigt.  
  
2.  Mithilfe von Standarddateitechniken zu dem Speicherort navigieren Sie die XML-Datei speichern, geben Sie einen Namen für die Datei in möchten die **Dateiname** Feld, und klicken Sie dann auf **OK**.  
  
#### <a name="to-import-datatips"></a>So importieren Sie DataTips  
  
1.  Klicken Sie im Menü Debuggen auf **DataTips importieren**.  
  
     Die **DataTips importieren** Dialogfeld wird angezeigt.  
  
2.  Verwenden Sie das Dialogfeld, um die XML-Datei zu suchen, die Sie verwenden möchten, öffnen, und klicken Sie auf **OK**.  
  
## <a name="see-also"></a>Siehe auch  
 [Anzeigen von Daten im Debugger](../debugger/viewing-data-in-the-debugger.md)   
 [Überwachen "und" Schnellüberwachung Windows](../debugger/watch-and-quickwatch-windows.md)   
 [Erstellen benutzerdefinierter Schnellansichten](../debugger/create-custom-visualizers-of-data.md)   
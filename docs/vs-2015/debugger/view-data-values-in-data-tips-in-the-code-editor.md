---
title: Anzeigen von Datenwerten als Datentipps im Code-Editor | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], DataTips
- DataTips tool
ms.assetid: ffa7bd18-439b-4685-a9b3-c7884b5de41f
caps.latest.revision: 41
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f1a7e755fd81bb66d822f7232e903fea9c53087c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47509622"
---
# <a name="view-data-values-in-data-tips--in-the-code-editor"></a>Anzeigen von Datenwerten als Datentipps im Code-Editor
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Anzeigen von Datenwerten als Datentipps im Code-Editor](https://docs.microsoft.com/visualstudio/debugger/view-data-values-in-data-tips-in-the-code-editor).  
  
DataTips stellen eine praktische Möglichkeit dar, um beim Debuggen Informationen über Variablen im Programm anzuzeigen. Sie können DataTips nur im Unterbrechungsmodus verwenden und nur mit Variablen, die sich im aktuellen Gültigkeitsbereich der Ausführung befinden.  
  
 In [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)], DataTips an einem bestimmten Speicherort in einer Quelldatei angeheftet werden können oder sie können auf alle float [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Windows.  
  
### <a name="to-display-a-datatip-in-break-mode-only"></a>So zeigen Sie DataTips an (nur im Unterbrechungsmodus)  
  
1.  Platzieren Sie in einem Quellcodefenster den Mauszeiger auf eine beliebige Variable aus dem aktuellen Gültigkeitsbereich.  
  
     Ein DataTip wird angezeigt.  
  
    > [!NOTE]
    >  DataTips werden immer in dem Kontext ausgeführt, in dem die Ausführung angehalten wird, und nicht an der Stelle, auf die der Cursor zeigt. Wenn Sie in einer anderen Funktion auf eine Variable mit dem Namen einer Variablen im aktuellen Kontext zeigen, wird der Wert der Variablen in der anderen Funktion als der Wert der Variablen im aktuellen Kontext angezeigt.  
  
2.  Der DataTip verschwindet, wenn Sie den Mauszeiger fortbewegen. Um den DataTip anzuheften, sodass dieser geöffnet bleibt, klicken Sie auf die **an Quelle heften** Symbol, oder  
  
    -   Mit der rechten Maustaste auf eine Variable, und klicken Sie dann **an Quelle heften**.  
  
     Der angeheftete DataTip wird geschlossen, wenn die Debugsitzung endet.  
  
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
  
-   Auf der **Debuggen** Menü klicken Sie auf **Löschen aller angehefteten DataTips,** *Datei*.  
  
## <a name="expanding-and-editing-information"></a>Erweitern und Bearbeiten von Informationen  
 Mithilfe von DataTips können Sie ein Array, eine Struktur oder ein Objekt erweitern, um deren Member anzuzeigen. Sie können mit einem DataTip auch den Wert einer Variablen bearbeiten.  
  
#### <a name="to-expand-a-variable-to-see-its-elements"></a>So erweitern Sie eine Variable, um ihre Elemente anzuzeigen  
  
-   Fügen Sie in einem DataTip den Mauszeiger über die **+** Zeichen vor dem Variablennamen.  
  
     Die Variable wird erweitert, und die Elemente werden in Strukturansicht angezeigt.  
  
     Bei erweiterter Variable können Sie mit den Pfeiltasten der Tastatur nach oben und unten navigieren. Sie können auch die Maus verwenden.  
  
#### <a name="to-edit-the-value-of-a-variable-using-a-datatip"></a>So bearbeiten Sie den Wert einer Variablen mit einem DataTip  
  
1.  Klicken Sie in einem DataTip auf den Wert. Für schreibgeschützte Werte ist diese Funktion deaktiviert.  
  
2.  Geben Sie einen neuen Wert ein, und drücken Sie die EINGABETASTE.  
  
## <a name="making-a-datatip-transparent"></a>Transparentes Darstellen eines DataTips  
 Wenn Sie den Code hinter einem DataTip sehen möchten, können Sie dazu den DataTip vorübergehend transparent machen. Dies gilt nicht für DataTips, die angeheftet oder unverankert sind.  
  
#### <a name="to-make-a-datatip-transparent"></a>So machen Sie einen DataTip transparent  
  
-   Drücken Sie in einem DataTip STRG.  
  
     Der DataTip bleibt so lange transparent, wie Sie STRG gedrückt halten.  
  
## <a name="visualizing-complex-data-types"></a>Visuelles Darstellen von komplexen Datentypen  
 Wenn ein Lupensymbol neben einem Variablennamen in mindestens einem DataTip angezeigt wird, [erstellen Sie benutzerdefinierte Schnellansichten](../debugger/create-custom-visualizers-of-data.md) stehen für die Variablen dieses Datentyps. Mit der Schnellansicht lassen sich Informationen noch übersichtlicher (in der Regel über eine grafische Darstellung) anzeigen.  
  
#### <a name="to-view-the-contents-of-a-variable-using-a-visualizer"></a>So zeigen Sie den Inhalt einer Variablen mithilfe der Schnellansicht an  
  
-   Klicken Sie auf das Symbol mit dem Vergrößerungsglas, um die Standardschnellansicht für den Datentyp auszuwählen.  
  
     - oder -   
  
     Klicken Sie auf den Popup-Pfeil neben der Schnellansicht, und wählen Sie aus der Liste eine dem Datentyp entsprechende Schnellansicht aus.  
  
     Die Informationen werden in einer Schnellansicht angezeigt.  
  
## <a name="adding-information-to-a-watch-window"></a>Hinzufügen von Informationen zu einem Überwachungsfenster  
 Wenn Sie weiterhin eine Variable ansehen möchten, können Sie die Variable Hinzufügen der **Watch** aus einem DataTip.  
  
#### <a name="to-add-a-variable-to-the-watch-window"></a>So fügen Sie dem Überwachungsfenster eine Variable hinzu  
  
-   Mit der rechten Maustaste in eines DataTips, und klicken Sie dann auf **Überwachung hinzufügen**.  
  
     Die Variable wird hinzugefügt, um die **Watch** Fenster. Wenn Sie eine Edition verwenden, die mehrere unterstützt **Watch** Windows, der Variablen hinzugefügt **Überwachen 1.**  
  
## <a name="importing-and-exporting-datatips"></a>Importieren und Exportieren von DataTips  
 Sie können DataTips in eine XML-Datei exportieren, die Sie gemeinsam mit Kollegen verwenden oder in einem Text-Editor bearbeiten können.  
  
#### <a name="to-export-datatips"></a>So exportieren Sie DataTips  
  
1.  Klicken Sie auf im Menü Debuggen auf **DataTips exportieren**.  
  
     Die **DataTips exportieren** Dialogfeld wird angezeigt.  
  
2.  Mithilfe von Standarddateitechniken zu dem Speicherort navigieren, in dem Sie die XML-Datei speichern, geben Sie einen Namen für die Datei im möchten, die **Dateiname** ein, und klicken Sie dann auf **OK**.  
  
#### <a name="to-import-datatips"></a>So importieren Sie DataTips  
  
1.  Klicken Sie auf im Menü Debuggen auf **DataTips importieren**.  
  
     Die **DataTips importieren** Dialogfeld wird angezeigt.  
  
2.  Verwenden Sie das Dialogfeld, um die XML-Datei zu finden, die Sie verwenden möchten, öffnen, und klicken Sie auf **OK**.  
  
## <a name="see-also"></a>Siehe auch  
 [Anzeigen von Daten im Debugger](../debugger/viewing-data-in-the-debugger.md)   
 [Vorgehensweise: Verwenden Sie das Dialogfeld ' Schnellüberwachung '](http://msdn.microsoft.com/library/ffaee1dd-e5ce-4ef2-9401-d28329398867)   
 [Erstellen benutzerdefinierter Schnellansichten](../debugger/create-custom-visualizers-of-data.md)   
 [Vorgehensweise: Ändern des numerischen Formats von Debugger-Windows](http://msdn.microsoft.com/library/cd593847-a625-411d-a430-b798346ef18f)




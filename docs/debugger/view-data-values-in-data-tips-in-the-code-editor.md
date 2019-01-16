---
title: Anzeigen der Variablenwerte in DataTips | Microsoft-Dokumentation
ms.custom: seodec18
ms.date: 11/21/2018
ms.topic: conceptual
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 59f7b21530ff51697daca40b5c9f412682f7df89
ms.sourcegitcommit: 59c48e1e42b48ad25a4e198af670faa4d8dae370
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2019
ms.locfileid: "54204400"
---
# <a name="view-data-values-in-datatips-in-the-code-editor"></a>Anzeigen von Datenwerten in DataTips im Code-editor

DataTips stellen eine praktische Möglichkeit dar, um beim Debuggen Informationen über Variablen im Programm anzuzeigen. Sie können DataTips nur im Unterbrechungsmodus verwenden und nur mit Variablen, die sich im aktuellen Gültigkeitsbereich der Ausführung befinden. Wenn Sie zum ersten Mal versuchen, Code zu debuggen, sollten Sie [Debuggen für Einsteiger](../debugger/debugging-absolute-beginners.md) sowie [Korrigieren von Fehlern durch das Schreiben von besserem C#-Code](../debugger/write-better-code-with-visual-studio.md) lesen, bevor Sie diesen Artikel durchgehen.
  
## <a name="work-with-datatips"></a>Arbeiten mit DataTips

DataTips werden nur im Unterbrechungsmodus befindet, und nur auf Variablen, die im aktuellen Bereich der Ausführung werden angezeigt.

### <a name="display-a-datatip"></a>Einen DataTip anzeigen  
  
1. Legen Sie einen Haltepunkt im Code, und starten Sie das Debuggen durch Drücken von **F5** oder Auswahl **Debuggen** > **Debuggen starten**.
  
1. Wenn die Ausführung am Haltepunkt angehalten wird, zeigen Sie auf eine beliebige Variable im aktuellen Bereich. Ein DataTip wird angezeigt, mit den Namen und den aktuellen Wert der Variablen an.

### <a name="make-a-datatip-transparent"></a>Stellen Sie einen DataTip transparent  

Um einen DataTip transparent, Code zu sehen, die darunter liegenden, während er sich in einem DataTip ist, drücken Sie **STRG**. Der DataTip bleibt transparent, solange Sie halten die **STRG** Schlüssel. Dies funktioniert nicht für angeheftet oder unverankert DataTips.  
### <a name="pin-a-datatip"></a>PIN einem DataTip

Um einem DataTip anzuheften, damit es geöffnet bleibt, wählen Sie auf das Pinsymbol **an Quelle heften** Symbol. 

![Heften Sie einen DataTip](../debugger/media/dbg-tips-data-tips-pinned.png "heften Sie einen DataTip")

Sie können einen angehefteten DataTip verschieben, ziehen Sie es um das Codefenster. Eine Ortsmarkensymbol sieht im Bundsteg neben der Zeile, die, der mit der DataTip verknüpft ist. 

>[!NOTE]
>DataTips werden immer ausgewertet, in dem Kontext, in dem Ausführung angehalten wird, nicht der aktuelle Cursor oder DataTip-Speicherort. Wenn Sie über eine Variable in einer anderen Funktion, die den gleichen Namen wie eine Variable im aktuellen Kontext verfügt zeigen, wird der Wert der Variablen im aktuellen Kontext angezeigt.
  
### <a name="unpin-a-datatip-from-source"></a>Lösen Sie einen DataTip aus der Quelle

Um einem angehefteten DataTip "float", zeigen Sie auf der DataTip, und wählen Sie im Kontextmenü auf das Pushpin-Symbol. 

Das Pushpin-Symbol in die gelöste Position ändert, und der DataTip jetzt floats oder über alle offenen Fenster gezogen werden kann. Unverankerte DataTips wird geschlossen, wenn die Debugsitzung endet.  
  
### <a name="repin-a-datatip"></a>Einen DataTip repin  
  
Um einen unverankerten DataTip an Quelle repin, zeigen Sie darauf, im Code-Editor, und wählen Sie das Pushpin-Symbol. Das Pushpin-Symbol in die angeheftete Position ändert, und der DataTip wieder nur mit Code-Fenster verknüpft ist. 

Wenn Sie ein DataTip über ein nicht-Source-Code-Fenster unverankert ist, das Pushpin-Symbol nicht verfügbar ist und der DataTip kann nicht neu angeheftet werden. Für den Zugriff auf das Pushpin-Symbol, geben Sie den DataTip durch Ziehen oder wenn Sie den Fokus des Code-Fenster zum Code-Editor-Fenster zurück. 
  
### <a name="close-a-datatip"></a>Schließen Sie einen DataTip  
  
Klicken Sie zum Schließen Sie einen DataTip, zeigen Sie auf der DataTip, und wählen Sie schließen (**x**) Symbol aus dem Kontextmenü.  
  
### <a name="close-all-datatips"></a>Schließen Sie alle DataTips  
  
So schließen Sie alle DataTips, auf die **Debuggen** , wählen Sie im Menü **alle DataTips löschen**.  
  
### <a name="close-all-datatips-for-a-specific-file"></a>Schließen Sie alle DataTips für eine bestimmte Datei  
  
Schließen Sie alle DataTips für eine bestimmte Datei, auf die **Debuggen** , wählen Sie im Menü **Löschen aller angehefteten DataTips, \<Filename >**.  
  
## <a name="expand-and-edit-information"></a>Erweitern Sie Informationen anzeigen und bearbeiten  
Mithilfe von DataTips können Sie ein Array, eine Struktur oder ein Objekt erweitern, um deren Member anzuzeigen. Sie können mit einem DataTip auch den Wert einer Variablen bearbeiten.  
  
### <a name="expand-a-variable"></a>Erweitern Sie eine variable

Erweitern Sie ein Objekt in einem DataTip auf ihre Elemente anzuzeigen, zeigen Sie auf die Pfeile zum Erweitern vor dem Elementnamen, die die Elemente in der Strukturansicht angezeigt. Wählen Sie für die einem angehefteten DataTip den **+** bevor Sie die Variable benennen, und klicken Sie dann die Struktur zu erweitern. 

![Erweitern Sie einen DataTip](../debugger/media/dbg-tour-data-tips.png "erweitern Sie einen DataTip")

Sie können die Maus oder die Pfeiltasten auf der Tastatur verwenden, in der erweiterten Ansicht nach oben oder unten verschieben. 

Sie können auch erweiterte Elemente, die der angeheftete DataTip anheften, indem sie mit der Maus und die Pinsymbole. Die Elemente werden dann in der angeheftete DataTip angezeigt, nachdem die Struktur reduziert wird. 

### <a name="edit-the-value-of-a-variable"></a>Bearbeiten Sie den Wert einer Variablen

Um den Wert einer Variable oder ein Element in einem DataTip bearbeiten zu können, wählen Sie den Wert aus, geben Sie einen neuen Wert, und drücken Sie **EINGABETASTE**. Auswahl wird für schreibgeschützte Werte deaktiviert.  

## <a name="visualize-complex-data-types"></a>Visualisieren von komplexen Datentypen  

Ein Lupensymbol neben einer Variable oder ein Element in einem DataTip bedeutet, dass eine oder mehrere [Schnellansichten](../debugger/create-custom-visualizers-of-data.md), z. B. die [Text-Schnellansicht](../debugger/string-visualizer-dialog-box.md), stehen für die Variable. Schnellansichten werden Informationen angezeigt, in einen aussagekräftigeren manchmal, Weise.
  
Um das Element mit die Standardschnellansicht für den Datentyp zu anzuzeigen, wählen Sie das Lupensymbol ![Schnellansicht Symbol](../debugger/media/dbg-tips-visualizer-icon.png "Schnellansicht Symbol"). Wählen Sie den Pfeil neben dem Lupensymbol aus einer Liste von Schnellansichten für den Datentyp auswählen.  

## <a name="add-a-variable-to-a-watch-window"></a>Fügen Sie eine Variable ein Fenster "überwachen"  

Wenn Sie weiterhin eine Variable ansehen möchten, können Sie hinzufügen, damit eine **Watch** aus einem DataTip. Mit der rechten Maustaste in der Variable in einem DataTip, und wählen **Überwachung hinzufügen**. 

Die Variable wird angezeigt, der **Watch** Fenster. Wenn die Visual Studio-Edition, mehr als eine unterstützt **Watch** Fenster Variablen angezeigt, **Überwachen 1**. 
  
## <a name="import-and-export-datatips"></a>Importieren und Exportieren von DataTips  

Sie können DataTips in eine XML-Datei exportieren, die Sie freigeben oder mit einem Text-Editor bearbeiten können. Sie können auch eine DataTip XML-Datei importieren, empfangen oder bearbeitet haben. 
  
**Exportieren von DataTips:** 
  
1. Wählen Sie **Debuggen** > **DataTips exportieren**.  
   
1. In der **DataTips exportieren** Dialogfeld, navigieren Sie zum Speicherort, an die XML-Datei speichern, geben Sie einen Namen für die Datei, und wählen Sie dann **speichern**.  
  
**Importieren von DataTips:** 
  
1. Wählen Sie **Debuggen** > **DataTips importieren**.  
   
1. In der **DataTips importieren** Dialogfeld Feld, wählen Sie die DataTips XML-Datei, die Sie verwenden möchten, öffnen, und wählen Sie dann **öffnen**.  

## <a name="see-also"></a>Siehe auch  
 [Was bedeutet „Debuggen“?](../debugger/what-is-debugging.md)  
 [Korrigieren von Fehlern durch das Schreiben von besserem C#-Code](../debugger/write-better-code-with-visual-studio.md)  
 [Ein erster Blick auf Debuggen](../debugger/debugger-feature-tour.md) [Anzeigen von Daten im Debugger](../debugger/viewing-data-in-the-debugger.md)   
 [Fenster „Überwachen“ und „Schnellüberwachung“](../debugger/watch-and-quickwatch-windows.md)   
 [Erstellen benutzerdefinierter Schnellansichten](../debugger/create-custom-visualizers-of-data.md)   

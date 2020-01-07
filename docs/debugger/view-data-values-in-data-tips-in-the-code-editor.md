---
title: Anzeigen von Variablen Werten in DataTips | Microsoft-Dokumentation
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bf5eda8205dbe0629d0b2801473de83c2f91257e
ms.sourcegitcommit: 8e123bcb21279f2770b28696995450270b4ec0e9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/25/2019
ms.locfileid: "75404282"
---
# <a name="view-data-values-in-datatips-in-the-code-editor"></a>Anzeigen von Datenwerten in DataTips im Code-Editor

DataTips stellen eine praktische Möglichkeit dar, um beim Debuggen Informationen über Variablen im Programm anzuzeigen. Sie können DataTips nur im Unterbrechungsmodus verwenden und nur mit Variablen, die sich im aktuellen Gültigkeitsbereich der Ausführung befinden. Wenn Sie den Code zum ersten Mal debuggen möchten, sollten Sie vor dem Durcharbeiten dieses Artikels das [Debuggen für absolute Einsteiger](../debugger/debugging-absolute-beginners.md) und [Debuggingtechniken und-Tools](../debugger/write-better-code-with-visual-studio.md) lesen.

## <a name="work-with-datatips"></a>Arbeiten mit DataTips

DataTips werden nur im Break-Modus und nur in Variablen angezeigt, die sich im aktuellen Ausführungs Bereich befinden.

### <a name="display-a-datatip"></a>Anzeigen eines DataTips

1. Legen Sie einen Haltepunkt im Code fest, und starten Sie das Debugging, indem Sie **F5** drücken oder **Debuggen** > **Debugging starten**auswählen.

1. Wenn der Mauszeiger am Haltepunkt angehalten wird, zeigen Sie auf eine beliebige Variable im aktuellen Bereich. Ein DataTip wird mit dem Namen und dem aktuellen Wert der Variablen angezeigt.

### <a name="make-a-datatip-transparent"></a>Erstellen eines DataTips transparent

Um einen DataTip transparent zu machen, um Code anzuzeigen, der sich darunter befindet, drücken Sie im DataTip **STRG**. Der DataTip bleibt transparent, solange Sie die **STRG** -Taste gedrückt halten. Dies funktioniert nicht für fixierte oder Gleit Komma DataTips.
### <a name="pin-a-datatip"></a>Anheften eines DataTips

Um einen DataTip so anzuheften, dass er geöffnet bleibt, wählen Sie das Symbol **PIN an Quelle** anheften aus.

![Anheften eines DataTips](../debugger/media/dbg-tips-data-tips-pinned.png "Anheften eines DataTips")

Sie können einen angehefteten DataTip verschieben, indem Sie ihn um das Code Fenster ziehen. Ein PushPin-Symbol wird im bundbundneben der Zeile angezeigt, an die der DataTip angeheftet ist.

>[!NOTE]
>DataTips werden immer im Kontext ausgewertet, in dem die Ausführung angehalten wird, nicht der aktuelle Cursor oder DataTip-Speicherort. Wenn Sie in einer anderen Funktion mit dem Mauszeiger auf eine Variable zeigen, die denselben Namen wie eine Variable im aktuellen Kontext hat, wird der Wert der Variablen im aktuellen Kontext angezeigt.

### <a name="unpin-a-datatip-from-source"></a>DataTip aus Quelle lösen

Um einen angehefteten DataTip zu verschieben, bewegen Sie den Mauszeiger über den DataTip, und wählen Sie im Kontextmenü das PushPin-Symbol aus.

Das PushPin-Symbol ändert sich in die angeheftete Position, und der DataTip-DataTip wird jetzt über alle geöffneten Fenster hinweggezogen. Beim Beenden der Debugsitzung werden Gleit Komma DataTips geschlossen.

### <a name="repin-a-datatip"></a>DataTip-REPA

Um einen unverankerten DataTip an die Quelle zu übergeben, bewegen Sie den Mauszeiger über den Code-Editor, und wählen Sie das PushPin-Symbol aus. Das PushPin-Symbol ändert sich in die angeheftete Position, und der DataTip wird erneut an das Code Fenster angeheftet.

Wenn ein DataTip über ein nicht-Quell Code Fenster schwebt, ist das PushPin-Symbol nicht verfügbar, und der DataTip kann nicht erneut ausgeführt werden. Wenn Sie auf das PushPin-Symbol zugreifen möchten, geben Sie den DataTip im Code-Editor-Fenster an, indem Sie ihn ziehen oder dem Code Fenster den Fokus geben

### <a name="close-a-datatip"></a>Schließen eines DataTips

Um einen DataTip zu schließen, zeigen Sie mit dem Mauszeiger auf den DataTip, und wählen Sie im Kontextmenü das Symbol schließen (**x**) aus.

### <a name="close-all-datatips"></a>Alle DataTips schließen

Wenn Sie alle DataTips schließen möchten, wählen Sie im Menü **Debuggen** die Option **alle DataTips löschen**aus.

### <a name="close-all-datatips-for-a-specific-file"></a>Alle DataTips für eine bestimmte Datei schließen

Wenn Sie alle DataTips für eine bestimmte Datei schließen möchten, wählen Sie im Menü **Debuggen** die Option **alle DataTips, die an \<Dateiname >** angeheftet sind.

## <a name="expand-and-edit-information"></a>Informationen erweitern und bearbeiten
Mithilfe von DataTips können Sie ein Array, eine Struktur oder ein Objekt erweitern, um deren Member anzuzeigen. Sie können mit einem DataTip auch den Wert einer Variablen bearbeiten.

### <a name="expand-a-variable"></a>Erweitern einer Variablen

Wenn Sie ein Objekt in einem DataTip erweitern möchten, um dessen Elemente anzuzeigen, zeigen Sie mit dem Mauszeiger auf die Erweiterungs Pfeile vor den Elementnamen, um die Elemente in der Struktur Form anzuzeigen. Wählen Sie für einen angehefteten DataTip den **+** vor dem Variablennamen aus, und erweitern Sie dann die Struktur.

![DataTip erweitern](../debugger/media/dbg-tour-data-tips.png "DataTip erweitern")

Mit der Maus oder den Pfeiltasten auf der Tastatur können Sie in der erweiterten Ansicht nach oben und unten bewegen.

Sie können auch erweiterte Elemente an den angehefteten DataTip anheften, indem Sie darauf zeigen und deren pinpinsymbole auswählen. Die Elemente werden dann im angehefteten DataTip angezeigt, nachdem die Struktur reduziert wurde.

### <a name="edit-the-value-of-a-variable"></a>Bearbeiten des Werts einer Variablen

Wenn Sie den Wert einer Variablen oder eines Elements in einem DataTip bearbeiten möchten, wählen Sie den Wert aus, geben Sie einen neuen Wert ein, und drücken **Sie die Eingabe**Taste. Die Auswahl ist für schreibgeschützte Werte deaktiviert.

::: moniker range=">= vs-2019"

## <a name="pin-properties-in-datatips"></a>Anheften von Eigenschaften in DataTips

> [!NOTE]
> Dieses Feature wird für .net Core 3,0 oder höher unterstützt.

Sie können Objekte **mithilfe der Eigenschaften** in DataTips in DataTips schnell überprüfen.  Um dieses Tool zu verwenden, zeigen Sie auf eine Eigenschaft, und wählen Sie das angezeigte anheft Symbol aus, und wählen Sie im resultierenden Kontextmenü die Option **Member als Favorit** anheften aus.  Dadurch wird diese Eigenschaft an den Anfang der Eigenschaften Liste des Objekts hochskaliert, und der Eigenschaftsname und der Wert werden in der rechten Spalte des DataTip angezeigt.  Wenn Sie eine Eigenschaft lösen möchten, wählen Sie das anheft Symbol erneut aus, oder wählen Sie im Kontextmenü die Option **Member als Favorit lösen** aus.

![Fixieren einer Eigenschaft in einem DataTip](../debugger/media/basic-pin-datatip.gif "Fixieren einer Eigenschaft in einem DataTip")

Sie können Eigenschaftsnamen auch umschalten und nicht fixierte Eigenschaften herausfiltern, wenn Sie die Eigenschaften Liste des Objekts in einem DataTip anzeigen.  Sie können auf eine der beiden Optionen zugreifen, indem Sie mit der rechten Maustaste auf eine Zeile mit einer Eigenschaft klicken und im Kontextmenü die Option nur angeheftete Member **anzeigen** oder angeheftete Element **Namen in Werten ausblenden** auswählen.

::: moniker-end

## <a name="visualize-complex-data-types"></a>Visualisieren komplexer Datentypen

Ein Lupensymbol neben einer Variablen oder einem Element in einem DataTip bedeutet, dass mindestens ein Schnellansicht-Steuerelement (z. b. die [Text](../debugger/string-visualizer-dialog-box.md)Schnellansicht) für die Variable [verfügbar ist.](../debugger/create-custom-visualizers-of-data.md) Visualisierungen zeigen Informationen in einer sinnvolleren, manchmal grafischen Weise an.

Um das Element mit der Standard Schnellansicht für den Datentyp anzuzeigen, wählen Sie das Lupensymbol ![Schnellansicht aus.](../debugger/media/dbg-tips-visualizer-icon.png "Symbol Schnellansicht") Wählen Sie den Pfeil neben dem Lupensymbol aus, und wählen Sie aus einer Liste von schnell Ansichten für den Datentyp aus.

## <a name="add-a-variable-to-a-watch-window"></a>Hinzufügen einer Variablen zu einer Überwachungsfenster

Wenn Sie die Überwachung einer Variablen fortsetzen möchten, können Sie Sie einem **Überwachungs** Fenster von einem DataTip hinzufügen. Klicken Sie mit der rechten Maustaste auf die Variable im DataTip, und wählen Sie **Überwachung hinzufügen**aus.

Die Variable wird im Fenster über **Wachen** angezeigt. Wenn Ihre Visual Studio-Edition mehr als ein **Überwachungs** Fenster unterstützt, wird die Variable in **Überwachung 1**angezeigt.

## <a name="import-and-export-datatips"></a>Importieren und Exportieren von DataTips

Sie können DataTips in eine XML-Datei exportieren, die Sie mithilfe eines Text-Editors freigeben oder bearbeiten können. Sie können auch eine DataTip-XML-Datei importieren, die Sie erhalten oder bearbeitet haben.

**Exportieren von DataTips:**

1. Wählen Sie **Debuggen** > **DataTips exportieren**aus.

1. Navigieren Sie im Dialogfeld **DataTips exportieren** zu dem Speicherort, an dem die XML-Datei gespeichert werden soll, geben Sie einen Namen für die Datei ein, und klicken Sie dann auf **Speichern**.

**Importieren von DataTips:**

1. Wählen Sie **Debuggen** > **DataTips importieren**aus.

1. Wählen Sie im Dialogfeld **DataTips importieren** die DataTips-XML-Datei aus, die Sie öffnen möchten, und wählen Sie dann **Öffnen**aus.

## <a name="see-also"></a>Siehe auch
- [What is debugging? (Was bedeutet „Debuggen“?)](../debugger/what-is-debugging.md)
- [Debugging techniques and tools (Debugverfahren und -tools)](../debugger/write-better-code-with-visual-studio.md)
- [Erster Einblick in das Debuggen](../debugger/debugger-feature-tour.md)
- [Anzeigen von Daten im Debugger](../debugger/viewing-data-in-the-debugger.md)
- [Fenster "Überwachen" und "Schnellüberwachung"](../debugger/watch-and-quickwatch-windows.md)
- [Erstellen benutzerdefinierter Schnellansichten](../debugger/create-custom-visualizers-of-data.md)

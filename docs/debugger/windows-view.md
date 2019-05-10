---
title: Windows-Ansicht | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.externaltools.spyplus.windowsview
helpviewer_keywords:
- Windows view
ms.assetid: 154786ce-c803-4bfb-8198-f7962a900363
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fef652cbaa83fde61f098fb8fcef9558473fe19a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62900857"
---
# <a name="windows-view"></a>Fensteransicht
Wenn Sie erstmalig Spy++ öffnen, zeigt Windows-Ansicht eine Struktur mit allen Windows- und Steuerelemente im System. Werden die Fenster-Handle und die Klasse angezeigt. Das aktuelle Desktopfenster ist am Anfang der Struktur. Alle anderen Fenster sind untergeordnete Elemente des Desktops, und anhand der Hierarchie Standardfenster aufgeführt sind. Gleichgeordnete Fenster werden im erweiterbaren Listen unter der übergeordneten Elemente eingezogen angezeigt.

 Die folgende Abbildung zeigt eine typische Spy++-Windows-Ansicht mit den obersten Knoten erweitert.

 ![Spy++&#43; &#43; Windows-Ansicht](../debugger/media/spy--_windowsview.png "Spy-_WindowsView") Spy++-Windows-Ansicht

 Das aktuelle Desktopfenster ist am Anfang der Struktur. Alle anderen Fenster sind untergeordnete Elemente des Desktops, und werden anhand der Hierarchie Standardfenster mit nebengeordnete Fenster nach Z-Reihenfolge geordnet aufgeführt. Sie können erweitern oder reduzieren Sie alle übergeordneten Knoten der Struktur, indem Sie auf das + oder - Symbol neben dem Knoten.

 Windows-Ansicht den Fokus hat, können Sie das Suchtool im Verwenden der [Fenster Meldungssuche (Dialogfeld)](../debugger/window-search-dialog-box.md) zum Anzeigen von Informationen in einem beliebigen geöffneten Fenster auf Ihrem System.

## <a name="in-this-section"></a>In diesem Abschnitt
 [Vorgehensweise: Verwenden des Suchtools](../debugger/how-to-use-the-finder-tool.md) zeigt, wie dieses Tool Windows für die Eigenschaften oder Meldungen überprüft.

 [Vorgehensweise: Suchen nach einem Fenster in der Windows-Ansicht](../debugger/how-to-search-for-a-window-in-windows-view.md) wird erläutert, wie Sie ein bestimmtes Fenster in der Windows-Ansicht.

 [Vorgehensweise: Anzeigen von Fenstereigenschaften](../debugger/how-to-display-window-properties.md) m Verfahren zum Öffnen das Dialogfeld "Eigenschaften".

## <a name="related-sections"></a>Verwandte Abschnitte
 [Spy++-Ansichten](../debugger/spy-increment-views.md) wird erläutert, die Spy++-Strukturansichten von Windows, Nachrichten, Prozesse und Threads.

 [Verwenden von Spy++](../debugger/using-spy-increment.md) stellt die Spy++-Tools vor und erläutert, wie sie verwendet werden kann.

 [Suchen Sie im Dialogfeld Fenster](../debugger/find-window-dialog-box.md) verwendet, um die Eigenschaften oder Nachrichten von einem bestimmten Fenster anzuzeigen.

 [Das Dialogfeld Fenstersuche](../debugger/window-search-dialog-box.md) verwendet, um den Knoten für ein bestimmtes Fenster in der Windows-Ansicht zu suchen.

 [Dialogfeld "Fenstereigenschaften"](../debugger/window-properties-dialog-box.md) verwendet zum Anzeigen der Eigenschaften eines Fensters in Windows-Ansicht ausgewählt.

 [Spy++-Referenz](../debugger/spy-increment-reference.md) enthält Abschnitte, die jedes Spy++ Menü- und Dialogfeldressourcen Feld beschreibt.
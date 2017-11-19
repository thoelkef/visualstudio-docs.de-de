---
title: 'Vorgehensweise: Suchen nach einem Fenster in der Fensteransicht | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: windows, searching in Windows view
ms.assetid: 30306970-b861-4315-acf8-f86a43d4e73b
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 81b970979759c7ef6a6b236a1f2dff34815a72d9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-search-for-a-window-in-windows-view"></a>Gewusst wie: Suchen nach einem Fenster in der Fensteransicht
Sie können mithilfe des Handles, Beschriftung, Klasse oder eine Kombination von Beschriftung und Klasse als Suchkriterium für ein bestimmtes Fenster in der Fensteransicht suchen. Sie können auch die ausgangsrichtung der Suche angeben. Die Felder im Dialogfeld werden die Attribute des das ausgewählte Fenster in der Fensterstruktur im angezeigt.  
  
 Beginnen Sie mit der Struktur auf der zweiten Ebene (alle Fenster, die untergeordnete Elemente des Desktops), erweitert, damit Sie-Desktop auf Dokumentebene Windows nach Klassennamen und Titel identifizieren können. Sobald Sie eine Desktop-Level-Fenster ausgewählt haben, können Sie dieser Ebene ein bestimmtes untergeordnetes Fenster zu erweitern.  
  
### <a name="to-search-for-a-window-in-windows-view"></a>Suchen Sie für ein Fenster in der Fensteransicht  
  
1.  Ordnen Sie die Fenster so, Spy++, die [Fensteransicht](../debugger/windows-view.md) Fenster und die Fenster "Ziel" sichtbar sind.  
  
2.  Aus der **Suche** Menü wählen **"Fenster Suchen"**.  
  
     Die [Fenster-Dialogfeld "Fenstersuche"](../debugger/window-search-dialog-box.md) wird geöffnet.  
  
    > [!TIP]
    >  Wählen Sie zum Bildschirm übersichtlicher gestalten möchten, die **Spy++ ausblenden** Option. Mit dieser Option das Hauptfenster Spy++ verbirgt und bewirkt, dass nur die **Fenstersuche** (Dialogfeld), die zusätzlich zu anderen Anwendungen sichtbar. Spy++-Hauptfenster wird wiederhergestellt, wenn Sie auf **OK** oder **"Abbrechen"**, oder wenn Sie deaktivieren die **Spy++ ausblenden** Option.  
  
3.  Ziehen Sie die **Suchtools** über dem Zielfenster. Wie Sie das Tool, ziehen Sie die **Fenstersuche** Dialogfeld zeigt Details für das ausgewählte Fenster.  
  
     - ODER  
  
     Sie kennen das Handle des Fensters werden sollen (z. B. aus dem Debugger), geben Sie ihn in die **behandeln** Feld.  
  
     - ODER  
  
     Sie kennen die Beschriftung und/oder die Klasse des Fensters werden sollen, geben Sie in der **Beschriftung** und **Klasse** Textfelder, und Deaktivieren der **behandeln** Textfeld.  
  
4.  Wählen Sie **einrichten** oder **unten** für die anfängliche Richtung der Suche.  
  
5.  Klicken Sie auf **OK**.  
  
     Wenn ein entsprechendes Fenster gefunden wird, wird es hervorgehoben, der [Fensteransicht](../debugger/windows-view.md) Fenster.
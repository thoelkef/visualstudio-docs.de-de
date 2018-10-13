---
title: 'Vorgehensweise: Suchen nach einem Fenster in der Windows-Ansicht | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- windows, searching in Windows view
ms.assetid: 30306970-b861-4315-acf8-f86a43d4e73b
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9cd33d8c7414d4db989533475a328ca8abf2ffdb
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49295060"
---
# <a name="how-to-search-for-a-window-in-windows-view"></a>Gewusst wie: Suchen nach einem Fenster in der Fensteransicht
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können für ein bestimmtes Fenster in der Windows-Ansicht mit das Handle, Beschriftung, Klasse oder eine Kombination der Beschriftung und die Klasse als Suchkriterium suchen. Sie können auch die anfangsrichtung für die Suche angeben. Die Felder im Dialogfeld werden die Attribute des ausgewählten Fensters in der Fensterstruktur im angezeigt werden.  
  
 Beginnen Sie mit der Struktur auf der zweiten Ebene (alle Fenster, die untergeordnete Elemente des Desktops), erweitert, damit Sie Windows-Desktop auf von ihren Klassennamen und den Titel identifizieren können. Nachdem Sie ein Fenster auf Desktop-Ebene ausgewählt haben, können Sie dieser Ebene um ein bestimmtes untergeordnetes Fenster suchen erweitern.  
  
### <a name="to-search-for-a-window-in-windows-view"></a>Suchen Sie nach einem Fenster in Windows-Ansicht  
  
1.  Ordnen Sie die Fenster also, Spy++, die [Windows-Ansicht](../debugger/windows-view.md) Fenster und das Ziel sind sichtbar.  
  
2.  Von der **Suche** Menü wählen **Fenster Suchen**.  
  
     Die [Dialogfeld Fenstersuche](../debugger/window-search-dialog-box.md) wird geöffnet.  
  
    > [!TIP]
    >  Um die Übersichtlichkeit des Bildschirms, wählen Sie die **Spy++ ausblenden** Option. Mit dieser Option das Hauptfenster Spy++ verbirgt und verbleibt nur der **Fenstersuche** Dialogfeld sichtbar ist, zusätzlich zu anderen Anwendungen. Spy++-Hauptfenster wird wiederhergestellt, wenn Sie auf **OK** oder **Abbrechen**, oder wenn Sie das Kontrollkästchen der **Spy++ ausblenden** Option.  
  
3.  Ziehen Sie die **Suchtool** über das Zielfenster. Wie Sie das Tool, ziehen Sie die **Fenstersuche** Dialogfeld zeigt die Details für das ausgewählte Fenster.  
  
     – oder –  
  
     Wenn Sie wissen das Handle des Fensters werden sollen (z. B. aus dem Debugger), können Sie eingeben, in der **behandeln** Feld.  
  
     – oder –  
  
     Wenn Sie wissen, die Beschriftung und/oder die Klasse des Fensters werden sollen, können Sie eingeben, in der **Beschriftung** und **Klasse** Textfelder, und Deaktivieren der **behandeln** Textfeld.  
  
4.  Wählen Sie **einrichten** oder **unten** für die anfängliche Richtung für die Suche.  
  
5.  Klicken Sie auf **OK**.  
  
     Wenn ein entsprechendes Fenster gefunden wird, ist die Hervorhebung der [Windows-Ansicht](../debugger/windows-view.md) Fenster.




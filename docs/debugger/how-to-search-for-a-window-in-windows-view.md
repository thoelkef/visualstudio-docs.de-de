---
title: "How to: Search for a Window in Windows View | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "windows, searching in Windows view"
ms.assetid: 30306970-b861-4315-acf8-f86a43d4e73b
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# How to: Search for a Window in Windows View
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können in der Fensteransicht ein Fenster suchen, indem Sie das Handle, die Beschriftung, die Klasse oder eine Kombination von Beschriftung und Klasse des Fensters als Suchkriterium verwenden.  Sie können auch die anfängliche Suchrichtung angeben.  In den Feldern des Dialogfelds werden die Attribute des in der Fensterstruktur ausgewählten Fensters angezeigt.  
  
 Beginnen Sie mit der auf die zweite Ebene erweiterten Struktur \(alle Fenster, die untergeordnete Elemente des Desktops sind\), damit Sie Fenster auf der Desktopebene anhand ihres Klassennamens und Titels identifizieren können.  Sobald Sie ein Fenster auf der Desktopebene ausgewählt haben, können Sie diese Ebene erweitern, um ein bestimmtes untergeordnetes Fenster zu suchen.  
  
### So suchen Sie ein Fenster in der Fensteransicht  
  
1.  Ordnen Sie die Fenster so an, dass Spy\+\+, das [Fensteransichtsfenster](../debugger/windows-view.md) und das Zielfenster sichtbar sind.  
  
2.  Klicken Sie im Menü **Suchen** auf **Fenster suchen**.  
  
     Das Dialogfeld [Fenstersuche](../debugger/window-search-dialog-box.md) wird geöffnet.  
  
    > [!TIP]
    >  Um die Übersichtlichkeit des Bildschirms zu erhöhen, aktivieren Sie die Option **Spy\+\+ ausblenden**.  Mit dieser Option wird das Spy\+\+\-Hauptfenster ausgeblendet, und nur das Dialogfeld **Fenstersuche** bleibt über den anderen Anwendungen sichtbar.  Das Spy\+\+\-Hauptfenster wird wiederhergestellt, wenn Sie auf **OK** oder **Abbrechen** klicken, oder wenn Sie die Option **Spy\+\+ ausblenden** deaktivieren.  
  
3.  Ziehen Sie das **Suchtool** auf das Zielfenster.  Während Sie das Tool ziehen, werden im Dialogfeld **Fenstersuche** Details zum ausgewählten Fenster angezeigt.  
  
     – oder –  
  
     Wenn Sie das Handle das gewünschten Fensters kennen \(z. B. aus dem Debugger\), können Sie es im Feld **Handle** eingeben.  
  
     – oder –  
  
     Wenn Sie die Beschriftung und\/oder die Klasse des gewünschten Fensters kennen, können Sie sie in den Textfeldern **Beschriftung** und **Klasse** eingeben und das Textfeld **Handle** löschen.  
  
4.  Wählen Sie als anfängliche Richtung der Suche **Nach oben** oder **Nach unten** aus.  
  
5.  Klicken Sie auf **OK**.  
  
     Wenn ein entsprechendes Fenster gefunden wird, wird es im Fenster [Fensteransicht](../debugger/windows-view.md) hervorgehoben.
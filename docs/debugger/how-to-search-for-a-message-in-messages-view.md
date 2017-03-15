---
title: "How to: Search for a Message in Messages View | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Message Search dialog box"
  - "Messages view"
  - "messages, searching for"
ms.assetid: 732b7ccc-54ea-41db-823b-2b96e3e4083e
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# How to: Search for a Message in Messages View
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können in der Meldungsansicht eine bestimmte Meldung suchen, indem Sie das Handle, den Typ oder die Meldungs\-ID der Meldung als Suchkriterium verwenden.  Jede dieser Angaben – oder eine Kombination von ihnen – ist ein gültiges Suchkriterium.  Die anfängliche Suchrichtung kann ebenfalls angegeben werden.  Die Felder im Dialogfeld werden mit den Attributen der gegenwärtig ausgewählten Meldung vorab geladen.  
  
### So suchen Sie in der Meldungsansicht eine Meldung  
  
1.  Ordnen Sie die Fenster so an, dass Spy\+\+ und das aktive [Meldungsansichtsfenster](../debugger/messages-view.md) sichtbar sind.  
  
2.  Klicken Sie im Menü **Suchen** auf **Meldung suchen**.  
  
     Das Dialogfeld [Meldungssuche](../debugger/message-search-dialog-box.md) wird geöffnet.  
  
3.  Ziehen Sie das **Suchtool** auf das gewünschte Fenster.  Während Sie das Tool ziehen, werden im Dialogfeld **Meldungssuche** Details zum ausgewählten Fenster angezeigt.  
  
     – oder –  
  
     Wenn Sie über das Handle des Fensters verfügen, dessen Meldungen Sie untersuchen möchten, geben Sie es im Textfeld **Handle** ein.  
  
     – oder –  
  
     Wenn Sie den gewünschten Meldungstyp und\/oder die gewünschte Meldungs\-ID kennen, wählen Sie diese in den Dropdownmenüs **Typ** und **Meldung** aus, und löschen das Textfeld **Handle**.  
  
4.  Löschen Sie alle Felder, für die Sie keine Werte angeben möchten.  
  
    > [!TIP]
    >  Um die Übersichtlichkeit des Bildschirms zu erhöhen, aktivieren Sie die Option **Spy\+\+ ausblenden**.  Mit dieser Option wird das Spy\+\+\-Hauptfenster ausgeblendet, sodass nur das Dialogfeld **Fenster suchen** über den anderen Anwendungen sichtbar bleibt.  Das Spy\+\+\-Hauptfenster wird wiederhergestellt, wenn Sie auf **OK** oder **Abbrechen** klicken, oder wenn Sie die Option **Spy\+\+ ausblenden** deaktivieren.  
  
5.  Wählen Sie als anfängliche Richtung der Suche **Nach oben** oder **Nach unten** aus.  
  
6.  Klicken Sie auf **OK**.  
  
 Wenn eine entsprechende Meldung gefunden wird, wird sie im Meldungsansichtsfenster hervorgehoben.  Informationen hierzu finden Sie unter [Meldungsansicht](../debugger/messages-view.md).
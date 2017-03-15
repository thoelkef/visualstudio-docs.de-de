---
title: "How to: Use the Finder Tool | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Window Finder Tool"
ms.assetid: 5841926b-08c3-4e43-88bd-4223d04f9aef
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# How to: Use the Finder Tool
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können das Suchtool im Dialogfeld **Fenster suchen** verwenden, um Fenstereigenschaften oder Meldungen anzuzeigen.  Das Suchtool kann auch deaktivierte untergeordnete Fenster suchen, und es erkennt, welches Fenster hervorgehoben werden muss, wenn sich deaktivierte untergeordnete Fenster überlappen.  
  
 ![Spy&#43;&#43;&#45;Dialogfeld "Fenster suchen"](../debugger/media/icon_spy--_find.png "Icon\_Spy\+\+\_Find")  
Suchtool im Dialogfeld "Fenster suchen"  
  
 In der obigen Abbildung wird die Darstellung des Dialogfelds "Fenster suchen" nach dem unten beschriebenen Schritt 3 gezeigt.  
  
### So zeigen Sie Fenstereigenschaften oder \-meldungen an  
  
1.  Ordnen Sie die Fenster so an, dass sowohl Spy\+\+ als auch das Zielfenster sichtbar sind.  
  
2.  Klicken Sie im Menü **Spy** auf **Fenster suchen**.  
  
     Das Dialogfeld [Fenster suchen](../debugger/find-window-dialog-box.md) wird geöffnet.  
  
3.  Ziehen Sie das **Suchtool** auf das Zielfenster.  
  
     Während Sie das Tool ziehen, werden im Dialogfeld **Fenster suchen** Details zum ausgewählten Fenster angezeigt.  
  
     – oder –  
  
     Wenn Sie über das Handle des zu untersuchenden Fensters verfügen \(beispielsweise aus dem Debugger kopiert\), geben Sie es im Textfeld **Handle** ein.  
  
    > [!TIP]
    >  Um die Übersichtlichkeit des Bildschirms zu erhöhen, aktivieren Sie die Option **Spy\+\+ ausblenden**.  Mit dieser Option wird das Spy\+\+\-Hauptfenster ausgeblendet, sodass nur das Dialogfeld **Fenster suchen** über den anderen Anwendungen sichtbar bleibt.  Das Spy\+\+\-Hauptfenster wird wiederhergestellt, wenn Sie auf **OK** oder **Abbrechen** klicken, oder wenn Sie die Option **Spy\+\+ ausblenden** deaktivieren.  
  
4.  Wählen Sie unter **Anzeigen** entweder **Eigenschaften** oder **Meldungen** aus.  
  
5.  Klicken Sie auf **OK**.  
  
     Wenn Sie **Eigenschaften** ausgewählt haben, wird das Dialogfeld [Fenstereigenschaften](../debugger/window-properties-dialog-box.md) geöffnet.  Wenn Sie **Meldungen** ausgewählt haben, wird ein [Meldungsansichtsfenster](../debugger/messages-view.md) geöffnet.  
  
## Siehe auch  
 [Spy\+\+ Views](../debugger/spy-increment-views.md)   
 [Using Spy\+\+](../debugger/using-spy-increment.md)   
 [Spy\+\+ Reference](../debugger/spy-increment-reference.md)
---
title: 'Vorgehensweise: Verwenden des Suchtools | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Window Finder Tool
ms.assetid: 5841926b-08c3-4e43-88bd-4223d04f9aef
caps.latest.revision: 9
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 00535fd336f504afcebdd24a4d009a10f7f6ff33
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841124"
---
# <a name="how-to-use-the-finder-tool"></a>Vorgehensweise: Verwenden des Suchtools
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können das Suchtool im Dialogfeld **Fenster suchen** verwenden, um Fenstereigenschaften oder Meldungen anzuzeigen. Mit dem Suchtool können auch deaktivierte untergeordnete Fenster gesucht werden, und es kann erkennen, welches Fenster hervorgehoben werden soll, wenn sich deaktivierte untergeordnete Fenster überlappen.  
  
 ![Spy&#43;&#43; Dialog Feld "Fenster Suchen"](../debugger/media/icon-spy-find.png "Icon_Spy++_Find")  
Finder-Tool im Dialogfeld "Fenster Suchen"  
  
 Die obige Abbildung zeigt das Dialogfeld „Fenster suchen“ nach Schritt 3.  
  
### <a name="to-display-window-properties-or-messages"></a>So zeigen Sie Fenstereigenschaften oder Meldungen an  
  
1. Ordnen Sie die Fenster so an, dass sowohl Spy++ als auch das Zielfenster sichtbar sind.  
  
2. Wählen Sie im Menü **Spy** die Option **Fenster suchen** aus.  
  
     Das [Dialogfeld „Fenster suchen“](../debugger/find-window-dialog-box.md) wird geöffnet.  
  
3. Ziehen Sie das **Suchtool** über das Zielfenster.  
  
     Wenn Sie das Tool ziehen, werden im Dialogfeld **Fenster suchen** Informationen zum ausgewählten Fenster angezeigt.  
  
     – oder –  
  
     Wenn Sie über das Handle des zu untersuchenden Fensters verfügen, (z. B. aus dem Debugger kopiert), geben Sie es im Textfeld **Handle** ein.  
  
    > [!TIP]
    > Damit der Bildschirm übersichtlich bleibt, wählen Sie die Option **Spy++ ausblenden** aus. Mit dieser Option wird das Spy++-Hauptfenster verborgen, sodass nur das Dialogfeld **Fenster suchen** über den anderen Anwendungen angezeigt wird. Das Spy++-Hauptfenster wird wiederhergestellt, wenn Sie auf **OK** oder **Abbrechen** klicken oder die Option **Spy++ ausblenden** deaktivieren.  
  
4. Wählen Sie unter **Anzeigen** entweder **Eigenschaften** oder **Meldungen** aus.  
  
5. Klicken Sie auf **OK**.  
  
     Wenn Sie **Eigenschaften** ausgewählt haben, wird das [Dialogfeld „Fenstereigenschaften“](../debugger/window-properties-dialog-box.md) geöffnet. Wenn Sie **Meldungen** ausgewählt haben, wird das [Meldungsansichtsfenster](../debugger/messages-view.md) geöffnet.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Spy + +-Ansichten](../debugger/spy-increment-views.md)   
 [Verwenden von Spy + +](../debugger/using-spy-increment.md)   
 [Spy++-Referenz](../debugger/spy-increment-reference.md)

---
title: 'Vorgehensweise: Debuggen von ActiveX-Steuerelementen | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vc.controls.debug
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- testing [Visual Studio], test containers
- ActiveX control container debugging [Visual Studio]
- debugging ActiveX controls
- data-bound controls, ActiveX
- test container
- containers, specifying for debug sessions
- ActiveX controls, debugging
- testing [Visual Studio], ActiveX controls
ms.assetid: bbc02cf7-a7e6-44fe-99af-87a43e1d7251
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cc47ba913ba9da1ecfe8e0df34894c31545e1734
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47513665"
---
# <a name="how-to-debug-an-activex-control"></a>Gewusst wie: Debuggen von ActiveX-Steuerelementen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Vorgehensweise: Debuggen von ActiveX-Steuerelementen](https://docs.microsoft.com/visualstudio/debugger/how-to-debug-an-activex-control).  
  
HINWEIS]
>  Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen. Klicken Sie im Menü Extras auf Einstellungen importieren und exportieren, um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Anpassen der Entwicklungseinstellungen in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Um das ActiveX-Steuerelement zu debuggen, müssen Sie einen Container (ausführbare Datei) angeben, in dem das Steuerelement ausgeführt werden kann.  
  
### <a name="to-specify-a-container-for-the-debug-session"></a>So legen Sie einen Container für die Debugsitzung fest  
  
1.  Wählen Sie im Projektmappen-Explorer das Projekt aus.  
  
2.  Von der **Ansicht** Menü wählen **Eigenschaftenseiten**.  
  
3.  In der **Project Property Pages** öffnen Sie im Dialogfeld die **Konfigurationseigenschaften** Ordner, und wählen **Debuggen**.  
  
4.  Unter den **Debuggen** (Kategorie), suchen Sie die **Befehl** Eigenschaft.  
  
5.  Geben Sie den Pfadnamen für den Container an. Beispielsweise C:\Programme\Internet Explorer\IEXPLORE.EXE.  
  
6.  Wenn Sie Internet Explorer als Container angeben, und Sie Active Desktop verwenden, geben Sie `/new` in die **Befehlsargumente** Feld.  
  
7.  Klicken Sie auf **OK**.  
  
     Wenn Sie keinen Container im Angeben der **Project Property Pages** im Dialogfeld können Sie den Container angeben, wenn Debuggen zu beginnen. Wenn Sie einen Ausführungsbefehl zum Starten des Debugvorgangs Auswählen der [ausführbare Datei für die Sitzung Dialogfeld Debuggen](../debugger/executable-for-debugging-session-dialog-box.md) angezeigt wird. Geben Sie den Pfadnamen des Containers im Dialogfeld an.  
  
## <a name="see-also"></a>Siehe auch  
 [ActiveX-Steuerelemente](http://msdn.microsoft.com/library/52aaec4d-3889-402e-b57d-758078f8ac57)   
 [Testen der Eigenschaften und Ereignisse mit Testcontainer](http://msdn.microsoft.com/library/626867cf-fe53-4c30-8973-55bb93ef3917)   
 [Debuggen von COM und ActiveX](../debugger/com-and-activex-debugging.md)   
 [Debuggen in Visual Studio](../debugger/debugging-in-visual-studio.md)




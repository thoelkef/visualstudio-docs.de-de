---
title: 'Vorgehensweise: Debuggen von ActiveX-Steuerelement | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vc.controls.debug
dev_langs:
- CSharp
- VB
- FSharp
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8892d83bb92198b9e8f1b7df1293a06f27d27716
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
ms.locfileid: "31474426"
---
# <a name="how-to-debug-an-activex-control"></a>Gewusst wie: Debuggen von ActiveX-Steuerelementen
> [!NOTE]
>  Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen. Klicken Sie im Menü Extras auf Einstellungen importieren und exportieren, um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../ide/personalizing-the-visual-studio-ide.md).  
  
 Um das ActiveX-Steuerelement zu debuggen, müssen Sie einen Container (ausführbare Datei) angeben, in dem das Steuerelement ausgeführt werden kann.  
  
### <a name="to-specify-a-container-for-the-debug-session"></a>So legen Sie einen Container für die Debugsitzung fest  
  
1.  Wählen Sie im Projektmappen-Explorer das Projekt aus.  
  
2.  Aus der **Ansicht** Menü wählen **Eigenschaftenseiten**.  
  
3.  In der **Projekteigenschaftenseiten** öffnen Sie im Dialogfeld die **Konfigurationseigenschaften** Ordner, und wählen **Debuggen**.  
  
4.  Unter den **Debuggen** Kategorie, suchen Sie die **Befehl** Eigenschaft.  
  
5.  Geben Sie den Pfadnamen für den Container an. Beispielsweise C:\Programme\Internet Explorer\IEXPLORE.EXE.  
  
6.  Wenn Sie Internet Explorer als Container angeben und Active Desktop verwenden, geben Sie `/new` in der **Befehlsargumente** Feld.  
  
7.  Klicken Sie auf **OK**.  
  
     Wenn Sie keinen Container angeben der **Projekteigenschaftenseiten** (Dialogfeld), können Sie den Container angeben, wenn Sie mit dem Debuggen beginnen. Wenn Sie zum Starten des Debugvorgangs einen Ausführungsbefehl wählen Sie die [ausführbare Datei für die Sitzung Dialogfeld Debuggen](../debugger/executable-for-debugging-session-dialog-box.md) angezeigt wird. Geben Sie den Pfadnamen des Containers im Dialogfeld an.  
  
## <a name="see-also"></a>Siehe auch  
 [ActiveX-Steuerelemente](/cpp/mfc/activex-controls)   
 [Testen der Eigenschaften und Ereignisse mit Testcontainer](/cpp/mfc/testing-properties-and-events-with-test-container)   
 [COM und ActiveX-Debugging](../debugger/com-and-activex-debugging.md)   
 [Debuggen in Visual Studio](../debugger/index.md)  
 [Debugger – Featuretour](../debugger/debugger-feature-tour.md)
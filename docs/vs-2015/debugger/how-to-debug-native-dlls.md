---
title: 'Vorgehensweise: Debuggen von nativen DLLs | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.dll
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging DLLs
- DLLs, debugging
- executable files, specifying for debug sessions
ms.assetid: 76b34d15-a66d-4963-842e-c8b955c81696
caps.latest.revision: 20
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 16a533b27e619526edab71374d922e68baf0a4b0
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "65702682"
---
# <a name="how-to-debug-native-dlls"></a>Vorgehensweise: Debuggen von systemeigenen DLLs
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

> [!NOTE]
> Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen. Klicken Sie im Menü Extras auf Einstellungen importieren und exportieren, um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Anpassen der Entwicklungseinstellungen in Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Das Debuggen einer DLL kann über die folgenden Projekte gestartet werden:  
  
- Über das Projekt, das zum Erstellen der ausführbaren Datei verwendet wurde, durch die die DLL aufgerufen wird.  
  
  \- oder –  
  
- Über das Projekt, durch das die DLL selbst erstellt wurde.  
  
  Falls das Projekt, mit dem die ausführbare Datei erstellt wurde, verfügbar ist, starten Sie den Debugvorgang über dieses Projekt. Sie können dann eine Quelldatei für die DLL öffnen und in dieser Datei Haltepunkte festlegen. Dies gilt auch, wenn die Datei nicht dem Projekt angehört, mit dem die ausführbare Datei erstellt wurde. Weitere Informationen finden Sie unter [Breakpoints (Haltepunkte)](https://msdn.microsoft.com/fe4eedc1-71aa-4928-962f-0912c334d583).  
  
  Wenn Sie den Debugvorgang über das Projekt starten, mit dem die DLL erstellt wird, müssen Sie die ausführbare Datei angeben, die beim Debuggen der DLL verwendet werden soll.  
  
### <a name="to-specify-an-executable-for-the-debug-session"></a>So legen Sie eine ausführbare Datei für die Debugsitzung fest  
  
1. In **Projektmappen-Explorer**, wählen Sie das Projekt, das die DLL erstellt.  
  
2. Von der **Ansicht** Menü wählen**Eigenschaftenseiten**.  
  
3. In der **Eigenschaftenseiten** öffnen Sie im Dialogfeld die **Konfigurationseigenschaften** Ordner, und wählen die **Debuggen** Kategorie.  
  
4. In der **Befehl** geben den Pfadnamen für den Container. Beispielsweise C:\Programme\MeineAnwendung\MEINEANW.EXE.  
  
5. In der **Befehlsargumente** geben erforderlichen Argumente für die ausführbare Datei.  
  
   Wenn Sie nicht die ausführbare Datei in angeben der _Projekt_**Eigenschaftenseiten** im Dialogfeld die [ausführbare für Dialogfeld "Sitzung" Debuggen](../debugger/executable-for-debugging-session-dialog-box.md) angezeigt wird, wenn Sie das Debuggen starten.  
  
## <a name="see-also"></a>Siehe auch  
 [Debugger Security (Debuggersicherheit)](../debugger/debugger-security.md)   
 [Debuggen in Visual Studio](../debugger/debugging-in-visual-studio.md)

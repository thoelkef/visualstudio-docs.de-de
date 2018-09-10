---
title: 'Gewusst wie: Debuggen einer ausführbaren Datei, die nicht Teil von Visual Studio-Projektmappe ist | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugging [Visual Studio], executables
- executable files, importing
- executable files, debugging outside of projects
ms.assetid: 3ea176e8-1ce5-42c4-b7a2-abe3a2765033
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ce84c4acdc2cf4324c76dbbf7fe0b39ca9715b3c
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/10/2018
ms.locfileid: "44279097"
---
# <a name="how-to-debug-an-executable-that-is-not-part-of-a-visual-studio-solution"></a>Gewusst wie: Debuggen einer ausführbaren Datei, die nicht Teil von Visual Studio-Projektmappe ist
In einigen Fällen sollten Sie zum Debuggen von einer ausführbaren Datei (.exe-Datei), die nicht Teil einer [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Projekt. Die ausführbare Datei wurde möglicherweise außerhalb von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] erstellt, oder sie stammt von einem anderen Entwickler.  
  
Dieses Problem wird normalerweise dadurch gelöst, dass die ausführbare Datei außerhalb von Visual Studio gestartet und mithilfe des [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Debuggers angehängt wird. Weitere Informationen finden Sie unter [Anfügen an ausgeführte Prozesse](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
Das Anfügen an eine Anwendung erfordert einige manuelle Schritte, die einige Sekunden dauern können. Diese kurze Verzögerung hat zur Folge, dass das Anfügen keine Abhilfe schafft, wenn Sie einen Fehler debuggen, der während des Startens auftritt. Auch beim Debuggen eines Programms, das keine Benutzereingaben erwartet und dessen Ausführung relativ schnell beendet ist, reicht die Zeit zum Anfügen u. U. nicht aus. Wenn man [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] und [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] installiert haben, können Sie für ein solches Programm ein EXE-Projekt erstellen.

> [!NOTE]
>  EXE-Projekte werden nicht von allen Programmiersprachen unterstützt.

Beim Debuggen einer ausführbaren Datei, die nicht Teil von Visual Studio-Projektmappe ist, die verfügbaren Debugfunktionen möglicherweise beschränkt, egal ob Sie an eine ausführbare Datei ausgeführt wird anfügen, oder fügen die ausführbare Datei eine [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Lösung.

- Falls der Quellcode verfügbar ist, empfiehlt es sich, den Quellcode in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zu importieren und ein Debugbuild der ausführbaren Datei in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zu erstellen.
- Wenn Sie nicht über den Quellcode verfügen und die ausführbare Datei erstellt wurde, ohne [Debuginformationen](../debugger/how-to-set-debug-and-release-configurations.md) in einem kompatiblen Format zur Verfügung Debugfunktionen sehr begrenzt sind. 
  
### <a name="to-create-an-exe-project-for-an-existing-executable"></a>So erstellen Sie ein EXE-Projekt für eine vorhandene ausführbare Datei  
  
1.  Auf der **Datei** Menü klicken Sie auf **öffnen** , und wählen Sie **Projekt**.  
  
2.  In der **geöffneten Projekt** (Dialogfeld), klicken Sie auf die Dropdownliste neben der **Dateiname** , und wählen Sie **alle Projektdateien**.  
  
3.  Suchen Sie die ausführbare Datei, und klicken Sie auf **OK**.  

    Auf diese Weise wird eine temporäre Projektmappe erstellt, in der die ausführbare Datei enthalten ist.

5.  Starten Sie die ausführbare Datei, indem Sie einen Ausführungsbefehl, z. B. **starten**, aus der **Debuggen** Menü.    
  
### <a name="to-import-an-executable-into-a-visual-studio-solution"></a>So importieren Sie eine ausführbare Datei in eine Visual Studio-Projektmappe  
  
1.  Auf der **Datei** Startmenü **Projekt hinzufügen**, und klicken Sie dann auf **vorhandenes Projekt**.  
  
2.  In der **vorhandenes Projekt hinzufügen** (Dialogfeld), klicken Sie auf die Dropdownliste neben der **Dateiname** , und wählen Sie **alle Projektdateien**.  
  
3.  Suchen Sie die ausführbare Datei, und wählen Sie sie aus.  
  
4.  Klicken Sie auf **OK**.  
  
5.  Starten Sie die ausführbare Datei, indem Sie einen Ausführungsbefehl, z. B. **starten**, aus der **Debuggen** Menü.    
  
## <a name="see-also"></a>Siehe auch  
 [Debuggereinstellungen und -vorbereitung](../debugger/debugger-settings-and-preparation.md)   
 [Debuggersicherheit](../debugger/debugger-security.md)   
 [DBG-Dateien](/previous-versions/visualstudio/visual-studio-2010/da528y14(v=vs.100))
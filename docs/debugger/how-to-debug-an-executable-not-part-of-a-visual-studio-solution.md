---
title: 'Vorgehensweise: Debuggen eine ausführbaren Datei, die nicht Teil einer Visual Studio-Projektmappe ist | Microsoft Docs'
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
ms.openlocfilehash: e16a938eda683a607dbf7d9418b2a7bd4455a0da
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
ms.locfileid: "31476246"
---
# <a name="how-to-debug-an-executable-that-is-not-part-of-a-visual-studio-solution"></a>Vorgehensweise: Debuggen eine ausführbaren Datei, die nicht Teil einer Visual Studio-Projektmappe ist
Sie möchten manchmal eine ausführbare Datei (.exe-Datei) zu debuggen, die nicht Teil einer [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Projekt. Die ausführbare Datei wurde möglicherweise außerhalb von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] erstellt, oder sie stammt von einem anderen Entwickler.  
  
Dieses Problem wird normalerweise dadurch gelöst, dass die ausführbare Datei außerhalb von Visual Studio gestartet und mithilfe des [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Debuggers angehängt wird. Weitere Informationen finden Sie unter [Anfügen an ausgeführte Prozesse](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
Das Anfügen an eine Anwendung erfordert einige manuelle Schritte, die einige Sekunden dauern können. Diese kurze Verzögerung hat zur Folge, dass das Anfügen keine Abhilfe schafft, wenn Sie einen Fehler debuggen, der während des Startens auftritt. Auch beim Debuggen eines Programms, das keine Benutzereingaben erwartet und dessen Ausführung relativ schnell beendet ist, reicht die Zeit zum Anfügen u. U. nicht aus. Wenn Sie haben [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] und [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] installiert haben, können Sie für ein solches Programm ein EXE-Projekt erstellen.

> [!NOTE]
>  EXE-Projekte werden nicht von allen Programmiersprachen unterstützt.

Beim Debuggen einer ausführbaren Datei, die nicht Teil der Visual Studio-Projektmappe ist, die verfügbaren Debugfunktionen sind ggf. eingeschränkt, ob Sie an eine laufende ausführbare Datei anhängen, oder fügen die ausführbare Datei eine [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Lösung.

- Falls der Quellcode verfügbar ist, empfiehlt es sich, den Quellcode in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zu importieren und ein Debugbuild der ausführbaren Datei in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zu erstellen.
- Wenn Sie den Quellcode haben, und wenn die ausführbare Datei erstellt wurde, ohne [Debuginformationen](../debugger/how-to-set-debug-and-release-configurations.md) in einem kompatiblen Format verfügbaren Debugfeatures nur sehr eingeschränkt werden. 
  
### <a name="to-create-an-exe-project-for-an-existing-executable"></a>So erstellen Sie ein EXE-Projekt für eine vorhandene ausführbare Datei  
  
1.  Auf der **Datei** Menü klicken Sie auf **öffnen** , und wählen Sie **Projekt**.  
  
2.  In der **Projekt öffnen** (Dialogfeld), klicken Sie auf die Dropdownliste neben der **Dateiname** , und wählen Sie **alle Projektdateien**.  
  
3.  Suchen Sie die ausführbare Datei, und klicken Sie auf **OK**.  

    Auf diese Weise wird eine temporäre Projektmappe erstellt, in der die ausführbare Datei enthalten ist.

5.  Starten Sie die ausführbare Datei, indem Sie einen Ausführungsbefehl, z. B. **starten**, aus der **Debuggen** Menü.    
  
### <a name="to-import-an-executable-into-a-visual-studio-solution"></a>So importieren Sie eine ausführbare Datei in eine Visual Studio-Projektmappe  
  
1.  Auf der **Datei** Sie im Menü **Projekt hinzufügen**, und klicken Sie dann auf **vorhandenes Projekt**.  
  
2.  In der **vorhandenes Projekt hinzufügen** (Dialogfeld), klicken Sie auf die Dropdownliste neben der **Dateiname** , und wählen Sie **alle Projektdateien**.  
  
3.  Suchen Sie die ausführbare Datei, und wählen Sie sie aus.  
  
4.  Klicken Sie auf **OK**.  
  
5.  Starten Sie die ausführbare Datei, indem Sie einen Ausführungsbefehl, z. B. **starten**, aus der **Debuggen** Menü.    
  
## <a name="see-also"></a>Siehe auch  
 [Debuggereinstellungen und -vorbereitung](../debugger/debugger-settings-and-preparation.md)   
 [Debuggersicherheit](../debugger/debugger-security.md)   
 [DBG-Dateien](http://msdn.microsoft.com/en-us/91e449e9-8b65-4123-960f-2107cd1f1cfd)
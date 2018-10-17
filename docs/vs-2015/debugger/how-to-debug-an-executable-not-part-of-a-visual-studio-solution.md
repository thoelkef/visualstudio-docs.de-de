---
title: 'Vorgehensweise: Debuggen einer ausführbaren Datei nicht Visual Studio-Projektmappe angehört | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], executables
- executable files, importing
- executable files, debugging outside of projects
ms.assetid: 3ea176e8-1ce5-42c4-b7a2-abe3a2765033
caps.latest.revision: 26
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 241a1dbf3af5db726f344ab42d53de3fdd30db3c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49278785"
---
# <a name="how-to-debug-an-executable-not-part-of-a-visual-studio-solution"></a>Gewusst wie: Debuggen einer ausführbaren Datei, die keiner Visual Studio-Projektmappe angehört
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Manchmal kann es erforderlich sein, eine ausführbare Datei zu debuggen, die nicht Bestandteil eines [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Projekts ist. Die ausführbare Datei wurde möglicherweise außerhalb von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] erstellt, oder sie stammt von einem anderen Entwickler.  
  
 Dieses Problem wird normalerweise dadurch gelöst, dass die ausführbare Datei außerhalb von Visual Studio gestartet und mithilfe des [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Debuggers angehängt wird. Weitere Informationen finden Sie unter[Anfügen an ausgeführte Prozesse](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
 Das Anfügen an eine Anwendung erfordert einige manuelle Schritte, die einige Sekunden dauern können. Diese kurze Verzögerung hat zur Folge, dass das Anfügen keine Abhilfe schafft, wenn Sie einen Fehler debuggen, der während des Startens auftritt. Auch beim Debuggen eines Programms, das keine Benutzereingaben erwartet und dessen Ausführung relativ schnell beendet ist, reicht die Zeit zum Anfügen u. U. nicht aus. Wenn [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] installiert ist, können Sie für ein solches Programm ein EXE-Projekt erstellen.  
  
### <a name="to-create-an-exe-project-for-an-existing-executable"></a>So erstellen Sie ein EXE-Projekt für eine vorhandene ausführbare Datei  
  
1.  Auf der **Datei** Menü klicken Sie auf **öffnen** , und wählen Sie **Projekt**.  
  
2.  In der **geöffneten Projekt** (Dialogfeld), klicken Sie auf die Dropdownliste neben der **Dateiname** , und wählen Sie **alle Projektdateien**.  
  
3.  Suchen Sie die ausführbare Datei, und klicken Sie auf **OK**.  
  
     Auf diese Weise wird eine temporäre Projektmappe erstellt, in der die ausführbare Datei enthalten ist.  
  
### <a name="to-import-an-executable-into-a-visual-studio-solution"></a>So importieren Sie eine ausführbare Datei in eine Visual Studio-Projektmappe  
  
1.  Auf der **Datei** Startmenü **Projekt hinzufügen**, und klicken Sie dann auf **vorhandenes Projekt**.  
  
2.  In der **vorhandenes Projekt hinzufügen** (Dialogfeld), klicken Sie auf die Dropdownliste neben der **Dateiname** , und wählen Sie **alle Projektdateien**.  
  
3.  Suchen Sie die ausführbare Datei, und wählen Sie sie aus.  
  
4.  Klicken Sie auf **OK**.  
  
5.  Starten Sie die ausführbare Datei, indem Sie einen Ausführungsbefehl, z. B. **starten**, aus der **Debuggen** Menü.  
  
    > [!NOTE]
    >  EXE-Projekte werden nicht von allen Programmiersprachen unterstützt. Installieren Sie [!INCLUDE[vcprvc](../includes/vcprvc-md.md)], falls Sie diese Funktion benötigen.  
  
     Wenn Sie eine ausführbare Datei ohne den Quellcode debuggen, sind die verfügbaren Debugfunktionen eingeschränkt, und zwar abhängig davon, ob es sich um ein Anhängen an eine laufende ausführbare Datei handelt, oder ob die ausführbare Datei einer [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Projektmappe hinzufügt wird. Wenn die ausführbare Datei ohne Debuginformationen in einem kompatiblen Format erstellt wurde, sind die verfügbaren Features noch weiter eingeschränkt. Falls der Quellcode verfügbar ist, empfiehlt es sich, den Quellcode in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zu importieren und ein Debugbuild der ausführbaren Datei in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zu erstellen.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggereinstellungen und -vorbereitung](../debugger/debugger-settings-and-preparation.md)   
 [Debuggersicherheit](../debugger/debugger-security.md)   
 [DBG-Dateien](http://msdn.microsoft.com/en-us/91e449e9-8b65-4123-960f-2107cd1f1cfd)




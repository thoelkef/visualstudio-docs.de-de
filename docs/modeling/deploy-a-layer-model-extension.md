---
title: Bereitstellen eine Ebene Model-Erweiterung | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dependency diagrams, deploying extensions
- layer models, deploying extensions
ms.assetid: 00a4675b-d20e-487e-8fd5-be2b1e0ba238
caps.latest.revision: 27
author: alexhomer1
ms.author: ahomer
manager: douge
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 8f84f22444a5df5b9f4f4af44cd8ee9136403467
ms.openlocfilehash: 03164fe80a0b8f4dbc321a7e57b7db9e38e405d5
ms.lasthandoff: 02/22/2017

---
# <a name="deploy-a-layer-model-extension"></a>Bereitstellen einer Ebenenmodellerweiterung
Andere Benutzer von Visual Studio können Ebenenmodellierungserweiterungen installieren, die Sie mithilfe von Visual Studio erstellt haben.  
  
## <a name="installing-your-extension"></a>Installieren der Erweiterung  
 Die Erweiterung wird zu einer VSIX-Datei kompiliert, die Sie auf anderen Computern installieren können. Sie können sie auch auf dem Entwicklungscomputer installieren, um die Erweiterung in der Hauptinstanz von Visual Studio verfügbar zu machen.  
  
#### <a name="to-install-the-extension"></a>So installieren Sie die Erweiterung  
  
1.  In das Projekt mit **source.vsix.manifest**öffnen **Bin\\ \* ** im Datei-Explorer.  
  
2.  Kopieren der ** \*VSIX** Datei auf dem Computer, auf dem Sie die Erweiterung installieren möchten.  
  
3.  Doppelklicken Sie auf dem Zielcomputer auf die VSIX-Datei in Windows-Explorer.  
  
     Das VSIX-Installationsprogramm wird geöffnet.  
  
#### <a name="to-uninstall-the-extension"></a>So deinstallieren Sie die Erweiterung  
  
1.  In Visual Studio auf die **Tools** Menü klicken Sie auf **Erweiterungen und Updates**.  
  
2.  Klicken Sie auf den Namen der Erweiterung, und klicken Sie dann auf **Deinstallieren**.  
  
## <a name="installing-an-extension-on-a-team-foundation-build-server"></a>Installieren einer Erweiterung auf einem Team Foundation Build-Server  
 Auf [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)]-Servern ist Visual Studio normalerweise nicht installiert, daher können Sie VSIX nicht durch Doppelklicken installieren. Die Installation von [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)] schließt einige Komponenten ein, die das Ausführen einer VSIX-Erweiterung ermöglichen, Sie müssen die Erweiterung jedoch manuell installieren.  
  
#### <a name="to-install-your-layer-extension-on-a-includeesprbuildmiscincludesesprbuildmdmd-server"></a>So installieren Sie die Ebenenerweiterung auf einem [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)]-Server  
  
1.  Kopieren der **VSIX** Dateien vom Entwicklungscomputer auf den [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)] Computer.  
  
     Speichern Sie die VSIX-Datei in einem der folgenden Speicherorte:  
  
    -   So führen Sie die Installation für alle Benutzer und Dienste aus:  
  
         %ProgramFiles%\Microsoft Visual Studio [Version]\Common7\IDE\Extensions\Microsoft  
  
    -   So führen Sie die Installation nur für den Netzwerkdienst aus, der [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)] ausführt:  
  
         %WinDir%\ServiceProfiles\NetworkService\AppData\Local\Microsoft\VisualStudio\\\Extensions\Microsoft [Version]  
  
    -   Wenn Sie [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)] zur Ausführung im interaktiven Modus für einen bestimmten Benutzer konfiguriert haben, können Sie die Installation nur für diesen Benutzer ausführen:  
  
         %LocalAppData%\Microsoft\VisualStudio\\\Extensions\Microsoft [Version]  
  
        > [!NOTE]
        >  %LocalAppData% ist in der Regel *DriveName*: Benutzer*Benutzername*AppDataLocal.  
  
2.  Erweitern Sie jede VSIX-Datei in einen Ordner am gleichen Speicherort:  
  
    1.  Ändern Sie den Dateinamen von **VSIX** auf **ZIP**.  
  
    2.  Extrahieren Sie den Inhalt der ZIP-Datei in einen Ordner.  
  
    3.  Löschen Sie die ZIP-Datei.  
  
3.  Starten Sie [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)] neu.


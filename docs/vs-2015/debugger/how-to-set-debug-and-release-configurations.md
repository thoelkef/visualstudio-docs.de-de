---
title: 'Vorgehensweise: Festlegen von Debug- und Releasekonfigurationen | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.builds
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
- configurations, release
- build configurations, release
- projects [Visual Studio], release configurations
- debugging [Visual Studio], release configurations
- release builds, changing settings
- debug builds
- debug builds, switching to release build
- debug builds, changing configuration settings
- debugging [Visual Studio], debug configurations
- projects [Visual Studio], debug configurations
- build configurations, debug
- debug configurations
- release builds, switching to debug build
- Visual Basic projects, debug and release builds
ms.assetid: 57b6bbb7-f2af-48f7-8773-127d75034ed2
caps.latest.revision: 48
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7e0dae046e02685e7ce1d6ce7f744b568e47c5eb
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49243125"
---
# <a name="how-to-set-debug-and-release-configurations"></a>Gewusst wie: Festlegen von Debug- und Releasekonfigurationen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio-Projekte verfügen über separate Release- und Debugkonfigurationen für Ihr Programm. Wie die Namen bereits vermuten lassen, erstellen Sie die Debugversion zum Debuggen und die Releaseversion für das endgültige Release, d. h. die Freigabe.  
  
 Die Debugkonfiguration des Programms wird mit vollständigen symbolischen Debuginformationen und ohne Optimierung kompiliert. Die Optimierung gestaltet das Debuggen etwas schwieriger, da die Beziehung zwischen Quellcode und generierten Anweisungen komplexer ist.  
  
 Die Releasekonfiguration des Programms enthält keine symbolischen Debuginformationen und wird vollständig optimiert. Debuginformationen können in PDB-Dateien generiert werden, je nachdem, welche Compileroptionen verwendet werden. PDB-Dateien zu erstellen kann sehr nützlich sein, wenn Sie später die Releaseversion debuggen müssen.  
  
 Weitere Informationen zu Buildkonfigurationen finden Sie unter [Grundlagen der Buildkonfigurationen](../ide/understanding-build-configurations.md).  
  
 Sie können die Buildkonfiguration Ändern der **erstellen** im Menü auf der Symbolleiste oder in den Eigenschaftenseiten des Projekts. Die Eigenschaftenseiten des Projekts sind sprachspezifisch. Das folgende Verfahren zeigt, wie die Buildkonfiguration über die Symbolleiste und das Menü geändert wird. Weitere Informationen zum Ändern der Buildkonfiguration in Projekten mit verschiedenen Sprachen finden Sie im Abschnitt „Verwandte Themen“.  
  
### <a name="to-change-the-build-configuration"></a>So ändern Sie die Buildkonfiguration  
  
1.  Im Menü erstellen: Klicken Sie auf **Build / Konfigurations-Manager**, und wählen Sie dann **Debuggen** oder **Version**.  
  
2.  Wählen Sie auf der Symbolleiste entweder **Debuggen** oder **Version** aus der **Projektmappenkonfigurationen** Listenfeld.  
  
     ![Symbolleisten-Buildkonfiguration](../debugger/media/toolbarbuildconfiguration.png "ToolbarBuildConfiguration")  
  
     Diese Symbolleiste ist in Express-Editionen nicht verfügbar. Können Sie die **erstellen Lösung F6** und **Debuggen F5 starten** Menüelemente, um die Konfiguration auszuwählen.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggereinstellungen und -vorbereitung](../debugger/debugger-settings-and-preparation.md)   
 [Projekteinstellungen für eine C++-Debugkonfiguration](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [Project Settings for  C# Debug Configurations (Projekteinstellungen für C#-Debugkonfigurationen)](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Project Settings for a Visual Basic Debug Configuration (Projekteinstellungen für eine Visual Basic-Debugkonfiguration)](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Vorgehensweise: Erstellen und Bearbeiten von Konfigurationen](../ide/how-to-create-and-edit-configurations.md)   
 [Debug- und Release-Projektkonfigurationen](http://msdn.microsoft.com/en-us/0440b300-0614-4511-901a-105b771b236e)




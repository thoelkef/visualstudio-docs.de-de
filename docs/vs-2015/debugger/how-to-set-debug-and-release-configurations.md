---
title: 'Gewusst wie: Festlegen von Debug-und Releasekonfigurationen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4984355c12a92529a943fe6778740ac2d7f522f8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65703644"
---
# <a name="how-to-set-debug-and-release-configurations"></a>Gewusst wie: Festlegen von Debug- und Releasekonfigurationen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio-Projekte verfügen über separate Release- und Debugkonfigurationen für Ihr Programm. Wie die Namen bereits vermuten lassen, erstellen Sie die Debugversion zum Debuggen und die Releaseversion für das endgültige Release, d. h. die Freigabe.  
  
 Die Debugkonfiguration des Programms wird mit vollständigen symbolischen Debuginformationen und ohne Optimierung kompiliert. Die Optimierung gestaltet das Debuggen etwas schwieriger, da die Beziehung zwischen Quellcode und generierten Anweisungen komplexer ist.  
  
 Die Releasekonfiguration des Programms enthält keine symbolischen Debuginformationen und wird vollständig optimiert. Debuginformationen können in PDB-Dateien generiert werden, je nachdem, welche Compileroptionen verwendet werden. PDB-Dateien zu erstellen kann sehr nützlich sein, wenn Sie später die Releaseversion debuggen müssen.  
  
 Weitere Informationen zu Buildkonfigurationen finden Sie Untergrund Legendes zu [Buildkonfigurationen](../ide/understanding-build-configurations.md).  
  
 Sie können die Buildkonfiguration über das Menü **Erstellen** , über die Symbolleiste oder auf den Eigenschaften Seiten des Projekts ändern. Die Eigenschaftenseiten des Projekts sind sprachspezifisch. Das folgende Verfahren zeigt, wie die Buildkonfiguration über die Symbolleiste und das Menü geändert wird. Weitere Informationen zum Ändern der Buildkonfiguration in Projekten mit verschiedenen Sprachen finden Sie im Abschnitt „Verwandte Themen“.  
  
### <a name="to-change-the-build-configuration"></a>So ändern Sie die Buildkonfiguration  
  
1. Klicken Sie im Menü Erstellen auf **Erstellen/Configuration Manager**, und wählen Sie dann **Debuggen** oder **Release**aus.  
  
2. Wählen Sie auf der Symbolleiste im Listenfeld Projektmappenkonfigurationen entweder **Debuggen** oder **Solution Configurations** **Release** aus.  
  
     ![Symbolleisten-Buildkonfiguration](../debugger/media/toolbarbuildconfiguration.png "ToolbarBuildConfiguration")  
  
     Diese Symbolleiste ist in Express-Editionen nicht verfügbar. Sie können die Menü Elemente Projekt Mappe **Erstellen** und **Debuggen starten** verwenden, um die Konfiguration auszuwählen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Debugger-Einstellungen und-Vorbereitung](../debugger/debugger-settings-and-preparation.md)   
 [Projekteinstellungen für eine C++-Debugkonfiguration](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [Projekteinstellungen für c#-Debugkonfigurationen](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Projekteinstellungen für eine Visual Basic Debugkonfiguration](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Gewusst wie: Erstellen und Bearbeiten von Konfigurationen](../ide/how-to-create-and-edit-configurations.md)   
 [Debug- und Release-Projektkonfigurationen](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e)

---
title: "Gewusst wie: Festlegen von Debug- und Releasekonfigurationen | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.builds"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Buildkonfigurationen, Debug"
  - "Buildkonfigurationen, Version"
  - "Konfigurationen, Version"
  - "Debugbuilds"
  - "Debugbuilds, Ändern von Konfigurationseinstellungen"
  - "Debugbuilds, Wechseln zu Releasebuild"
  - "Debugkonfigurationen"
  - "Debuggen [Visual Studio], Debugkonfigurationen"
  - "Debuggen [Visual Studio], Releasekonfigurationen"
  - "Projekte [Visual Studio], Debugkonfigurationen"
  - "Projekte [Visual Studio], Releasekonfigurationen"
  - "Releasebuilds, Ändern der Einstellungen"
  - "Releasebuilds, Wechseln zu Debugbuild"
  - "Visual Basic-Projekte, Debugbuilds und Releasebuilds"
ms.assetid: 57b6bbb7-f2af-48f7-8773-127d75034ed2
caps.latest.revision: 45
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 45
---
# Gewusst wie: Festlegen von Debug- und Releasekonfigurationen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual Studio\-Projekte verfügen über separate Release\- und Debugkonfigurationen für Ihr Programm.  Wie die Namen bereits vermuten lassen, erstellen Sie die Debugversion zum Debuggen und die Releaseversion für das endgültige Release, d. h. die Freigabe.  
  
 Die Debugkonfiguration des Programms wird mit vollständigen symbolischen Debuginformationen und ohne Optimierung kompiliert.  Die Optimierung gestaltet das Debuggen etwas schwieriger, da die Beziehung zwischen Quellcode und generierten Anweisungen komplexer ist.  
  
 Die Releasekonfiguration des Programms enthält keine symbolischen Debuginformationen und wird vollständig optimiert.  Debuginformationen können in PDB\-Dateien generiert werden, je nachdem, welche Compileroptionen verwendet werden.  PDB\-Dateien zu erstellen kann sehr nützlich sein, wenn Sie später die Releaseversion debuggen müssen.  
  
 Weitere Informationen zu Buildkonfigurationen finden Sie unter [Grundlagen der Buildkonfiguration](../ide/understanding-build-configurations.md).  
  
 Sie können die Buildkonfiguration über die Symbolleiste im Menü **Build** oder über die Eigenschaftenseiten des Projekts ändern.  Die Eigenschaftenseiten des Projekts sind sprachspezifisch.  Das folgende Verfahren zeigt, wie die Buildkonfiguration über die Symbolleiste und das Menü geändert wird.  Weitere Informationen zum Ändern der Buildkonfiguration in Projekten mit verschiedenen Sprachen finden Sie im Abschnitt „Verwandte Themen“.  
  
### So ändern Sie die Buildkonfiguration  
  
1.  Klicken Sie im Buildmenü auf **Build \/ Konfigurations\-Manager** und wählen Sie anschließend **Debug** oder **Release**.  
  
2.  Wählen Sie auf der Symbolleiste im Listenfeld **Projektmappenkonfigurationen** die Option **Debuggen** oder **Release** aus.  
  
     ![Symbolleisten&#45;Buildkonfiguration](../debugger/media/toolbarbuildconfiguration.png "ToolbarBuildConfiguration")  
  
     Diese Symbolleiste ist in Express\-Editionen nicht verfügbar.  Sie können die Menüelemente **Projektmappe erstellen** \(F6\) und **Debuggen starten** \(F5\) verwenden, um die Konfiguration auszuwählen.  
  
## Siehe auch  
 [Einstellungen und Vorbereitung für das Debuggen](../debugger/debugger-settings-and-preparation.md)   
 [Projekteinstellungen für eine C\+\+\-Debugkonfiguration](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [Projekteinstellungen für C\#\-Debugkonfigurationen](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Projekteinstellungen für eine Visual Basic\-Debugkonfiguration](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Gewusst wie: Erstellen und Bearbeiten von Konfigurationen](../ide/how-to-create-and-edit-configurations.md)   
 [Debug and Release Project Configurations](http://msdn.microsoft.com/de-de/0440b300-0614-4511-901a-105b771b236e)
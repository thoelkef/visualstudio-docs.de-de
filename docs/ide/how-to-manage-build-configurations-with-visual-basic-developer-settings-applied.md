---
title: "Gewusst wie: Verwalten von Buildkonfigurationen mit aktivierten Visual Basic Developer-Einstellungen | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Erweiterte Buildkonfigurationen"
  - "Erstellen mit Visual Basic-Entwicklereinstellungen"
  - "Debugbuilds"
  - "MSBuild, Debugbuild"
  - "MSBuild, Releasebuild"
  - "Releasebuilds"
  - "Visual Studio, Erstellen mit Visual Basic-Einstellungen"
ms.assetid: eaea6e0b-6c61-4869-8d63-d372c745a23c
caps.latest.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 9
---
# Gewusst wie: Verwalten von Buildkonfigurationen mit aktivierten Visual Basic Developer-Einstellungen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Bei aktivierten [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] Developer\-Einstellungen sind alle Optionen für die erweiterte Buildkonfiguration standardmäßig ausgeblendet.  In diesem Thema wird erläutert, wie diese Einstellungen manuell aktiviert werden.  
  
## Aktivieren von erweiterten Buildkonfigurationen  
 Aufgrund der [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] Developer\-Einstellungen sind die Optionen zum Öffnen des Dialogfelds **Konfigurations\-Manager** sowie der Listen **Konfiguration** und **Plattform** im [Projekt\-Designer](http://msdn.microsoft.com/de-de/898dd854-c98d-430c-ba1b-a913ce3c73d7) standardmäßig nicht verfügbar.  
  
#### So ermöglichen Sie erweiterte Buildkonfigurationen  
  
1.  Klicken Sie im Menü **Extras** auf **Optionen**.  
  
2.  Erweitern Sie **Projekte und Projektmappen**, und klicken Sie auf **Allgemein**.  
  
    > [!NOTE]
    >  Der Knoten **Allgemein** ist auch dann sichtbar, wenn die Option **Alle Einstellungen anzeigen** deaktiviert ist.  Wenn Sie alle verfügbaren Optionen anzeigen möchten, klicken Sie auf **Alle Einstellungen anzeigen**.  
  
3.  Klicken Sie auf **Erweiterte Buildkonfigurationen anzeigen**.  
  
4.  Klicken Sie auf **OK**.  
  
     Jetzt ist der **Konfigurations\-Manager** im Menü **Erstellen** verfügbar, und auch die Listen **Konfiguration** und **Plattform** werden im Projekt\-Designer angezeigt.  
  
## Siehe auch  
 [Grundlagen der Buildkonfiguration](../ide/understanding-build-configurations.md)   
 [Anwendungen in Visual Studio erstellen](../ide/compiling-and-building-in-visual-studio.md)
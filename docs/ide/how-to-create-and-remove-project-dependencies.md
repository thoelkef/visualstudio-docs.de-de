---
title: "Gewusst wie: Erstellen und Entfernen von Projektabh&#228;ngigkeiten | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.ProjectDependenciesDlg"
helpviewer_keywords: 
  - "Builds [Visual Studio], Einrichten"
  - "Abhängigkeiten, Projekt"
  - "Projektbuildkonfigurationen, Abhängigkeiten"
  - "Projektabhängigkeiten"
  - "Projekte [Visual Studio], Abhängigkeiten"
  - "vs.build.projectdependencies"
ms.assetid: e2a0a8ff-dae7-40a8-b774-b88aa5235183
caps.latest.revision: 12
caps.handback.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Gewusst wie: Erstellen und Entfernen von Projektabh&#228;ngigkeiten
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Beim Erstellen einer Projektmappe mit mehreren Projekten kann es erforderlich sein, zunächst bestimmte Projekte zu erstellen, um Code zu generieren, der dann von anderen Projekten verwendet werden kann.  Wenn ein Projekt ausführbaren Code verwendet, der von einem anderen Projekt generiert wurde, wird das Projekt, das den Code generiert, als Projektabhängigkeit des Projekts bezeichnet, das den Code verwendet.  Solche Abhängigkeitsbeziehungen können im **Projektabhängigkeiten** Dialogfeld definiert werden.  
  
### So weisen Sie Projektabhängigkeiten zu  
  
1.  Wählen Sie im **Projektmappen\-Explorer** ein Projekt aus.  
  
2.  Klicken Sie im Menü **Projekt** auf **Projektabhängigkeiten**.  
  
     Das Dialogfeld **Projektabhängigkeiten** wird geöffnet.  
  
    > [!NOTE]
    >  Die Option **Projektabhängigkeiten** ist nur in einer Projektmappe verfügbar, die mehrere Projekte enthält.  
  
3.  Wählen Sie auf der Registerkarte **Abhängigkeiten** ein Projekt aus dem Dropdownmenü **Projekt** aus.  
  
4.  Aktivieren Sie im Feld **Abhängigkeiten** das Kontrollkästchen eines beliebigen weiteren Projekts, das vor Erstellung dieses Projekts erstellt werden muss.  
  
 Die Projektmappe muss über mehrere Projekte verfügen, damit Projektabhängigkeiten erstellt werden können.  
  
### So entfernen Sie Projektabhängigkeiten  
  
1.  Wählen Sie im **Projektmappen\-Explorer** ein Projekt aus.  
  
2.  Klicken Sie im Menü **Projekt** auf **Projektabhängigkeiten**.  
  
     Das Dialogfeld **Projektabhängigkeiten** wird geöffnet.  
  
    > [!NOTE]
    >  Die Option **Projektabhängigkeiten** ist nur in einer Projektmappe verfügbar, die mehrere Projekte enthält.  
  
3.  Wählen Sie auf der Registerkarte **Abhängigkeiten** ein Projekt aus dem Dropdownmenü **Projekt** aus.  
  
4.  Deaktivieren Sie im Feld **Abhängigkeiten** die Kontrollkästchen neben den Projekten, die nicht länger in Abhängigkeit zu diesem Projekt stehen sollen.  
  
## Siehe auch  
 [Erstellen und Bereinigen von Projekten und Projektmappen in Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)   
 [Anwendungen in Visual Studio erstellen](../ide/compiling-and-building-in-visual-studio.md)   
 [Grundlagen der Buildkonfiguration](../ide/understanding-build-configurations.md)   
 [Gewusst wie: Ändern von Projekteigenschaften und Konfigurationseinstellungen](http://msdn.microsoft.com/de-de/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)
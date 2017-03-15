---
title: "Projektmappenkonfiguration | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Projektmappenkonfigurationen"
ms.assetid: f22cfc75-3e31-4e0d-88a9-3ca99539203b
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# Projektmappenkonfiguration
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Projektmappenkonfigurationen speichern auf Eigenschaften. Sie leiten das Verhalten der **Start** \(F5\) Schlüssel und **Build** Befehle. Standardmäßig werden diese Befehle erstellen und die Debugkonfiguration zu starten. Beide Befehle werden im Kontext einer Projektmappenkonfiguration ausführen. Dies bedeutet, dass der Benutzer F5 erwarten kann, zu starten und zu erstellen, die ungeachtet die aktive Projektmappe über die Einstellungen konfiguriert ist. Die Umgebung soll für Lösungen statt Projekte zu optimieren, wenn es darum geht, erstellen und ausführen.  
  
 Der Standardsymbolleiste von Visual Studio enthält eine Startschaltfläche und eine Projektmappenkonfiguration\-Dropdownliste rechts neben der Schaltfläche "Start". Diese Liste ermöglicht das Auswählen der Konfiguration gestartet werden soll, wenn F5 gedrückt wird, ihre eigenen Projektmappenkonfigurationen erstellen oder eine vorhandene Konfiguration bearbeiten.  
  
> [!NOTE]
>  Es gibt keine Erweiterbarkeitsschnittstellen zum Erstellen oder Bearbeiten von Projektmappenkonfigurationen. Verwenden Sie `DTE.SolutionBuilder`. Es gibt jedoch Erweiterbarkeits\-APIs für die Verwaltung der Erstellung der Projektmappe. Weitere Informationen finden Sie unter <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2>.  
  
 Hier ist zum Implementieren von Projektmappenkonfigurationen vom Projekttyp unterstützt:  
  
-   Projekt  
  
     Zeigt die Namen der Projekte in der aktuellen Projektmappe.  
  
-   Konfiguration  
  
     Die Liste der Konfigurationen, die vom Projekttyp unterstützt und in den Eigenschaftenseiten angezeigten implementieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>.  
  
     Die Configuration\-Spalte zeigt den Namen der Projektkonfiguration in dieser Projektmappenkonfiguration erstellen, und listet alle Projektkonfigurationen, wenn Sie auf den Pfeil klicken. Die Umgebung Ruft die <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgNames%2A> Methode, um diese Liste ausfüllen. Wenn die <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgProviderProperty%2A> \-Methode gibt an, dass das Projekt neue Konfiguration zu bearbeiten unterstützt, oder bearbeiten Auswahl wird auch unter der Überschrift Konfiguration angezeigt. Jede Auswahl starten Dialogfelder, die Methoden zum Aufrufen der `IVsCfgProvider2` Schnittstelle, um die Projektkonfigurationen bearbeiten.  
  
     Wenn ein Projekt Konfigurationen nicht unterstützt, wird die Spalte Konfiguration wird keiner angezeigt und ist deaktiviert.  
  
-   Plattform  
  
     Zeigt die Plattform, die die ausgewählte Projektkonfiguration für erstellt und enthält eine Liste aller verfügbaren Plattformen für das Projekt, wenn Sie den Pfeil klicken. Die Umgebung Ruft die <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetPlatformNames%2A> Methode, um diese Liste ausfüllen. Wenn die <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgProviderProperty%2A> \-Methode gibt an, dass das Projekt unterstützt die Plattform zu bearbeiten, neu oder bearbeiten Auswahl wird auch unter der Überschrift Plattform angezeigt. Jede Auswahl starten Dialogfelder, die aufgerufen werden `IVsCfgProvider2` Methoden, um das Projekt verfügbaren Plattformen zu bearbeiten.  
  
     Wenn ein Projekt keine Plattformen unterstützt, wird die Spalte Plattform für das Projekt wird keiner angezeigt und ist deaktiviert.  
  
-   Build  
  
     Gibt an, ob das Projekt von der aktuellen Projektmappenkonfiguration erstellt wird. Nicht ausgewählte Projekte werden nicht erstellt werden, wenn die Befehle zum Erstellen von Projektmappen auf Dokumentebene trotz projektabhängigkeiten aufgerufen werden, die sie enthalten. Projekte, die nicht ausgewählt werden immer noch Debuggen, ausführen, Verpackung und Bereitstellung der Lösung umfasst.  
  
-   Bereitstellen  
  
     Gibt an, ob das Projekt bereitgestellt wird, wenn die Befehle starten oder Bereitstellen mit der ausgewählten Projektmappen\-Buildkonfiguration verwendet werden. Das Kontrollkästchen für dieses Feld ist verfügbar, wenn das Projekt unterstützt die Bereitstellung durch die Implementierung der <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> Schnittstelle auf seine <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> Objekt.  
  
 Sobald eine neue Projektmappenkonfiguration hinzugefügt wurde, kann der Benutzer auswählen es aus dem Dropdown\-Listenfeld Projektmappenkonfiguration auf der Standardsymbolleiste erstellen und\/oder zu starten, die die Konfiguration.  
  
## Siehe auch  
 [Verwalten von Konfigurationsoptionen](../../extensibility/internals/managing-configuration-options.md)   
 [Konfiguration zum Erstellen des Projekts](../../extensibility/internals/project-configuration-for-building.md)   
 [Projekt\-Konfigurationsobjekt](../../extensibility/internals/project-configuration-object.md)
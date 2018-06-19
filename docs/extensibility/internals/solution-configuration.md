---
title: Projektmappenkonfiguration | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- solution configurations
ms.assetid: f22cfc75-3e31-4e0d-88a9-3ca99539203b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f7b2a453d4ea4e8b92b40ee126f9441e6f353606
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31132720"
---
# <a name="solution-configuration"></a>Projektmappenkonfiguration
Projektmappenkonfigurationen Projektmappenebene Eigenschaften zu speichern. Sie leiten das Verhalten der **starten** (F5) Schlüssel und **erstellen** Befehle. Standardmäßig werden diese Befehle erstellen und die Debug-Konfiguration beginnen. Beide Befehle, die im Kontext einer Projektmappenkonfiguration ausgeführt werden. Dies bedeutet, dass der Benutzer F5 erwarten kann, zu starten und zu erstellen, die alle die aktive Projektmappe über die Einstellungen konfiguriert ist. Die Umgebung ist dafür ausgelegt, optimiert für Lösungen statt Projekte beim Erstellen und ausführen.  
  
 Der Visual Studio-Standardsymbolleiste enthält eine Schaltfläche "Start" und eine Lösung-Konfigurationen-Dropdownliste rechts neben der Schaltfläche "Start". Diese Liste kann Benutzer wählen Sie die Konfiguration gestartet werden soll, wenn F5 gedrückt wird, ihre eigenen Projektmappenkonfigurationen erstellen oder Bearbeiten einer vorhandenen Konfigurations.  
  
> [!NOTE]
>  Es gibt keine Erweiterbarkeitsschnittstellen erstellen oder bearbeiten die Konfiguration der Projektmappe ein. Verwenden Sie `DTE.SolutionBuilder`. Es gibt jedoch-Erweiterbarkeits-APIs für die Verwaltung der Erstellung der Projektmappe. Weitere Informationen finden Sie unter <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2>.  
  
 Hier ist, wie Sie durch den Projekttyp unterstützten Projektmappenkonfigurationen implementieren können:  
  
-   Projekt  
  
     Zeigt die Namen von Projekten, die in der aktuellen Projektmappe gefunden.  
  
-   Konfiguration  
  
     Geben Sie die Liste der Konfigurationen, die durch den Projekttyp unterstützt, und implementieren Sie die Eigenschaftenseiten angezeigt <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>.  
  
     Configuration-Spalte zeigt den Namen der Projektkonfiguration, die in dieser Konfiguration der Projektmappe erstellt, und zeigt eine Liste aller Projektkonfigurationen, wenn Sie den Pfeil klicken. Die Umgebung Ruft die <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgNames%2A> Methode, um diese Liste ausfüllen. Wenn die <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgProviderProperty%2A> Methode gibt an, dass das Projekt neue Konfiguration zu bearbeiten unterstützt, oder bearbeiten Auswahl werden ebenfalls unter der Überschrift Konfiguration angezeigt. Jede Auswahl starten Dialogfelder, die Methoden Aufrufen der `IVsCfgProvider2` Schnittstelle, um Konfigurationen für das Projekt bearbeiten.  
  
     Wenn ein Projekt Konfigurationen nicht unterstützt, wird die Spalte wird keiner angezeigt und ist deaktiviert.  
  
-   Plattform  
  
     Zeigt die Plattform, die die ausgewählte Projektkonfiguration für builds, die und zeigt eine Liste aller verfügbaren Plattformen für das Projekt, wenn Sie den Pfeil klicken. Die Umgebung Ruft die <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetPlatformNames%2A> Methode, um diese Liste ausfüllen. Wenn die <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgProviderProperty%2A> Methode gibt an, dass das Projekt neue Plattform zu bearbeiten unterstützt, oder bearbeiten Auswahl werden unter der Überschrift Plattform ebenfalls angezeigt. Jede Auswahl starten Dialogfelder, die aufgerufen werden `IVsCfgProvider2` Methoden, um das Projekt verfügbaren Plattformen zu bearbeiten.  
  
     Wenn ein Projekt Plattformen nicht unterstützt, wird die Spalte mit der Plattform für dieses Projekt wird keiner angezeigt und ist deaktiviert.  
  
-   Build  
  
     Gibt an, und zwar unabhängig davon, ob durch die Konfiguration der aktuellen Projektmappe das Projekt erstellt wird. Nicht ausgewählte Projekte werden nicht erstellt werden, wenn die Befehle zum Erstellen von Projektmappen auf Dokumentebene trotz projektabhängigkeiten aufgerufen werden, die sie enthalten. Projekte, die zu erstellenden nicht ausgewählt sind immer noch im Debuggen, ausführen, Packen und Bereitstellen der Projektmappe enthalten.  
  
-   Bereitstellen  
  
     Gibt an, und zwar unabhängig davon, ob das Projekt bereitgestellt wird, wenn die Start- oder Bereitstellen Befehle mit der ausgewählten Projektmappen-Buildkonfiguration verwendet werden. Das Kontrollkästchen für dieses Feld ist verfügbar, wenn das Projekt unterstützt das bereitstellen, die durch die Implementierung der <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> Schnittstelle auf seine <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> Objekt.  
  
 Sobald eine neue Projektmappenkonfiguration hinzugefügt wird, kann der Benutzer auswählen es aus dem Dropdown-Listenfeld Projektmappenkonfiguration auf der Standardsymbolleiste erstellen und/oder starten, die die Konfiguration.  
  
## <a name="see-also"></a>Siehe auch  
 [Verwalten von Konfigurationsoptionen](../../extensibility/internals/managing-configuration-options.md)   
 [Konfiguration für die Erstellung des Projekts](../../extensibility/internals/project-configuration-for-building.md)   
 [Projektkonfigurationsobjekt](../../extensibility/internals/project-configuration-object.md)
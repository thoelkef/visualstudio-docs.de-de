---
title: Projektmappenkonfiguration | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- solution configurations
ms.assetid: f22cfc75-3e31-4e0d-88a9-3ca99539203b
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c2efd5a626e92d180f7c842172f764fa7f8011e4
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49245794"
---
# <a name="solution-configuration"></a>Projektmappenkonfiguration
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Projektmappenkonfigurationen auf Projektmappenebene Eigenschaften zu speichern. Sie leiten das Verhalten der **starten** (F5) Schlüssel und **erstellen** Befehle. Standardmäßig werden diese Befehle erstellen und die Debug-Konfiguration zu starten. Führen Sie beide Befehle im Kontext einer Projektmappenkonfiguration. Dies bedeutet, dass der Benutzer F5 erwarten kann, zu starten und zu erstellen, die beliebige die aktive Projektmappe über die Einstellungen konfiguriert ist. Die Umgebung für Lösungen anstelle von Projekten zu optimieren, wenn es darum geht, erstellen und ausführen soll.  
  
 Der standardmäßige Visual Studio-Symbolleiste enthält eine Schaltfläche "Start" und eine Projektmappenkonfiguration-Dropdownliste rechts neben der Schaltfläche "Start". Dieser Liste kann Benutzer wählen die Konfiguration gestartet werden soll, wenn F5 gedrückt wird, ihre eigenen Projektmappenkonfigurationen erstellen oder Bearbeiten einer vorhandenen Konfigurations.  
  
> [!NOTE]
>  Es gibt keine Erweiterungsschnittstellen erstellen oder bearbeiten die Projektmappenkonfiguration ein. Verwenden Sie `DTE.SolutionBuilder`. Es gibt jedoch Erweiterbarkeits-APIs für die Verwaltung der Erstellung der Projektmappe. Weitere Informationen finden Sie unter <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2>.  
  
 Hier ist, wie Sie die Projektmappenkonfiguration, die vom Projekttyp unterstützt implementieren können:  
  
-   Projekt  
  
     Zeigt die Namen von Projekten, die in der aktuellen Projektmappe gefunden.  
  
-   Konfiguration  
  
     Geben Sie die Liste der Konfigurationen, die vom Projekttyp unterstützt, und implementieren Sie in den Eigenschaftenseiten angezeigten <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>.  
  
     Die Configuration-Spalte zeigt den Namen der Projektkonfiguration, die in dieser Projektmappenkonfiguration erstellt, und listet alle den Projektkonfigurationen, wenn Sie auf den Pfeil klicken. Die Umgebung Ruft die <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgNames%2A> Methode zum Auffüllen dieser Liste. Wenn die <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgProviderProperty%2A> Methode gibt an, dass das Projekt unterstützt neue Konfiguration zu bearbeiten, bearbeiten Auswahl werden ebenfalls unter der Überschrift "Konfiguration" angezeigt. Jede dieser Optionen starten Dialogfelder, die Methoden zum Aufrufen der `IVsCfgProvider2` Schnittstelle, um die Konfigurationen des Projekts bearbeiten.  
  
     Wenn ein Projekt Konfigurationen nicht unterstützt, wird die Configuration-Spalte wird keiner angezeigt und ist deaktiviert.  
  
-   Plattform  
  
     Zeigt die Plattform, die die Projektkonfiguration für die ausgewählten builds für und zeigt eine Liste aller verfügbaren Plattformen für das Projekt, wenn Sie den Pfeil klicken. Die Umgebung Ruft die <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetPlatformNames%2A> Methode zum Auffüllen dieser Liste. Wenn die <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgProviderProperty%2A> Methode gibt an, dass das Projekt unterstützt neue Plattform zu bearbeiten, bearbeiten Auswahl werden ebenfalls angezeigt, unter der Überschrift "Platform". Jede dieser Optionen starten Dialogfelder, die aufgerufen werden `IVsCfgProvider2` Methoden, um die verfügbaren Plattformen des Projekts bearbeiten.  
  
     Wenn ein Projekt keine Plattformen unterstützt, wird die Spalte mit der Plattform für das Projekt wird keiner angezeigt und ist deaktiviert.  
  
-   Build  
  
     Gibt an, und zwar unabhängig davon, ob das Projekt von der aktuellen Konfiguration der Projektmappe erstellt wird. Nicht ausgewählte Projekte werden nicht erstellt werden, wenn die Befehle zum Erstellen von Projektmappen auf Dokumentebene trotz alle Abhängigkeiten des Projekts aufgerufen werden, die sie enthalten. Projekte nicht erstellt werden sollen, sind immer noch im Debuggen, ausführen, Packen und Bereitstellen der Lösung enthalten.  
  
-   Bereitstellen  
  
     Gibt an, und zwar unabhängig davon, ob das Projekt bereitgestellt wird, wenn die Befehle starten oder Bereitstellen mit der ausgewählten Projektmappe Buildkonfiguration verwendet werden. Das Kontrollkästchen neben diesem Feld werden verfügbar, wenn das Projekt unterstützt die Bereitstellung, die durch die Implementierung der <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> Schnittstelle, für dessen <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> Objekt.  
  
 Sobald eine neue Projektmappenkonfiguration hinzugefügt wurde, kann der Benutzer auswählen es aus dem Dropdown-Listenfeld Projektmappenkonfiguration auf der Standardsymbolleiste erstellen bzw. diese Konfiguration zu starten.  
  
## <a name="see-also"></a>Siehe auch  
 [Verwalten von Konfigurationsoptionen](../../extensibility/internals/managing-configuration-options.md)   
 [Konfiguration für die Erstellung des Projekts](../../extensibility/internals/project-configuration-for-building.md)   
 [Projektkonfigurationsobjekt](../../extensibility/internals/project-configuration-object.md)


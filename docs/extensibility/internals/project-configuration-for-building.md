---
title: Zum Erstellen von Projektkonfiguration | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], configuration for building
- project configurations, building
ms.assetid: 2c83615d-fa4d-4b9f-b315-7a69b3000da0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4d78ac1cabc356db162639d3eb19d0bff71e295e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="project-configuration-for-building"></a>Konfiguration für die Erstellung des Projekts
Die Liste der Konfigurationen für Projektmappenbuilds für eine bestimmte Lösung wird durch das Dialogfeld Projektmappenkonfigurationen verwaltet.  
  
 Ein Benutzer kann weitere Projektmappenkonfigurationen, jeweils über einen eindeutigen Namen erstellen. Wenn der Benutzer eine neue Projektmappenkonfiguration erstellt, wird standardmäßig die IDE auf den entsprechenden Konfigurationsnamen in die Projekte oder Debuggen, wenn keine entsprechenden Namen vorhanden ist. Der Benutzer kann die Auswahl für speziellen Anforderungen bei Bedarf ändern. Die einzige Ausnahme dieses Verhalten ist, wenn das Projekt eine Konfiguration unterstützt, die den Namen der neuen Projektmappenkonfiguration entspricht. Nehmen wir beispielsweise an, dass eine Projektmappe Projekt1 und Projekt2 enthält. Projekt1 hat Projektkonfigurationen Debuggen, Verkaufs- und MyConfig1. Projekt2 hat Projektkonfigurationen Debuggen, Verkaufs- und MyConfig2.  
  
 Wenn der Benutzer eine neue Projektmappenkonfiguration, die mit dem Namen MyConfig2 erstellt, bindet Projekt1 die Debug-Konfiguration an die Projektmappenkonfiguration standardmäßig an. Projekt2 wird auch die MyConfig2 Konfiguration an die Projektmappenkonfiguration standardmäßig gebunden.  
  
> [!NOTE]
>  Die Bindung ist Groß-/Kleinschreibung.  
  
 Wenn der Benutzer wählt die **Mehrfachauswahl** Element in der Dropdownliste Konfiguration die Umgebung zeigt ein Dialogfeld, das die Liste mit verfügbaren Konfigurationen enthält.  
  
 ![Konfigurationen mit mehreren](../../extensibility/internals/media/vsmultiplecfgs.gif "VsMultipleCfgs")  
Mehrere Konfigurationen  
  
 Innerhalb dieses Dialogfelds kann der Benutzer eine oder mehrere Konfigurationen auswählen. Nach dem auswählen, entsprechen die Eigenschaftswerte, die auf das Dialogfeld Eigenschaftenseiten angezeigt die Schnittmenge der Werte für die ausgewählten Konfigurationen.  
  
 Finden Sie unter [Projektmappenkonfiguration](../../extensibility/internals/solution-configuration.md) Informationen im Zusammenhang mit hinzufügen und Umbenennen von Konfigurationen für Projektmappen und Projekte.  
  
 Projektabhängigkeiten und Buildreihenfolge für Ziele sind unabhängige Projektmappenkonfiguration: Sie können also nur eingerichtet für alle Projekte in der Projektmappe eine Abhängigkeitsstruktur. Die Projektmappe oder das Projekt mit der rechten Maustaste und Auswählen von entweder der **Projektabhängigkeiten** oder **Projektbuildreihenfolge** option öffnet der **Projektabhängigkeiten** (Dialogfeld). Es kann auch aus geöffnet werden die **Projekt** Menü.  
  
 ![Projektabhängigkeiten](../../extensibility/internals/media/vsprojdependencies.gif "VsProjDependencies")  
Projektabhängigkeiten  
  
 Projektabhängigkeiten bestimmt die Reihenfolge, in der Projekte erstellen. Verwenden Sie die Registerkarte Buildreihenfolge für Ziele im Dialogfeld, um die genaue Reihenfolge anzuzeigen, in der Projekte innerhalb einer Projektmappe zu erstellen, und verwenden die Registerkarte "Abhängigkeiten" So ändern Sie die Buildreihenfolge für Ziele.  
  
> [!NOTE]
>  Projekte in der Liste, die zugehörigen Kontrollkästchen ausgewählt haben, jedoch werden abgeblendet angezeigt wurden hinzugefügt, von der Umgebung aufgrund eines expliziten Abhängigkeiten, die gemäß der <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency> oder <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency> Schnittstellen und kann nicht geändert werden. Z. B. Hinzufügen eines Projekt-Verweises aus einem [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] Projekt in ein anderes Projekt fügt automatisch eine Buildabhängigkeit, die nur durch Löschen des Verweises entfernt werden kann. Projekte, deren Kontrollkästchen deaktiviert sind und abgeblendet, können nicht ausgewählt werden, da auf diese Weise eine Abhängigkeit Schleife erstellt würde (z. B. Projekt1 wäre Projekt2 abhängt und Projekt2 wäre Projekt1 abhängt), würde die Builds installieren.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Buildprozesse umfassen die typische kompilieren und Verknüpfen von Operationen, die mit einem einzigen Buildbefehl aufgerufen werden. Zwei andere Buildprozesse können ebenfalls unterstützt: eine saubere Operation zum Löschen von alle Ausgabeelemente aus einem vorherigen Build und eine Überprüfung auf dem neuesten Stand, zu bestimmen, ob ein Ausgabeelement in einer Konfiguration geändert hat.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> Objekte zurückgeben, eine entsprechende <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> (Merry <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>) zum Verwalten ihrer Buildprozesse. Um den Status der Buildvorgang zu melden, während er ausgeführt wird, die Konfigurationen die Aufrufe an <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildStatusCallback>, eine Schnittstelle implementiert, von der Umgebung, und ein anderes Objekt von Interesse Buildereignisse-Status.  
  
 Sobald erstellt, können die Konfigurationseinstellungen verwendet werden, um zu bestimmen, und zwar unabhängig davon, ob sie unter der Kontrolle des Debuggers ausgeführt werden können. Implementieren von Konfigurationen <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg> um Debuggen zu unterstützen.  
  
 Nach der Implementierung der projektabhängigkeiten, können Sie die Abhängigkeiten über das Automatisierungsmodell programmgesteuert bearbeiten. Rufen Sie <xref:EnvDTE.SolutionBuild.BuildDependencies%2A> in das Automatisierungsmodell. Es sind keine verfügbaren VSIP-API-Ebene-Schnittstellen, die die direkte Bearbeitung von den Manager Projektmappenbuild-Konfigurationen und deren Eigenschaften zu ermöglichen.  
  
 Darüber hinaus können Sie ein Raster im Projektfenster für Abhängigkeiten bereitstellen. Weitere Informationen finden Sie unter [Anzeige Eigenschaftenraster](../../extensibility/internals/properties-display-grid.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Verwalten von Konfigurationsoptionen](../../extensibility/internals/managing-configuration-options.md)   
 [Konfiguration des Projekts für die Verwaltung der Bereitstellung](../../extensibility/internals/project-configuration-for-managing-deployment.md)   
 [Projektkonfiguration für die Ausgabe](../../extensibility/internals/project-configuration-for-output.md)
---
title: Projektkonfiguration für die Erstellung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], configuration for building
- project configurations, building
ms.assetid: 2c83615d-fa4d-4b9f-b315-7a69b3000da0
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 799330ffa4fbedc5d1fee1ff4cb2f0dfdb3049f1
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47514960"
---
# <a name="project-configuration-for-building"></a>Projektkonfiguration beim Erstellen
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Projektkonfiguration für das Erstellen von](https://docs.microsoft.com/visualstudio/extensibility/internals/project-configuration-for-building).  
  
Die Liste der Konfigurationen für eine bestimmte Lösung wird im Dialogfeld Projektmappenkonfigurationen verwaltet.  
  
 Ein Benutzer kann weitere Projektmappenkonfigurationen, jeweils mit eigenen eindeutigen Namen erstellen. Wenn der Benutzer eine neue Projektmappenkonfiguration erstellt, standardmäßig die IDE auf den Namen der entsprechenden in den Projekten oder Debuggen, wenn keine entsprechenden Namen vorhanden ist. Der Benutzer kann die Auswahl, um die jeweiligen Anforderungen zu erfüllen, bei Bedarf ändern. Die einzige Ausnahme für dieses Verhalten ist, wenn es sich bei das Projekt eine Konfiguration unterstützt, die den Namen der neuen Projektmappenkonfiguration entspricht. Nehmen wir beispielsweise an, dass eine Projektmappe Projekt1 und "Projekt2" enthält. Projekt1 hat Projektkonfigurationen MyConfig1, Retail- und Debug. "Projekt2" hat die Projektkonfigurationen MyConfig2, Retail- und Debug.  
  
 Wenn der Benutzer eine neue Projektmappenkonfiguration, die mit dem Namen MyConfig2 erstellt, bindet Projekt1 die Debug-Konfiguration an die Projektmappenkonfiguration standardmäßig an. "Projekt2" wird außerdem die MyConfig2-Konfiguration auf die Projektmappenkonfiguration standardmäßig gebunden.  
  
> [!NOTE]
>  Die Bindung ist Groß-/Kleinschreibung.  
  
 Wenn der Benutzer wählt die **Mehrfachauswahl** Element in der Dropdown-Konfigurationsliste die Umgebung zeigt das Dialogfeld, das die Liste mit verfügbaren Konfigurationen bereitstellt.  
  
 ![Konfigurationen mit mehreren](../../extensibility/internals/media/vsmultiplecfgs.gif "VsMultipleCfgs")  
Mehrere Konfigurationen  
  
 In diesem Dialogfeld kann der Benutzer eine oder mehrere Konfigurationen auswählen. Nach der Auswahl entsprechend die Eigenschaftswerten, die auf das Dialogfeld Eigenschaftenseiten angezeigten die Schnittmenge der Werte für die ausgewählten Konfigurationen.  
  
 Finden Sie unter [Projektmappenkonfiguration](../../extensibility/internals/solution-configuration.md) Informationen im Zusammenhang mit hinzufügen und Umbenennen von Konfigurationen für Projektmappen und Projekten.  
  
 Projektabhängigkeiten und Buildreihenfolge sind unabhängige Projektmappenkonfiguration: d. h. Sie können nur einrichten eine Abhängigkeitsstruktur für alle Projekte in der Projektmappe. Mit der rechten Maustaste die Projektmappe oder das Projekt, und wählen entweder die **Projektabhängigkeiten** oder **Projektbuildreihenfolge** option öffnet der **Projektabhängigkeiten** Dialogfeld. Sie können auch aus geöffnet werden die **Projekt** Menü.  
  
 ![Projektabhängigkeiten](../../extensibility/internals/media/vsprojdependencies.gif "VsProjDependencies")  
Projektabhängigkeiten  
  
 Projektabhängigkeiten bestimmt die Reihenfolge, in der Projekte erstellen. Verwenden Sie die Registerkarte "Ziele" im Dialogfeld, um die genaue Reihenfolge anzeigen, in der Projekte in einer Projektmappe erstellen, und verwenden die Registerkarte "Abhängigkeiten", um die Buildreihenfolge zu ändern.  
  
> [!NOTE]
>  Projekte in der Liste, auf denen die Kontrollkästchen ausgewählt, aber werden abgeblendet angezeigt wurde von der Umgebung aufgrund der expliziten Abhängigkeiten, die gemäß der <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency> oder <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency> Schnittstellen und kann nicht geändert werden. Z. B. Hinzufügen eines Projektverweises aus einem [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] Projekt in ein anderes Projekt fügt automatisch eine Buildabhängigkeit, die nur entfernt werden kann, indem Sie nacheinander den Verweis auf. Projekte, deren Kontrollkästchen deaktiviert sind und abgeblendet angezeigt werden, können nicht ausgewählt werden, da auf diese Weise eine Abhängigkeitsschleife erstellt würde (z. B. Projekt1 wäre hängt von "Projekt2" und "Projekt2" wäre Projekt1 abhängig), würde die Builds installieren.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Buildprozesse umfassen die typische kompilieren und Verknüpfen von Operationen, die mit einem einzelnen Buildbefehl aufgerufen werden. Zwei andere Buildprozesse können auch unterstützt werden: eine saubere Operation So löschen Sie alle Ausgabeelemente aus einem vorherigen Build und eine Überprüfung auf dem neuesten Stand, um festzustellen, ob ein Output-Element in einer Konfiguration geändert hat.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> Objekte zurückgeben, eine entsprechende <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> (Merry <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>) ihre Buildprozesse zu verwalten. Um den Status eines Buildvorgangs zu melden, während es ausgeführt wird, die Konfigurationen die Aufrufe an <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildStatusCallback>, eine Schnittstelle, die von der Umgebung implementiert und ein anderes Objekt von buildstatusereignissen interessiert.  
  
 Nachdem Sie erstellt haben, können Konfigurationseinstellungen verwendet werden, um zu bestimmen, und zwar unabhängig davon, ob sie unter der Kontrolle des Debuggers ausgeführt werden können. Implementieren von Konfigurationen <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg> zur Debugunterstützung.  
  
 Nach der Implementierung der projektabhängigkeiten, können Sie die Abhängigkeiten über das Automatisierungsmodell programmgesteuert ändern. Rufen Sie <xref:EnvDTE.SolutionBuild.BuildDependencies%2A> im Automatisierungsmodell. Es gibt keine verfügbaren VSIP-API-Ebene-Schnittstellen, die die direkte Bearbeitung der Projektmappenbuild-Konfigurationen-Manager und ihre Eigenschaften zu ermöglichen.  
  
 Darüber hinaus können Sie ein Raster im Projektfenster Abhängigkeiten bereitstellen. Weitere Informationen finden Sie unter [Anzeigeraster für Eigenschaften](../../extensibility/internals/properties-display-grid.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Verwalten von Konfigurationsoptionen](../../extensibility/internals/managing-configuration-options.md)   
 [Projektkonfiguration für die Verwaltung der Bereitstellung](../../extensibility/internals/project-configuration-for-managing-deployment.md)   
 [Projektkonfiguration für die Ausgabe](../../extensibility/internals/project-configuration-for-output.md)


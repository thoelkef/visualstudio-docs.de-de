---
title: "Konfiguration zum Erstellen des Projekts | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Projekte [Visual Studio SDK] Konfiguration zum Erstellen von"
  - "Projektkonfigurationen erstellen"
ms.assetid: 2c83615d-fa4d-4b9f-b315-7a69b3000da0
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# Konfiguration zum Erstellen des Projekts
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Die Liste der Projektmappenkonfigurationen für eine bestimmte Lösung wird durch das Dialogfeld Projektmappenkonfigurationen verwaltet.  
  
 Ein Benutzer kann zusätzliche Projektmappenkonfigurationen, jeweils mit eigenen eindeutigen Namen erstellen. Wenn ein Benutzer eine neue Projektmappenkonfiguration erstellt, standardmäßig die IDE auf den entsprechenden Konfigurationsnamen in den Projekten oder Debuggen, wenn keine entsprechenden Namen vorhanden ist. Der Benutzer kann die Auswahl, um die jeweiligen Anforderungen erfüllen, bei Bedarf ändern. Die einzige Ausnahme zu diesem Verhalten ist, wenn das Projekt eine Konfiguration unterstützt, die den Namen der neuen Projektmappenkonfiguration entspricht. Nehmen wir beispielsweise an, dass eine Projektmappe Projekt1 und Projekt2 enthält. Project1 hat Projektkonfigurationen Debug, Verkaufs\- und MyConfig1. Projekt2 hat Projektkonfigurationen Debug, Verkaufs\- und MyConfig2.  
  
 Wenn der Benutzer eine neue Projektmappenkonfiguration, die mit dem Namen MyConfig2 erstellt, bindet Project1 die Debug\-Konfiguration an die Projektmappenkonfiguration standardmäßig an. Projekt2 bindet zudem die MyConfig2\-Konfiguration auf die Konfiguration der Projektmappe standardmäßig.  
  
> [!NOTE]
>  Bindung ist Groß\-\/Kleinschreibung.  
  
 Wenn der Benutzer wählt die **Mehrfachauswahl** Element in der Dropdown\-Liste, die Umgebung zeigt ein Dialogfeld mit der Liste der verfügbaren Konfigurationen.  
  
 ![Mehrere Konfigurationen](../../extensibility/internals/media/vsmultiplecfgs.png "vsMultipleCfgs")  
Mehrere Konfigurationen  
  
 In diesem Dialogfeld kann der Benutzer eine oder mehrere Konfigurationen auswählen. Nach der Auswahl entsprechend die Eigenschaftswerte, die auf das Dialogfeld Eigenschaftenseiten angezeigt die Schnittmenge der Werte für die ausgewählten Konfigurationen.  
  
 Finden Sie unter [Projektmappenkonfiguration](../../extensibility/internals/solution-configuration.md) für Informationen zum Hinzufügen und Umbenennen von Konfigurationen für Projektmappen und Projekte.  
  
 Projektabhängigkeiten und Buildreihenfolge sind unabhängige Projektmappenkonfiguration: d. h. Sie können nur Einrichten einer Abhängigkeitsstruktur für alle Projekte in der Projektmappe. Der rechten Maustaste auf die Projektmappe oder das Projekt, und wählen entweder die **Projektabhängigkeiten** oder **Projektbuildreihenfolge** option geöffnet der **Projektabhängigkeiten** \(Dialogfeld\). Es kann auch geöffnet werden die **Projekt** Menü.  
  
 ![Projektabhängigkeiten](../../extensibility/internals/media/vsprojdependencies.png "vsProjDependencies")  
Projektabhängigkeiten  
  
 Abhängigkeiten bestimmt die Reihenfolge, in der Projekte zu erstellen. Verwenden Sie die Registerkarte Buildreihenfolge im Dialogfeld genau der Reihenfolge an, in der Projekte innerhalb einer Projektmappe erstellen, und verwenden die Registerkarte Abhängigkeiten die Buildreihenfolge zu ändern.  
  
> [!NOTE]
>  Projekte in der Liste, die entsprechenden Kontrollkästchen aktiviert, aber abgeblendet hinzugefügt wurden, indem die expliziten Abhängigkeiten, die durch angegebene\-Umgebung die <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency> oder <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency> Schnittstellen und kann nicht geändert werden. Z. B. Hinzufügen eines Projektverweises aus einem [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] Projekt in ein anderes Projekt fügt automatisch eine Buildabhängigkeit, die nur durch Löschen des Verweises entfernt werden kann. Projekte, deren Kontrollkästchen deaktiviert sind, und werden abgeblendet angezeigt, können nicht ausgewählt werden, da dadurch eine Schleife Abhängigkeit erstellen \(z. B. Project1 wäre Projekt2 abhängig und Projekt2 Project1 abhängig ist\), würde die Builds still.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Buildprozesse enthalten die normalen kompilieren und Verknüpfen von Operationen, die mit einem einzelnen Buildbefehl aufgerufen werden. Zwei andere Buildprozesse können auch unterstützt werden: eine saubere Operation zum Löschen von alle Ausgabeelemente aus einem vorherigen Build und eine aktuelle Prüfung zu bestimmen, ob ein Output\-Element in einer Konfiguration geändert hat.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> Objekte zurückgeben eines entsprechenden <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> \(zurückgegeben von <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>\) die Buildprozesse zu verwalten. Um den Status eines Vorgangs Build zu melden, während er ausgeführt wird, die Konfigurationen die Aufrufe an <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildStatusCallback>, eine Schnittstelle implementiert, von der Umgebung, und ein anderes Objekt interessiert Buildereignisse Status.  
  
 Nachdem erstellt, können Konfigurationseinstellungen verwendet werden, zu bestimmen, ob sie unter der Kontrolle des Debuggers ausgeführt werden können. Implementieren von Konfigurationen <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg> zur Debugunterstützung.  
  
 Nach dem Implementieren der Abhängigkeiten, können Sie die Abhängigkeiten über das Automatisierungsmodell programmgesteuert ändern. Rufen Sie <xref:EnvDTE.SolutionBuild.BuildDependencies%2A> im Automatisierungsmodell. Befinden sich keine verfügbaren VSIP\-API\-Ebene, die die direkte Bearbeitung der Build\-Manager Projektmappenkonfigurationen und deren Eigenschaften zu ermöglichen.  
  
 Darüber hinaus können Sie ein Raster im Fenster Abhängigkeiten Projekt bereitstellen. Weitere Informationen finden Sie unter [Raster von Eigenschaften anzeigen](../../extensibility/internals/properties-display-grid.md).  
  
## Siehe auch  
 [Verwalten von Konfigurationsoptionen](../../extensibility/internals/managing-configuration-options.md)   
 [Konfiguration für die Verwaltung der Bereitstellung des Projekts](../../extensibility/internals/project-configuration-for-managing-deployment.md)   
 [Konfiguration für die Ausgabe des Projekts](../../extensibility/internals/project-configuration-for-output.md)
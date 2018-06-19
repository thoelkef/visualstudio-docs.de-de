---
title: Projektkonfiguration für die Verwaltung von Bereitstellung | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project configurations, managing deployment
- projects [Visual Studio SDK], configuration for managing deployment
ms.assetid: bd5940d9-d94d-4944-beda-4ec1ab2bbde5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 723edd078636eb324fc2d5dfca2ae81ef3249a43
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31132249"
---
# <a name="project-configuration-for-managing-deployment"></a>Konfiguration des Projekts für die Verwaltung der Bereitstellung
Bereitstellung dient der Datenmigration die Ausgabeelemente aus einem Buildprozess an den erwarteten Speicherort zum Debuggen und Installation. Z. B. möglicherweise eine Webanwendung auf einem lokalen Computer erstellt und klicken Sie dann auf dem Server platziert werden.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] unterstützt zwei Methoden, um Projekte in der Bereitstellung einbezogen werden können:  
  
-   Wie der Antragsteller des Bereitstellungsprozesses.  
  
-   Wie der Manager des Bereitstellungsprozesses.  
  
 Bevor Lösungen bereitgestellt werden können, müssen Sie zuerst ein Bereitstellungsprojekt zum Konfigurieren der Bereitstellungsoptionen hinzufügen. Wenn das Projekt bereitstellen nicht bereits vorhanden ist, werden Sie gefragt, ob Sie erstellen, wenn Sie auswählen möchten **Projektmappe bereitstellen** aus der **erstellen** Menü oder durch Rechtsklick auf die Projektmappe. Auf **Ja** öffnet die **neues Projekt hinzufügen** Dialogfeld mit den **Remote Assistenten zum Bereitstellen von** Projekt auswählen.  
  
 Der Remote-bereitstellen-Assistent fragt Sie für den Typ der Anwendung (Windows oder Web), die Ausgabe Projektgruppen einschließen, ggf. zusätzlichen Dateien, die Sie einschließen möchten und dem Remotecomputer, die, dem Sie bereitstellen möchten. Die letzte Seite des Assistenten zeigt eine Zusammenfassung der ausgewählten Optionen.  
  
 Projekte, die einen Bereitstellungsprozess werden erzeugen Ausgabeelemente angezeigt, die an einer anderen Umgebung verschoben werden müssen. Diese Ausgabe beschriebenen Elemente als Parameter für die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> -Schnittstelle, deren primären Zweck If, um Projekte zu Gruppe Ausgaben zu ermöglichen. Weitere Informationen über die Implementierung von `IVsProjectCfg2`, finden Sie unter [Projektkonfiguration für die Ausgabe](../../extensibility/internals/project-configuration-for-output.md).  
  
 Bereitstellungsprojekte, die den Bereitstellungsprozess zu verwalten, aktivieren den Befehl bereitstellen und Antworten, wenn dieser Befehl aktiviert ist. Bereitstellungsprojekte implementieren die <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> Schnittstelle zum Durchführen der Bereitstellung und Aufrufe an die <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployStatusCallback> Schnittstelle, um den Bericht bereitstellen Statusereignisse.  
  
 Konfigurationen können Abhängigkeiten angeben, die ihrer Erstellung oder Bereitstellung Vorgänge auswirken. Erstellen oder Bereitstellen Abhängigkeiten sind Projekte, die müssen entweder erstellt oder bereitgestellt werden, vor oder nach der Konfigurationen selbst erstellt oder bereitgestellt werden. Buildabhängigkeiten zwischen Projekten werden beschrieben, mit der <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency> Schnittstelle und Bereitstellen von Abhängigkeiten mit dem <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency> Schnittstelle. Weitere Informationen finden Sie unter [Projektkonfiguration zum Erstellen von](../../extensibility/internals/project-configuration-for-building.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Verwalten von Konfigurationsoptionen](../../extensibility/internals/managing-configuration-options.md)   
 [Konfiguration für die Erstellung des Projekts](../../extensibility/internals/project-configuration-for-building.md)   
 [Projektkonfiguration für die Ausgabe](../../extensibility/internals/project-configuration-for-output.md)
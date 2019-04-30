---
title: Projektkonfiguration für die Verwaltung der Bereitstellung von | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project configurations, managing deployment
- projects [Visual Studio SDK], configuration for managing deployment
ms.assetid: bd5940d9-d94d-4944-beda-4ec1ab2bbde5
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6c9bf9dd71007e3a33a217a7ec30b357cd211b00
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62909342"
---
# <a name="project-configuration-for-managing-deployment"></a>Projektkonfiguration für die Verwaltung der Bereitstellung
Die Bereitstellung ist der Vorgang der Datenmigration die Ausgabeelemente aus einem Buildprozess an den erwarteten Speicherort für das Debuggen und die Installation. Beispielsweise kann eine Webanwendung basiert auf einem lokalen Computer und klicken Sie dann auf dem Server platziert werden.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] unterstützt zwei Methoden, um Projekte in der Bereitstellung einbezogen werden können:

- Wie der Antragsteller des Bereitstellungsprozesses.

- Wie der Manager des Bereitstellungsprozesses.

  Bevor Lösungen bereitgestellt werden können, müssen Sie zuerst ein Bereitstellungsprojekt zum Konfigurieren von Optionen für die Bereitstellung hinzufügen. Wenn das Projekt bereitstellen, nicht bereits vorhanden ist, werden Sie gefragt, ob Sie bei der Auswahl erstellen möchten **Projektmappe bereitstellen** aus der **erstellen** Menü oder durch Rechtsklick auf die Projektmappe. Auf **Ja** öffnet die **neues Projekt hinzufügen** Dialogfeld mit den **Remote Assistenten zum Bereitstellen von** Projekt ausgewählt.

  Der Assistent für Remote bereitstellen aufgefordert, für den Typ der Anwendung ("Windows" oder "Web"), die Ausgabe Projektgruppen einschließen, weiteren Dateien, die Sie einschließen möchten und dem Remotecomputer, die, dem Sie bereitstellen möchten. Die letzte Seite des Assistenten zeigt eine Zusammenfassung der ausgewählten Optionen.

  Projekte, die einen Bereitstellungsprozess werden führen Ausgabe-Elementen, die in einer anderen Umgebung verschoben werden müssen. Diese Ausgabe Elemente gelten als Parameter für die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> -Schnittstelle, deren primären Zweck If in Projekten an Group-Ausgaben zu ermöglichen. Weitere Informationen über die Implementierung von `IVsProjectCfg2`, finden Sie unter [Projektkonfiguration für die Ausgabe](../../extensibility/internals/project-configuration-for-output.md).

  Bereitstellungsprojekte, die den Bereitstellungsprozess zu verwalten, aktivieren Sie den Befehl bereitstellen und Antworten, wenn dieser Befehl aktiviert ist. Bereitstellungsprojekte implementieren die <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> Benutzeroberfläche zum Durchführen der Bereitstellung und Aufrufe an die <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployStatusCallback> Schnittstelle, um den Bericht bereitstellen Statusereignisse.

  Konfigurationen können Abhängigkeiten angeben, die ihre Builds oder Bereitstellungen Vorgänge auswirken. Erstellen oder Bereitstellen Abhängigkeiten sind Projekte, die entweder integriert oder müssen bereitgestellt werden, vor oder nach der die Konfigurationen selbst erstellt oder bereitgestellt werden. Buildabhängigkeiten zwischen Projekten werden beschrieben, mit der <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency> Schnittstelle und Bereitstellen von Abhängigkeiten mit der <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency> Schnittstelle. Weitere Informationen finden Sie unter [Projektkonfiguration für das Erstellen von](../../extensibility/internals/project-configuration-for-building.md).

## <a name="see-also"></a>Siehe auch
- [Verwalten von Konfigurationsoptionen](../../extensibility/internals/managing-configuration-options.md)
- [Projektkonfiguration beim Erstellen](../../extensibility/internals/project-configuration-for-building.md)
- [Projektkonfiguration für die Ausgabe](../../extensibility/internals/project-configuration-for-output.md)
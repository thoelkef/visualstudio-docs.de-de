---
title: Projektkonfiguration für die Verwaltung der Bereitstellung | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project configurations, managing deployment
- projects [Visual Studio SDK], configuration for managing deployment
ms.assetid: bd5940d9-d94d-4944-beda-4ec1ab2bbde5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 62f7bf6535a89e46799ade88fe8976974b3019c5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706710"
---
# <a name="project-configuration-for-managing-deployment"></a>Projektkonfiguration für die Verwaltung der Bereitstellung
Bei der Bereitstellung werden die Ausgabeelemente physisch von einem Buildprozess an den erwarteten Speicherort für das Debuggen und Installieren bewegt. Beispielsweise kann eine Webanwendung auf einem lokalen Computer erstellt und dann auf dem Server platziert werden.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]unterstützt zwei Möglichkeiten, wie Projekte in die Bereitstellung einbezogen werden können:

- Als Thema des Bereitstellungsprozesses.

- Als Manager des Bereitstellungsprozesses.

  Bevor Lösungen bereitgestellt werden können, müssen Sie zunächst ein Bereitstellungsprojekt hinzufügen, um Bereitstellungsoptionen zu konfigurieren. Wenn das Bereitstellungsprojekt noch nicht vorhanden ist, werden Sie gefragt, ob Sie eine Lösung erstellen möchten, wenn Sie im Menü **Build** die Option **Lösung bereitstellen** auswählen oder mit der rechten Maustaste auf die Projektmappe klicken. Wenn Sie auf **Ja** klicken, wird das Dialogfeld **Neues Projekt hinzufügen** geöffnet, in dem das Projekt des **Remotebereitstellungs-Assistenten** ausgewählt ist.

  Der Remotebereitstellungs-Assistent fragt Sie nach dem Anwendungstyp (Windows oder Web), den einzuschließenden Projektausgabegruppen, allen zusätzlichen Dateien, die Sie einschließen möchten, und dem Remotecomputer, auf dem Sie bereitstellen möchten. Auf der letzten Seite des Assistenten wird eine Zusammenfassung der ausgewählten Optionen angezeigt.

  Projekte, die Gegenstand eines Bereitstellungsprozesses sind, erzeugen Ausgabeelemente, die in eine alternative Umgebung verschoben werden müssen. Diese Ausgabeelemente werden als <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> Parameter für die Schnittstelle beschrieben, deren Hauptzweck, wenn Projekte Ausgaben gruppieren können. Weitere Informationen zur Implementierung `IVsProjectCfg2`von finden Sie unter [Projektkonfiguration für Ausgabe](../../extensibility/internals/project-configuration-for-output.md).

  Bereitstellungsprojekte, die den Bereitstellungsprozess verwalten, aktivieren den Befehl Bereitstellen und reagieren, wenn dieser Befehl ausgewählt ist. Bereitstellungsprojekte <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> implementieren die Schnittstelle, um die <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployStatusCallback> Bereitstellung auszuführen und Aufrufe an die Schnittstelle auszuführen, um Bereitstellungsstatusereignisse zu melden.

  Konfigurationen können Abhängigkeiten angeben, die sich auf ihre Build- oder Bereitstellungsvorgänge auswirken. Build- oder Bereitstellungsabhängigkeiten sind Projekte, die entweder erstellt oder bereitgestellt werden müssen, bevor oder nachdem die Konfigurationen selbst erstellt oder bereitgestellt wurden. Buildabhängigkeiten zwischen Projekten werden <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency> mit der Schnittstelle beschrieben <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency> und stellen Abhängigkeiten mit der Schnittstelle bereit. Weitere Informationen finden Sie unter [Projektkonfiguration für Das Erstellen](../../extensibility/internals/project-configuration-for-building.md).

## <a name="see-also"></a>Weitere Informationen
- [Verwalten von Konfigurationsoptionen](../../extensibility/internals/managing-configuration-options.md)
- [Projektkonfiguration beim Erstellen](../../extensibility/internals/project-configuration-for-building.md)
- [Projektkonfiguration für die Ausgabe](../../extensibility/internals/project-configuration-for-output.md)

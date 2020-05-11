---
title: Projektkonfiguration für Gebäude | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], configuration for building
- project configurations, building
ms.assetid: 2c83615d-fa4d-4b9f-b315-7a69b3000da0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bdd084053e06206a99298b234b4d51c8504119a2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706734"
---
# <a name="project-configuration-for-building"></a>Projektkonfiguration beim Erstellen
Die Liste der Lösungskonfigurationen für eine bestimmte Lösung wird im Dialogfeld Lösungskonfigurationen verwaltet.

 Ein Benutzer kann zusätzliche Lösungskonfigurationen mit jeweils einem eigenen Namen erstellen. Wenn der Benutzer eine neue Projektmappenkonfiguration erstellt, wird die IDE standardmäßig auf den entsprechenden Konfigurationsnamen in den Projekten oder debuggen, wenn kein entsprechender Name vorhanden ist. Der Benutzer kann die Auswahl bei Bedarf an bestimmte Anforderungen anpassen. Die einzige Ausnahme von diesem Verhalten ist, wenn das Projekt eine Konfiguration unterstützt, die mit dem Namen der neuen Projektmappenkonfiguration übereinstimmt. Angenommen, eine Projektmappe enthält Project1 und Project2. Project1 verfügt über projektkonfigurationen Debug, Retail und MyConfig1. Project2 verfügt über Projektkonfigurationen Debug, Retail und MyConfig2.

 Wenn der Benutzer eine neue Projektmappenkonfiguration mit dem Namen MyConfig2 erstellt, bindet Project1 standardmäßig seine Debugkonfiguration an die Projektmappenkonfiguration. Project2 bindet auch seine MyConfig2-Konfiguration standardmäßig an die Projektmappenkonfiguration.

> [!NOTE]
> Bei der Bindung wird die Groß-/Kleinschreibung nicht berücksichtigt.

 Wenn der Benutzer das Element **Mehrfachauswahl** in der Dropdownliste Konfiguration auswählt, zeigt die Umgebung ein Dialogfeld an, das die Liste der verfügbaren Konfigurationen bereitstellt.

 ![Mehrere Konfigurationen](../../extensibility/internals/media/vsmultiplecfgs.gif "vsMultipleCfgs") Mehrere Konfigurationen

 In diesem Dialogfeld kann der Benutzer eine oder mehrere Konfigurationen auswählen. Nach der Auswahl spiegeln die Eigenschaftenwerte, die im Dialogfeld Eigenschaftenseiten angezeigt werden, den Schnittpunkt der Werte für die ausgewählten Konfigurationen wider.

 Weitere Informationen zum Hinzufügen und Umbenennen von Konfigurationen für Lösungen und Projekte finden Sie unter [Lösungskonfiguration.](../../extensibility/internals/solution-configuration.md)

 Projektabhängigkeiten und Buildreihenfolge sind lösungsunabhängig, d. h., Sie können nur eine Abhängigkeitsstruktur für alle Projekte in der Projektmappe einrichten. Wenn Sie mit der rechten Maustaste auf die Projektmappe oder das Projekt klicken und entweder die Option **Projektabhängigkeiten** oder **Projektbuildreihenfolge** auswählen, wird das Dialogfeld **Projektabhängigkeiten** geöffnet. Es kann auch über das **Menü Projekt** geöffnet werden.

 ![Projektabhängigkeiten](../../extensibility/internals/media/vsprojdependencies.gif "vsProjAbhängigkeiten") Projektabhängigkeiten

 Projektabhängigkeiten bestimmen die Reihenfolge, in der Projekte erstellt werden. Verwenden Sie die Registerkarte Bestellerstellung im Dialogfeld, um die genaue Reihenfolge anzuzeigen, in der Projekte innerhalb einer Projektmappe erstellt werden, und verwenden Sie die Registerkarte Abhängigkeiten, um die Buildreihenfolge zu ändern.

> [!NOTE]
> Projekte in der Liste, deren Kontrollkästchen aktiviert sind, aber abgeblendet angezeigt werden, <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency> wurden <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency> von der Umgebung aufgrund expliziter Abhängigkeiten hinzugefügt, die von der oder den Schnittstellen angegeben wurden, und können nicht geändert werden. Wenn Sie z. B. [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] einen Projektverweis aus einem Projekt zu einem anderen Projekt hinzufügen, wird automatisch eine Buildabhängigkeit hinzugefügt, die nur durch Löschen des Verweises entfernt werden kann. Projekte, deren Kontrollkästchen klar sind und abgeblendet erscheinen, können nicht ausgewählt werden, da dadurch eine Abhängigkeitsschleife erstellt würde (z. B. wäre Project1 von Project2 und Project2 von Project1 abhängig), wodurch der Build blockiert würde.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Buildprozesse umfassen die typischen Kompilierungs- und Verknüpfungsvorgänge, die mit einem einzelnen Buildbefehl aufgerufen werden. Zwei weitere Buildprozesse können ebenfalls unterstützt werden: ein sauberer Vorgang zum Löschen aller Ausgabeelemente aus einem vorherigen Build und eine aktuelle Prüfung, um festzustellen, ob sich ein Ausgabeelement in einer Konfiguration geändert hat.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>Objekte geben <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> eine entsprechende <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>(von zurückgegeben) zurück, um ihre Buildprozesse zu verwalten. Um den Status eines Buildvorgangs zu melden, während <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildStatusCallback>dieser Vorgang auftritt, rufen Konfigurationen auf , eine Schnittstelle, die von der Umgebung und allen anderen Objekten implementiert wird, die an Buildstatusereignissen interessiert sind.

 Nach der Erstellten können Konfigurationseinstellungen verwendet werden, um zu bestimmen, ob sie unter der Kontrolle des Debuggers ausgeführt werden können. Konfigurationen <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg> implementieren, um das Debuggen zu unterstützen.

 Nach dem Implementieren der Projektabhängigkeiten können Sie die Abhängigkeiten über das Automatisierungsmodell programmgesteuert bearbeiten. Sie <xref:EnvDTE.SolutionBuild.BuildDependencies%2A> rufen das Automatisierungsmodell auf. Es sind keine Schnittstellen auf VSIP-API-Ebene verfügbar, die die direkte Bearbeitung der Lösungsbuild-Manager-Konfigurationen und ihrer Eigenschaften ermöglichen.

 Darüber hinaus können Sie ein Raster im Fenster Projektabhängigkeiten bereitstellen. Weitere Informationen finden Sie unter [Eigenschaftenanzeigeraster](../../extensibility/internals/properties-display-grid.md).

## <a name="see-also"></a>Weitere Informationen
- [Verwalten von Konfigurationsoptionen](../../extensibility/internals/managing-configuration-options.md)
- [Projektkonfiguration für die Verwaltung der Bereitstellung](../../extensibility/internals/project-configuration-for-managing-deployment.md)
- [Projektkonfiguration für die Ausgabe](../../extensibility/internals/project-configuration-for-output.md)

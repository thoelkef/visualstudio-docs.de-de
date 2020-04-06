---
title: Lösungskonfiguration | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solution configurations
ms.assetid: f22cfc75-3e31-4e0d-88a9-3ca99539203b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7c96b73747ef8b136a74a7256cde7fef8d1c42de
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705377"
---
# <a name="solution-configuration"></a>Projektmappenkonfiguration
Lösungskonfigurationen speichern Eigenschaften auf Lösungsebene. Sie leiten das Verhalten der **Start-Taste** (F5) und der **Build-Befehle.** Standardmäßig erstellen und starten diese Befehle die Debugkonfiguration. Beide Befehle werden im Kontext einer Lösungskonfiguration ausgeführt. Dies bedeutet, dass der Benutzer erwarten kann, dass F5 unabhängig davon, ob die aktive Lösung über die Einstellungen konfiguriert ist, F5 startet und erstellt. Die Umgebung ist so konzipiert, dass sie für Lösungen und nicht für Projekte optimiert wird, wenn es um das Bauen und Laufen geht.

 Die standardmäßige Visual Studio-Symbolleiste enthält eine Startschaltfläche und eine Dropdown-Liste für die Lösungskonfiguration rechts neben der Startschaltfläche. In dieser Liste können Benutzer die Konfiguration auswählen, die beim Drücken von F5 gestartet werden soll, eigene Lösungskonfigurationen erstellen oder eine vorhandene Konfiguration bearbeiten.

> [!NOTE]
> Es gibt keine Erweiterbarkeitsschnittstellen zum Erstellen oder Bearbeiten der Lösungskonfigurationen. Hierzu muss `DTE.SolutionBuild` verwendet werden. Es gibt jedoch Erweiterbarkeits-APIs für die Verwaltung des Lösungsbuilds. Weitere Informationen finden Sie unter <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2>.

 So können Sie die von Ihrem Projekttyp unterstützten Projektmappenkonfigurationen implementieren:

- Project

   Zeigt die Namen der Projekte an, die in der aktuellen Projektmappe gefunden wurden.

- Konfiguration

   Implementieren Sie , <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>um die Liste der Konfigurationen bereitzustellen, die vom Projekttyp unterstützt und auf den Eigenschaftenseiten angezeigt werden.

   In der Spalte Konfiguration wird der Name der Projektkonfiguration angezeigt, die in dieser Projektmappenkonfiguration erstellt werden soll, und alle Projektkonfigurationen werden aufgelistet, wenn Sie auf die Pfeilschaltfläche klicken. Die Umgebung <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgNames%2A> ruft die Methode zum Ausfüllen dieser Liste auf. Wenn <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgProviderProperty%2A> die Methode angibt, dass das Projekt die Konfigurationsbearbeitung unterstützt, werden Neue oder Bearbeitungsauswahlen auch unter der Überschrift Konfiguration angezeigt. Jede dieser Auswahlen startet Dialogfelder, `IVsCfgProvider2` in denen Methoden der Schnittstelle aufgerufen werden, um die Konfigurationen des Projekts zu bearbeiten.

   Wenn ein Projekt keine Konfigurationen unterstützt, werden in der Spalte Konfiguration Keine angezeigt und ist deaktiviert.

- Plattform

   Zeigt die Plattform an, für die die ausgewählte Projektkonfiguration erstellt wurde, und listet alle verfügbaren Plattformen für das Projekt auf, wenn Sie auf die Pfeilschaltfläche klicken. Die Umgebung <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetPlatformNames%2A> ruft die Methode zum Ausfüllen dieser Liste auf. Wenn <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgProviderProperty%2A> die Methode angibt, dass das Projekt die Plattformbearbeitung unterstützt, werden Neue oder Bearbeitungsauswahlen auch unter der Überschrift Plattform angezeigt. Jede dieser Auswahlen startet Dialogfelder, in denen Methoden zum Bearbeiten der verfügbaren Plattformen des Projekts aufgerufen `IVsCfgProvider2` werden.

   Wenn ein Projekt plattformennicht unterstützt, werden in der Plattformspalte für dieses Projekt Keine angezeigt und ist deaktiviert.

- Build

   Gibt an, ob das Projekt von der aktuellen Projektmappenkonfiguration erstellt wird. Nicht ausgewählte Projekte werden nicht erstellt, wenn die Buildbefehle auf Projektmappenebene trotz aller darin enthaltenen Projektabhängigkeiten aufgerufen werden. Projekte, die nicht für die Bereitstellung ausgewählt wurden, sind weiterhin beim Debuggen, Ausführen, Verpacken und Bereitstellen der Projektmappe enthalten.

- Bereitstellen

   Gibt an, ob das Projekt bereitgestellt wird, wenn die Befehle Start oder Deploy mit der ausgewählten Projektmappenbuildkonfiguration verwendet werden. Das Kontrollkästchen für dieses Feld ist verfügbar, wenn das <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> Projekt <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> die Bereitstellung unterstützt, indem die Schnittstelle für das Objekt implementiert wird.

  Sobald eine neue Lösungskonfiguration hinzugefügt wurde, kann der Benutzer diese aus dem Dropdown-Listenfeld Lösungskonfiguration auf der Standardsymbolleiste auswählen, um diese Konfiguration zu erstellen und/oder zu starten.

## <a name="see-also"></a>Weitere Informationen
- [Verwalten von Konfigurationsoptionen](../../extensibility/internals/managing-configuration-options.md)
- [Projektkonfiguration beim Erstellen](../../extensibility/internals/project-configuration-for-building.md)
- [Projektkonfigurationsobjekt](../../extensibility/internals/project-configuration-object.md)

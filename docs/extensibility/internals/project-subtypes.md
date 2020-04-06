---
title: Projektuntertypen | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], subtypes
- project subtypes [Visual Studio SDK]
ms.assetid: d235b47b-cf11-4d47-a63f-e33d9d16105d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 71dab4767c806b44cbd1f9638738b4a13d6b2bcb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706408"
---
# <a name="project-subtypes"></a>Projektuntertypen
Mit Projektuntertypen können Sie das Verhalten der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Projektsysteme von anpassen oder anpassen. Zu den Anpassungen gehören das Speichern zusätzlicher Daten in der Projektdatei, das Hinzufügen oder Filtern von Elementen im Dialogfeld **Neues Element hinzufügen,** das Steuern, wie Assemblys gedebuggen und bereitgestellt werden, und das Erweitern des Dialogfelds **Eigenschaftenseiten** des Projekts. VSPackages implementieren Projektuntertypen mithilfe der COM-Aggregation.

> [!NOTE]
> Das Visual C++-Projektsystem unterstützt keine Projektuntertypen. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]selbst verwendet Projektuntertypen, um SQL Server- und Smart Device-Projekte zu implementieren.

## <a name="in-this-section"></a>In diesem Abschnitt
- [Entwurf von Projektuntertypen](../../extensibility/internals/project-subtypes-design.md)

 Beschreibt das Konzept von Projektuntertypen.

- [Initialisierungssequenz von Projektuntertypen](../../extensibility/internals/initialization-sequence-of-project-subtypes.md)

 Beschreibt die programmgesteuerte Projektsubtypinitialisierungssequenz nach [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Umgebung.

- [Eigenschaften und Methoden, die von Projektuntertypen erweitert werden](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)

 Enthält detaillierte Beschreibungen der Features und Methoden, die am häufigsten durch die Verwendung von Projektuntertypen erweitert werden.

- [Beibehalten von Daten in der MSBuild-Projektdatei](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)

 Beschreibt, wie Daten in einer Projektdatei <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> beibehalten werden und wie die Daten in der Projektdatei über die Aggregationsebenen des Projektsubtyps hinweg verwaltet werden.

- [Benutzeroberfläche für Projekteigenschaften](../../extensibility/internals/project-property-user-interface.md)

 Beschreibt, wie Projektuntertypen das Dialogfeld **Eigenschaftenseiten** des Projekts ändern können.

- [Erweitern des Objektmodells des Basisprojekts](../../extensibility/internals/extending-the-object-model-of-the-base-project.md)

 Enthält Informationen dazu, wie Projektuntertypen Automation Extender verwenden können, um das Automatisierungsobjektmodell zu erweitern.

- [Mitwirken am Dialogfeld „Neues Element hinzufügen“](../../extensibility/internals/contributing-to-the-add-new-item-dialog-box.md)

 Beschreibt das Hinzufügen von Elementen zum Dialogfeld **Neues Element hinzufügen.**

- [Speichern von Daten in Projektdateien](../../extensibility/saving-data-in-project-files.md)

 Erläutert, wie ein Projektuntertyp subtypspezifische Daten in der Projektdatei mithilfe des Managed Package Framework (MPF) speichern und abrufen kann.

- [Behandlung einer speziellen Bereitstellung](../../extensibility/internals/handling-specialized-deployment.md)

 Erläutert, wie Projektuntertypen durch Implementieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> der Schnittstelle ein spezielles Bereitstellungsverhalten bereitstellen können.

- [Hinzufügen und Entfernen von Eigenschaftenseiten](../../extensibility/adding-and-removing-property-pages.md)

 Beschreibt das Hinzufügen und Entfernen von Eigenschaftenseiten im Projekt-Designer.

## <a name="related-sections"></a>Verwandte Abschnitte
- [Projekttypen](../../extensibility/internals/project-types.md)

 Enthält Links zu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Themen, in denen Projekte detailliert beschrieben werden.

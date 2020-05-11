---
title: Hinzufügen von Projekt- und Projektelementvorlagen | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], adding
- project items [Visual Studio], adding
ms.assetid: 8c59217f-56e5-4540-a73b-cd10de189373
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 14eb1a9e2e63fa6e63d3ba2efa4426421e6b5593
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710207"
---
# <a name="add-project-and-project-item-templates"></a>Hinzufügen von Projekt- und Projektelementvorlagen
Wenn Sie eigene Projekttypen erstellen, müssen Sie das Hinzufügen neuer Projekte [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] und Projektelemente mithilfe der Dialogfelder der integrierten Standardentwicklungsumgebung (IDE) unterstützen. In den folgenden Themen werden verschiedene Techniken zum Hinzufügen von Projekten und Projektelementen erläutert.

## <a name="in-this-section"></a>In diesem Abschnitt
- [Projektkontext](../../extensibility/internals/project-context.md)

 Erläutert, dass das Projekt die meisten Kontextinformationen für das, was in der Umgebung geschieht, bereitstellt.

- [Projektpriorität](../../extensibility/internals/project-priority.md)

 Erläutert, dass ein Projektelement in der Regel Mitglied eines Projekts ist, um Unklarheiten darüber zu vermeiden, welches Projekt zum Öffnen des Elements verwendet wird.

- [Projekt "Verschiedene Dateien"](../../extensibility/internals/miscellaneous-files-project.md)

 Enthält Informationen zu den beiden Editortypen, die zum Öffnen von Dateien in einem Projekt verwendet werden können, und der Rolle, die das Projekt bei der Bestimmung des Editors spielt, der beim Öffnen eines Projektelements verwendet werden soll.

- [Registrieren von Projekt- und Elementvorlagen](../../extensibility/internals/registering-project-and-item-templates.md)

 Erläutert, was [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] beim Erstellen eines Projekts geschieht.

- [Hinzufügen von Elementen zum Dialogfeld Neues Element hinzufügen](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)

 Erläutert den Vorgang zum Hinzufügen von Elementen zum Dialogfeld **Neues Element hinzufügen.**

- [Hinzufügen von Verzeichnissen zum Dialogfeld Neues Projekt](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)

 Enthält ein Beispiel für die Registrierung eines neuen Verzeichnisses, das benutzerdefinierte Vorlagen enthält, die von einem VSPackage bereitgestellt werden.

- [Hinzufügen von Verzeichnissen zum Dialogfeld Neues Element hinzufügen](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)

 Enthält ein Beispiel für das Registrieren eines neuen Satzes von Verzeichnissen für das Dialogfeld **Neues Element hinzufügen.**

- [IDE-definierte Befehle zum Erweitern von Projektsystemen](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)

 Listet verschiedene Arten von Befehlselementen auf, die zum Erweitern von Projektsystemen verwendet werden.

- [CATIDs für Objekte, die in der Regel zum Erweitern von Projekten verwendet werden](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)

 Listet CATIDs für Objekte auf, [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]die [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] zum Erweitern [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]von , und Projektsystemen verwendet werden.

## <a name="related-sections"></a>Verwandte Abschnitte
- [Gewusst wie: Öffnen sie projektspezifische Editoren](../../extensibility/how-to-open-project-specific-editors.md)

 Enthält schrittweise Anweisungen zum Öffnen eines Elements, das an einen bestimmten Editor für ein Projekt gebunden ist.

- [Gewusst wie: Öffnen von Standard-Editoren](../../extensibility/how-to-open-standard-editors.md)

 Enthält Schritt-für-Schritt-Anleitungen zum Öffnen eines Standard-Editors.

- [Projektuntertypen](../../extensibility/internals/project-subtypes.md)

 Stellt Verknüpfungen zu konzeptionellen Themen des Projektuntertyps bereit. Projektuntertypen erweitern [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] vorhandene und Projekte.

- [Projekttypen](../../extensibility/internals/project-types.md)

 Enthält Links zu weiteren Themen, die Informationen zum Entwerfen neuer Projekttypen enthalten.

---
title: Hinzufügen von Projekt-und Projekt Element Vorlagen | Microsoft-Dokumentation
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80710207"
---
# <a name="add-project-and-project-item-templates"></a>Projekt-und Projekt Element Vorlagen hinzufügen
Wenn Sie eigene Projekttypen erstellen, müssen Sie Unterstützung für das Hinzufügen neuer Projekte und Projekt Elemente mithilfe der Standard [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Dialogfelder für die integrierte Entwicklungsumgebung (Integrated Development Environment, IDE) bereitstellen. In den folgenden Themen werden die verschiedenen Techniken zum Hinzufügen von Projekten und Projekt Elementen erläutert.

## <a name="in-this-section"></a>In diesem Abschnitt
- [Projektkontext](../../extensibility/internals/project-context.md)

 Erläutert, dass das Projekt die meisten Kontextinformationen für die Vorgänge in der Umgebung bereitstellt.

- [Projekt Priorität](../../extensibility/internals/project-priority.md)

 Erläutert, dass ein Projekt Element normalerweise ein Member eines Projekts ist, um die Mehrdeutigkeit zu vermeiden, welches Projekt zum Öffnen des Elements verwendet wird.

- [Projekt "sonstige Dateien"](../../extensibility/internals/miscellaneous-files-project.md)

 Stellt Informationen über die beiden Typen von Editoren bereit, die zum Öffnen von Dateien in einem Projekt verwendet werden können, und die Rolle, die das Projekt beim Festlegen des zu verwendenden Editors verwendet, wenn ein Projekt Element geöffnet wird.

- [Registrieren von Projekt-und Element Vorlagen](../../extensibility/internals/registering-project-and-item-templates.md)

 Erläutert, was geschieht, wenn ein [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Projekt erstellt wird.

- [Hinzufügen von Elementen zum Dialogfeld "Neues Element hinzufügen"](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)

 Erläutert den Prozess zum Hinzufügen von Elementen zum Dialogfeld **Neues Element hinzufügen** .

- [Hinzufügen von Verzeichnissen zum Dialogfeld "Neues Projekt"](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)

 Enthält ein Beispiel für die Registrierung eines neuen Verzeichnisses, das benutzerdefinierte Vorlagen enthält, die von einem VSPackage bereitgestellt werden.

- [Hinzufügen von Verzeichnissen zum Dialogfeld "Neues Element hinzufügen"](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)

 Enthält ein Beispiel für das Registrieren eines neuen Satzes von Verzeichnissen für das Dialogfeld **Neues Element hinzufügen** .

- [IDE-definierte Befehle zum Erweitern von Projekt Systemen](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)

 Listet verschiedene Typen von Befehls Elementen auf, die zum Erweitern von Projekt Systemen verwendet werden.

- [CATIDs für Objekte, die in der Regel zum Erweitern von Projekten verwendet werden](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)

 Listet CATIDs für Objekte auf, die verwendet werden, um [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] -,-und- [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] Projektsysteme zu erweitern.

## <a name="related-sections"></a>Verwandte Abschnitte
- [Gewusst wie: Öffnen von projektspezifischen Editoren](../../extensibility/how-to-open-project-specific-editors.md)

 Enthält Schritt-für-Schritt-Anweisungen zum Öffnen eines Elements, das intrinsisch an einen bestimmten Editor für ein Projekt gebunden ist.

- [Vorgehensweise: Öffnen von Standard-Editoren](../../extensibility/how-to-open-standard-editors.md)

 Enthält Schritt-für-Schritt-Anweisungen zum Öffnen eines Standard-Editors.

- [Projekt Untertypen](../../extensibility/internals/project-subtypes.md)

 Enthält Links zu konzeptionellen Themen des Projekt unter Typs. Projekt Untertypen erweitern vorhandene [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] -und- [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] Projekte.

- [Projekttypen](../../extensibility/internals/project-types.md)

 Enthält Links zu weiteren Themen, in denen Informationen zum Entwerfen neuer Projekttypen angeboten werden.

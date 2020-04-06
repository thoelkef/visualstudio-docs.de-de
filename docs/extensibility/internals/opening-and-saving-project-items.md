---
title: Öffnen und Speichern von Projektelementen | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], file persistence
- files [Visual Studio], opening and saving
- editors [Visual Studio SDK], file persistence
ms.assetid: f71898ad-335f-4c43-a177-4da87078afd1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bbb89d99e401be6bae7d8ee9be8ee33fa7574723
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706972"
---
# <a name="opening-and-saving-project-items"></a>Öffnen und Speichern von Projektelementen
Wenn Sie einen neuen Projekttyp hinzufügen, müssen Sie das Öffnen [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] und Speichern Ihrer Projektdateien in der integrierten Entwicklungsumgebung (IDE) verwalten. In den folgenden Themen werden die verschiedenen Ansätze zum Öffnen und Speichern von Dateien erläutert.

## <a name="in-this-section"></a>In diesem Abschnitt
- [Anzeigen von Dateien mit dem Befehl „Datei öffnen“](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)

 Enthält eine schrittweise Erläuterung, wie die IDE den Befehl **"Datei öffnen"** verarbeitet und welche Rolle Projekte bei der Beantwortung dieses Befehls spielen.

- [Anzeigen von Dateien mit dem Befehl „Öffnen mit“](../../extensibility/internals/displaying-files-by-using-the-open-with-command.md)

 Bietet eine detaillierte, schrittweise Erklärung, wie die IDE den Befehl **"Öffnen mit"** verarbeitet, und fordert das Öffnen einer Datei an, die eine Auswahl an Standard-Editoren enthält.

- [Gewusst wie: Öffnen von projektspezifischen Editoren](../../extensibility/how-to-open-project-specific-editors.md)

 Enthält schrittweise Anweisungen zum Angeben, dass Dateien eines bestimmten Typs in Ihrem Projekt mithilfe eines projektspezifischen Editors geöffnet werden sollen.

- [Gewusst wie: Öffnen von Standard-Editoren](../../extensibility/how-to-open-standard-editors.md)

 Enthält schrittweise Anweisungen zum Angeben, wie die IDE das Öffnen eines Standard-Editors für Dateien in Ihrem Projekttyp aktivieren kann.

- [Gewusst wie: Öffnen von Editoren für geöffnete Dokumente](../../extensibility/how-to-open-editors-for-open-documents.md)

 Enthält schritt für Schritt Anweisungen zum Öffnen eines projektspezifischen Editors für eine geöffnete Datei.

- [Speichern eines Standarddokuments](../../extensibility/internals/saving-a-standard-document.md)

 Enthält eine detaillierte Erläuterung, wie die IDE die Befehle **Speichern**, **Speichern unter**und Speichern **aller** Befehle für ein Dokument verarbeitet, das in einem Standardeditor geöffnet wurde.

- [Speichern eines benutzerdefinierten Dokuments](../../extensibility/internals/saving-a-custom-document.md)

 Enthält ein Diagramm und eine detaillierte Erläuterung, wie die IDE die Befehle **Speichern**, **Speichern unter**und **Speichern aller** Befehle für Dokumente verarbeitet, die in einem benutzerdefinierten Editor geöffnet werden.

- [Bestimmen, welcher Editor eine Datei in einem Projekt öffnet](../../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)

 Erläutert den Prozess, dem die IDE folgt, um den entsprechenden Editor oder Designer für eine Datei auszuwählen.

## <a name="related-sections"></a>Verwandte Abschnitte
- [Erstellen von benutzerdefinierten Editoren und Designern](../../extensibility/creating-custom-editors-and-designers.md)

 Listet die vier Editortypen auf, die von der IDE hosten können, und gibt Beschreibungen für jeden Editor an.

- [Projekttypen](../../extensibility/internals/project-types.md)

 Erläutert, wie Projekte steuern, wie Code kompiliert und erstellt wird, wie Editoren geöffnet werden und wie Projektelemente formatiert werden.

---
title: 'Checkliste: Erstellen neuer Projekttypen | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], creating new types
- project types, checklist for creating
ms.assetid: 29eb9c3b-1933-4741-aa85-65a33f0825ba
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5963083239571af43012e1a79576ee80846d80bd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709750"
---
# <a name="checklist-create-new-project-types"></a>Checkliste: Neue Projekttypen erstellen
Sie müssen mehrere Vorgänge ausführen, um einen neuen Projekttyp zu erstellen. Die folgende Checkliste enthält eine Anleitung zu diesen Aufgaben:

1. Entwerfen Sie die Funktionalität für Ihren neuen Projekttyp. Weitere Informationen finden Sie unter [Projekttypentwurfsentscheidungen](../../extensibility/internals/project-type-design-decisions.md).

2. Bestimmen Sie, welche Editoren für Code und andere Projektelemente verwendet werden. Sie können die Kern- oder Standard-Editoren verwenden oder projektspezifische Editoren erstellen und verwenden. Weitere Informationen finden Sie unter [Erstellen benutzerdefinierter Editoren und Designer](../../extensibility/creating-custom-editors-and-designers.md) und [Anleitung: Öffnen projektspezifischer Editoren](../../extensibility/how-to-open-project-specific-editors.md).

3. Bestimmen Sie die Teilnahmeebene, die Ihre Projektelemente in der **Klassenansicht** und im **Objektbrowser**haben. Weitere Informationen finden Sie unter [Support-Symbol-Browsing-Tools](../../extensibility/internals/supporting-symbol-browsing-tools.md).

4. Leiten Sie neue Klassen basierend auf Entwurfsentscheidungen ab, die Sie zuvor für Ihre Projekt- und Projektelemente getroffen haben.

5. Schreiben Sie den Code für die folgenden Projekttypkomponenten:

    - Projektfactory, um das Erstellen neuer Projekte und das Öffnen bestehender Projekte zu verwalten. Weitere Informationen finden Sie unter [Erstellen von Projektinstanzen mithilfe von Projektfabriken](../../extensibility/internals/creating-project-instances-by-using-project-factories.md).

    - Projekthierarchie und Befehlsbehandlung. Weitere Informationen finden Sie unter [Verwenden von HierUtil7-Projektklassen zum Implementieren eines Projekttyps (C++),](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346) [Elemente eines Projektmodells](../../extensibility/internals/elements-of-a-project-model.md), [Projektmodellkernkomponenten](../../extensibility/internals/project-model-core-components.md)und [MenuCommands im Vergleich zu OleMenuCommands](/visualstudio/extensibility/menucommands-vs-olemenucommands?view=vs-2015).

    - Projektelementverwaltung, einschließlich hinzufügen des Projekts zum Dialogfeld **Neues Projekt.** Weitere Informationen finden Sie unter Hinzufügen von [Projekt- und Projektelementvorlagen](../../extensibility/internals/adding-project-and-project-item-templates.md) und Registrieren von [Projekt- und Elementvorlagen](../../extensibility/internals/registering-project-and-item-templates.md).

    - Persistenz von Projektstatus und einzelnen Elementen. Weitere Informationen finden Sie unter [Öffnen und Speichern von Projektelementen](../../extensibility/internals/opening-and-saving-project-items.md). Persistenz von Lösungsinformationen finden Sie unter [Lösungen](../../extensibility/internals/solutions-overview.md).

    - Konfigurationsunabhängige Eigenschaften, die im Eigenschaftenfenster angezeigt werden sollen. Weitere Informationen finden Sie unter Erweitern von [Eigenschaften](../../extensibility/internals/extending-properties.md).

    - Projektkonfigurationseigenschaften, wie sie in Eigenschaftenseiten implementiert sind, um konfigurationsabhängige Eigenschaften anzuzeigen. Weitere Informationen finden Sie unter Verwalten von [Konfigurationsoptionen](../../extensibility/internals/managing-configuration-options.md).

    - Aufzählen von Ausgaben für die Bereitstellung. Weitere Informationen finden Sie unter [Projektkonfiguration für Ausgabe](../../extensibility/internals/project-configuration-for-output.md).

    - Projektstartdienste. Weitere Informationen finden Sie unter [Elemente eines Projektmodells](../../extensibility/internals/elements-of-a-project-model.md) und [Zubauder des Projektmodells](../../extensibility/internals/project-model-core-components.md).

    - Objekte oder Klassen, `IDispatch`die von abgeleitet wurden, stehen für die Automatisierung zur Verfügung.

    - XML-Befehlstabelle (*.vsct*) Dateien. Weitere Informationen finden Sie unter [Visual Studio-Befehlstabellendateien (.vsct) .](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

6. Testen, debuggen und starten Sie den Projekttyp.

7. Zeigen Sie Ihr Projekt auf der Registerkarte **Projekt** des Dialogfelds **Referenz hinzufügen** an, indem Sie den Wert für `VARIANT_TRUE` `VSHPROPID_ShowProjInSolutionPage`festlegen. Weitere Informationen finden Sie unter <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>.

8. Erstellen Sie die Datei Microsoft Installer (*.msi*) für die Installation Ihrer VSPackages. Weitere Informationen finden Sie unter Installieren von [VSPackages mit Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md), [Registrieren eines Projekttyps](../../extensibility/internals/registering-a-project-type.md)und [VSPackages](../../extensibility/internals/vspackages.md).

## <a name="see-also"></a>Weitere Informationen
- [Hierarchien in Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)
- [Wann Projekttypen erstellt werden sollen](../../extensibility/internals/when-to-create-project-types.md)
- [Erstellen von Projekttypen](../../extensibility/internals/creating-project-types.md)

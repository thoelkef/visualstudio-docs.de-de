---
title: 'Prüfliste: Erstellen neuen Projekttypen | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], creating new types
- project types, checklist for creating
ms.assetid: 29eb9c3b-1933-4741-aa85-65a33f0825ba
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 11707e62e99dd6a7920ad627d02e6e418c002e80
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31131988"
---
# <a name="checklist-creating-new-project-types"></a>Prüfliste: Erstellen neuen Projekttypen
Sie müssen mehrere Aufgaben zum Erstellen eines neuen Projekttyps. Die folgende Checkliste enthält eine Anleitung für diese Aufgaben.  
  
1.  Entwerfen Sie die Funktionalität für den neuen Projekttyp. Weitere Informationen finden Sie unter [Projekt Typ Entwurfsentscheidungen](../../extensibility/internals/project-type-design-decisions.md).  
  
2.  Bestimmen Sie, welche Editoren für Code und andere Projektelemente verwendet werden. Können Sie die Core oder standard-Editoren, oder Sie erstellen und projektspezifische Editoren verwenden können. Weitere Informationen finden Sie unter [Erstellen benutzerdefinierter Editoren und Designern](../../extensibility/creating-custom-editors-and-designers.md) und [Vorgehensweise: Öffnen projektspezifische Editoren](../../extensibility/how-to-open-project-specific-editors.md).  
  
3.  Bestimmen Sie die Art der Mitgliedschaft der Projektelemente in weist der **Klassenansicht** und **Objektkatalog**. Weitere Informationen finden Sie unter [Tools zum Durchsuchen des Symbols unterstützen](../../extensibility/internals/supporting-symbol-browsing-tools.md).  
  
4.  Leiten Sie neue Klassen basierend auf entwurfsentscheidungen, die Sie zuvor für das Projekt und Projektelemente vorgenommen.  
  
5.  Schreiben Sie den Code für die folgenden Komponenten der Projekt-Typ:  
  
    -   Projekt-Factory, um neue Projekte erstellen und Öffnen vorhandener Projekte zu verwalten. Weitere Informationen finden Sie unter [erstellen Instanzen von mithilfe von Project Projektfactorys](../../extensibility/internals/creating-project-instances-by-using-project-factories.md).  
  
    -   Projekthierarchie und befehlsverarbeitung. Weitere Informationen finden Sie unter [nicht im Build: verwenden HierUtil7 Projektklassen zum Implementieren von einem Project-Typs (C++)](http://msdn.microsoft.com/en-us/a5c16a09-94a2-46ef-87b5-35b815e2f346), [Elemente eines Modells Projekt](../../extensibility/internals/elements-of-a-project-model.md), [Projekt Modell Kernkomponenten](../../extensibility/internals/project-model-core-components.md)und [MenuCommand-und. OleMenuCommands](../../extensibility/menucommands-vs-olemenucommands.md).  
  
    -   Verwaltung, einschließlich des Hinzufügens von Ihrem Projekt, um Elemente der **neues Projekt** (Dialogfeld). Weitere Informationen finden Sie unter [Hinzufügen von Projekt- und Projektelementvorlagen](../../extensibility/internals/adding-project-and-project-item-templates.md) und [Registrieren von Projekt- und Elementvorlagen](../../extensibility/internals/registering-project-and-item-templates.md).  
  
    -   Die Dauerhaftigkeit des Projektzustands und einzelne Elemente. Weitere Informationen finden Sie unter [öffnen und Speichern von Projektelementen](../../extensibility/internals/opening-and-saving-project-items.md). Die Persistenz von Lösungsinformationen, finden Sie unter [Lösungen](../../extensibility/internals/solutions.md).  
  
    -   Unabhängige Konfigurationseigenschaften im Eigenschaftenfenster angezeigt. Weitere Informationen finden Sie unter [Erweitern von Eigenschaften](../../extensibility/internals/extending-properties.md).  
  
    -   Projizieren Sie Konfigurationseigenschaften wie Eigenschaftenseiten anzuzeigende konfigurationsabhängigen Eigenschaften implementiert. Weitere Informationen finden Sie unter [Konfigurationsoptionen verwalten](../../extensibility/internals/managing-configuration-options.md).  
  
    -   Auflisten von Ausgaben für die Bereitstellung aus. Weitere Informationen finden Sie unter [Projektkonfiguration für die Ausgabe](../../extensibility/internals/project-configuration-for-output.md).  
  
    -   Start-Services-Projekt. Weitere Informationen finden Sie unter [Elemente eines Modells Projekt](../../extensibility/internals/elements-of-a-project-model.md) und [Projekt Modell Kernkomponenten](../../extensibility/internals/project-model-core-components.md).  
  
    -   -Objekte oder abgeleitete Klassen `IDispatch`, für die Automatisierung verfügbar.  
  
    -   XML-Befehlstabelle (VSCT)-Dateien. Weitere Informationen finden Sie unter [Visual Studio-Befehlstabelle (. VSCT)-Dateien](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
6.  Testen Sie, Debuggen Sie, und starten Sie den Projekttyp.  
  
7.  Zeigen Sie das Projekt in der **Projekt** auf der Registerkarte die **Verweis hinzufügen** Dialogfeld durch Festlegen von `VARIANT_TRUE` als Wert für `VSHPROPID_ShowProjInSolutionPage`. Weitere Informationen finden Sie unter <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>.  
  
8.  Erstellen Sie die Microsoft Installer (MSI)-Datei für die Installation von Ihre VSPackages. Weitere Informationen finden Sie unter [Installieren von VSPackages mit Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md), [registrieren einen Projekttyp](../../extensibility/internals/registering-a-project-type.md), und [VSPackages](../../extensibility/internals/vspackages.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Hierarchien in Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)   
 [Wenn Projekttypen erstellen](../../extensibility/internals/when-to-create-project-types.md)   
 [Erstellen von Projekttypen](../../extensibility/internals/creating-project-types.md)
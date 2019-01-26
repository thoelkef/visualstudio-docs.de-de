---
title: 'Prüfliste: Erstellen neuer Projekttypen | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], creating new types
- project types, checklist for creating
ms.assetid: 29eb9c3b-1933-4741-aa85-65a33f0825ba
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7e0c5f170e64833a20774d21bed04c9d4728dc06
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54951949"
---
# <a name="checklist-create-new-project-types"></a>Prüfliste: Erstellen Sie neue Projekttypen
Sie müssen mehrere Aufgaben aus, um einen neuen Projekttyp erstellen abschließen. Die folgende Checkliste enthält eine Anleitung für diese Aufgaben:  
  
1.  Entwerfen Sie die Funktionalität für den neuen Projekttyp. Weitere Informationen finden Sie unter [entwurfsentscheidungen bei Projekttypen](../../extensibility/internals/project-type-design-decisions.md).  
  
2.  Bestimmen Sie, welche Editoren für Code und andere Projektelemente verwendet werden. Können Sie Kern- oder standard-Editoren, oder Sie erstellen und Verwenden von projektspezifischen Editoren. Weitere Informationen finden Sie unter [Erstellen von benutzerdefinierten Editoren und Designern](../../extensibility/creating-custom-editors-and-designers.md) und [Vorgehensweise: Öffnen von projektspezifischen Editoren](../../extensibility/how-to-open-project-specific-editors.md).  
  
3.  Bestimmt die Art der Mitgliedschaft Ihrer Projektelemente in müssen der **Klassenansicht** und **Objektkatalog**. Weitere Informationen finden Sie unter [Supporttools zum Durchsuchen von Symbolen](../../extensibility/internals/supporting-symbol-browsing-tools.md).  
  
4.  Leiten Sie neue Klassen basierend auf Entscheidungen, die Sie zuvor für das Projekt und Projektelemente vorgenommen.  
  
5.  Schreiben Sie Code für die folgenden Komponenten des Projekt-Typ:  
  
    -   Projektfactory, um das Erstellen neuer Projekte, und Öffnen von vorhandenen Projekten zu verwalten. Weitere Informationen finden Sie unter [Erstellen von Projektinstanzen mithilfe von projektfactorys](../../extensibility/internals/creating-project-instances-by-using-project-factories.md).  
  
    -   Teamprojekthierarchie und Behandlung von Befehlen. Weitere Informationen finden Sie unter [verwenden HierUtil7 Projektklassen zum Implementieren eines Projekttyps (C++)](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346), [Elemente eines Projektmodells](../../extensibility/internals/elements-of-a-project-model.md), [Hauptkomponenten eines Projekt](../../extensibility/internals/project-model-core-components.md), und [ MenuCommands im Vergleich zu OleMenuCommands](../../extensibility/menucommands-vs-olemenucommands.md).  
  
    -   Verwaltung, einschließlich des Hinzufügens von das Projekt für die Elemente der **neues Projekt** Dialogfeld. Weitere Informationen finden Sie unter [Hinzufügen von Projekt- und Projektelementvorlagen](../../extensibility/internals/adding-project-and-project-item-templates.md) und [Registrieren von Projekt- und Elementvorlagen](../../extensibility/internals/registering-project-and-item-templates.md).  
  
    -   Die Dauerhaftigkeit des Projektzustands und einzelne Elemente. Weitere Informationen finden Sie unter [öffnen und speichern Sie Projektelemente](../../extensibility/internals/opening-and-saving-project-items.md). Persistenz der Informationen zur Lösung finden Sie unter [Lösungen](../../extensibility/internals/solutions.md).  
  
    -   Konfigurationsunabhängigen Eigenschaften im Eigenschaftenfenster angezeigt. Weitere Informationen finden Sie unter [Eigenschaften erweitern](../../extensibility/internals/extending-properties.md).  
  
    -   Projizieren Sie Konfigurationseigenschaften an, wie in den Eigenschaftenseiten, um die konfigurationsabhängigen Eigenschaften implementiert. Weitere Informationen finden Sie unter [verwalten Konfigurationsoptionen](../../extensibility/internals/managing-configuration-options.md).  
  
    -   Auflisten von Ausgaben für die Bereitstellung aus. Weitere Informationen finden Sie unter [Projektkonfiguration für die Ausgabe](../../extensibility/internals/project-configuration-for-output.md).  
  
    -   Projekt Startdienste. Weitere Informationen finden Sie unter [Elemente eines Projektmodells](../../extensibility/internals/elements-of-a-project-model.md) und [Hauptkomponenten eines Projekt](../../extensibility/internals/project-model-core-components.md).  
  
    -   Objekte oder von abgeleiteten Klassen `IDispatch`, für die Automatisierung verfügbar.  
  
    -   XML-Befehlstabelle (*VSCT*) Dateien. Weitere Informationen finden Sie unter [Visual Studio-Befehlstabellen (VSCT) Befehlsdateien](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
6.  Testen Sie, Debuggen Sie und starten Sie die Art Ihres Projekts.  
  
7.  Zeigen Sie Ihr Projekt in der **Projekt** Registerkarte die **Verweis hinzufügen** Dialogfeld durch Festlegen von `VARIANT_TRUE` als Wert für `VSHPROPID_ShowProjInSolutionPage`. Weitere Informationen finden Sie unter <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>.  
  
8.  Erstellen Sie den Microsoft Installer (*MSI*)-Datei für Ihre VSPackages zu installieren. Weitere Informationen finden Sie unter [Installieren von VSPackages mit Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md), [registrieren ein Projekttyps](../../extensibility/internals/registering-a-project-type.md), und [VSPackages](../../extensibility/internals/vspackages.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Hierarchien in Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)   
 [Gründe für das Erstellen von Projekttypen](../../extensibility/internals/when-to-create-project-types.md)   
 [Erstellen von Projekttypen](../../extensibility/internals/creating-project-types.md)
---
title: 'Prüfliste: Erstellen neuer Projekttypen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], creating new types
- project types, checklist for creating
ms.assetid: 29eb9c3b-1933-4741-aa85-65a33f0825ba
caps.latest.revision: 24
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5f3a6a091e5574721b93cbff23f873fe1a845ef6
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "59001737"
---
# <a name="checklist-creating-new-project-types"></a>Prüfliste: Erstellen neuer Projekttypen
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Sie müssen mehrere Aufgaben aus, um einen neuen Projekttyp erstellen abschließen. Die folgende Checkliste enthält eine Anleitung für diese Aufgaben.  
  
1.  Entwerfen Sie die Funktionalität für den neuen Projekttyp. Weitere Informationen finden Sie unter [Entwurfsentscheidungen bei Projekttypen](../../extensibility/internals/project-type-design-decisions.md).  
  
2.  Bestimmen Sie, welche Editoren für Code und andere Projektelemente verwendet werden. Können Sie Kern- oder standard-Editoren, oder Sie erstellen und Verwenden von projektspezifischen Editoren. Weitere Informationen finden Sie unter [Erstellen von benutzerdefinierten Editoren und Designern](../../extensibility/creating-custom-editors-and-designers.md) und [Vorgehensweise: Öffnen von projektspezifischen Editoren](../../extensibility/how-to-open-project-specific-editors.md).  
  
3.  Bestimmt die Art der Mitgliedschaft Ihrer Projektelemente in müssen der **Klassenansicht** und **Objektkatalog**. Weitere Informationen finden Sie unter [Tools zum Durchsuchen von Symbolen unterstützen](../../extensibility/internals/supporting-symbol-browsing-tools.md).  
  
4.  Leiten Sie neue Klassen basierend auf Entscheidungen, die Sie zuvor für das Projekt und Projektelemente vorgenommen.  
  
5.  Schreiben Sie Code für die folgenden Komponenten des Projekt-Typ:  
  
    -   Projektfactory, um das Erstellen neuer Projekte, und Öffnen von vorhandenen Projekten zu verwalten. Weitere Informationen finden Sie unter [erstellen Projekt Instanzen von mithilfe von Projektfactorys](../../extensibility/internals/creating-project-instances-by-using-project-factories.md).  
  
    -   Teamprojekthierarchie und Behandlung von Befehlen. Weitere Informationen finden Sie unter [nicht im Build: HierUtil7-Projektklassen zum Implementieren eines Projekttyps (C++) mit](http://msdn.microsoft.com/a5c16a09-94a2-46ef-87b5-35b815e2f346), [Elemente eines Projektmodells](../../extensibility/internals/elements-of-a-project-model.md), [Hauptkomponenten eines Projekt](../../extensibility/internals/project-model-core-components.md) und [MenuCommands im Vergleich. OleMenuCommands](../../misc/menucommands-vs-olemenucommands.md).  
  
    -   Verwaltung, einschließlich des Hinzufügens von das Projekt für die Elemente der **neues Projekt** Dialogfeld. Weitere Informationen finden Sie unter [Hinzufügen von Projekt- und Projektelementvorlagen](../../extensibility/internals/adding-project-and-project-item-templates.md) und [Registrieren von Projekt- und Elementvorlagen](../../extensibility/internals/registering-project-and-item-templates.md).  
  
    -   Die Dauerhaftigkeit des Projektzustands und einzelne Elemente. Weitere Informationen finden Sie unter [öffnen und Speichern von Projektelementen](../../extensibility/internals/opening-and-saving-project-items.md). Persistenz der Informationen zur Lösung finden Sie unter [Lösungen](../../extensibility/internals/solutions-overview.md).  
  
    -   Unabhängige Eigenschaften im Eigenschaftenfenster angezeigt. Weitere Informationen finden Sie unter [Erweitern von Eigenschaften](../../extensibility/internals/extending-properties.md).  
  
    -   Projizieren Sie Konfigurationseigenschaften an, wie in den Eigenschaftenseiten, um die konfigurationsabhängigen Eigenschaften implementiert. Weitere Informationen finden Sie unter [Konfigurationsoptionen verwalten](../../extensibility/internals/managing-configuration-options.md).  
  
    -   Auflisten von Ausgaben für die Bereitstellung aus. Weitere Informationen finden Sie unter [Projektkonfiguration für die Ausgabe](../../extensibility/internals/project-configuration-for-output.md).  
  
    -   Projekt Startdienste. Weitere Informationen finden Sie unter [Elemente eines Projektmodells](../../extensibility/internals/elements-of-a-project-model.md) und [Hauptkomponenten eines Projektmodells](../../extensibility/internals/project-model-core-components.md).  
  
    -   Objekte oder von abgeleiteten Klassen `IDispatch`, für die Automatisierung verfügbar.  
  
    -   XML-Command Table (.vsct)-Dateien. Weitere Informationen finden Sie unter [Visual Studio Command Table (.Vsct) Files](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
6.  Testen Sie, Debuggen Sie und starten Sie die Art Ihres Projekts.  
  
7.  Zeigen Sie Ihr Projekt in der **Projekt** Registerkarte die **Verweis hinzufügen** Dialogfeld durch Festlegen von `VARIANT_TRUE` als Wert für `VSHPROPID_ShowProjInSolutionPage`. Weitere Informationen finden Sie unter <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>.  
  
8.  Erstellen Sie die Microsoft Installer (MSI)-Datei für die Installation von Ihre VSPackages. Weitere Informationen finden Sie unter [Installieren von VSPackages mit Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md), [Registrieren eines Projekttyps](../../extensibility/internals/registering-a-project-type.md), und [VSPackages](../../extensibility/internals/vspackages.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Hierarchien in Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)   
 [Gründe für das Erstellen von Projekttypen](../../extensibility/internals/when-to-create-project-types.md)   
 [Erstellen von Projekttypen](../../extensibility/internals/creating-project-types.md)

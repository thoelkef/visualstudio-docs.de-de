---
title: "Pr&#252;fliste: Erstellen von neuen Typen | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Projekte [Visual Studio SDK], Erstellen neuer Typen"
  - "Prüfliste für das Erstellen von Projekttypen"
ms.assetid: 29eb9c3b-1933-4741-aa85-65a33f0825ba
caps.latest.revision: 23
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 23
---
# Pr&#252;fliste: Erstellen von neuen Typen
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Sie müssen mehrere Aufgaben aus, um einen neuen Projekttyp erstellen abschließen. Die folgende Checkliste enthält eine Anleitung für diese Aufgaben.  
  
1.  Entwerfen Sie die Funktionalität für den neuen Projekttyp. Weitere Informationen finden Sie unter [Projekt Typ Designentscheidungen](../../extensibility/internals/project-type-design-decisions.md).  
  
2.  Bestimmen Sie, welche Editoren für Code und andere Projektelemente verwendet werden. Können Sie die zentrale oder standard\-Editoren, oder Sie erstellen und Verwenden von projektspezifische Editoren. Weitere Informationen finden Sie unter [Erstellen von benutzerdefinierten Editoren und Designern](../../extensibility/creating-custom-editors-and-designers.md) und [Gewusst wie: Öffnen von Editoren projektspezifische](../../extensibility/how-to-open-project-specific-editors.md).  
  
3.  Bestimmen Sie die Art der Mitgliedschaft der Projektelemente in müssen der **Klassenansicht** und **Objektkatalog**. Weitere Informationen finden Sie unter [Unterstützung von Tools zum Durchsuchen des Symbols](../../extensibility/internals/supporting-symbol-browsing-tools.md).  
  
4.  Leiten Sie neue Klassen basierend auf entwurfsentscheidungen, die Sie zuvor für das Projekt und Projektelemente vorgenommen.  
  
5.  Schreiben Sie Code für die folgenden Komponenten der Projekt\-Typ:  
  
    -   Projekt\-Factory, um neue Projekte erstellen und Öffnen vorhandener Projekte zu verwalten. Weitere Informationen finden Sie unter [Erstellen von Instanzen von Project mithilfe von Project\-Factorys](../../extensibility/internals/creating-project-instances-by-using-project-factories.md).  
  
    -   Teamprojekthierarchie und Befehlsbehandlung. Weitere Informationen finden Sie unter [nicht im Build: mithilfe von HierUtil7 Projektklassen implementieren eine Projekt\-Typ \(C\+\+\)](http://msdn.microsoft.com/de-de/a5c16a09-94a2-46ef-87b5-35b815e2f346), [Elemente eines Projektmodells](../../extensibility/internals/elements-of-a-project-model.md), [Projekt\-Modell\-Kernkomponenten](../../extensibility/internals/project-model-core-components.md) und [MenuCommand\- und OleMenuCommand\-Objekte](../../misc/menucommands-vs-olemenucommands.md).  
  
    -   Verwaltung, einschließlich hinzufügen das Projekt für die Elemente der **Neues Projekt** \(Dialogfeld\). Weitere Informationen finden Sie unter [Hinzufügen von Projekt\- und Projektelementvorlagen](../../extensibility/internals/adding-project-and-project-item-templates.md) und [Registrieren von Projekt\- und Elementvorlagen](../../extensibility/internals/registering-project-and-item-templates.md).  
  
    -   Die Dauerhaftigkeit des Projektstatus und einzelne Elemente. Weitere Informationen finden Sie unter [Öffnen und Speichern von Projektelementen](../../extensibility/internals/opening-and-saving-project-items.md). Dauerhaftigkeit von Informationen zur Lösung finden Sie unter [Projektmappen](../../extensibility/internals/solutions.md).  
  
    -   Unabhängige Konfigurationseigenschaften im Eigenschaftenfenster angezeigt. Weitere Informationen finden Sie unter [Erweitern von Eigenschaften](../../extensibility/internals/extending-properties.md).  
  
    -   Projekteigenschaften Sie Konfiguration gemäß der Implementierung in den Eigenschaftenseiten, um die konfigurationsabhängigen Eigenschaften anzuzeigen. Weitere Informationen finden Sie unter [Verwalten von Konfigurationsoptionen](../../extensibility/internals/managing-configuration-options.md).  
  
    -   Auflisten von Ausgaben für die Bereitstellung. Weitere Informationen finden Sie unter [Konfiguration für die Ausgabe des Projekts](../../extensibility/internals/project-configuration-for-output.md).  
  
    -   Start\-Services\-Projekt. Weitere Informationen finden Sie unter [Elemente eines Projektmodells](../../extensibility/internals/elements-of-a-project-model.md) und [Projekt\-Modell\-Kernkomponenten](../../extensibility/internals/project-model-core-components.md).  
  
    -   Objekte oder abgeleitete Klassen `IDispatch`, für die Automatisierung verfügbar.  
  
    -   XML\-Befehlstabelle \(VSCT\)\-Dateien. Weitere Informationen finden Sie unter [Visual Studio\-Befehl\-Tabelle \(. VSCT\) Dateien](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
6.  Testen Sie, Debuggen Sie und starten Sie den Projekttyp.  
  
7.  Anzeigen ein Projekts in der **Projekt** auf der Registerkarte der **Verweis hinzufügen** das Dialogfeld festlegen `VARIANT_TRUE` als Wert für `VSHPROPID_ShowProjInSolutionPage`. Weitere Informationen finden Sie unter <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>.  
  
8.  Erstellen Sie die Microsoft Installer \(MSI\)\-Datei für die Installation der VSPackages. Weitere Informationen finden Sie unter [Installieren von VSPackages mit Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md), [Registrieren einen Projekttyp](../../extensibility/internals/registering-a-project-type.md) und [VSPackages](../../extensibility/internals/vspackages.md).  
  
## Siehe auch  
 [Hierarchien in Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)   
 [Erstellen von Projekttypen](../../extensibility/internals/when-to-create-project-types.md)   
 [Erstellen von Projekttypen](../../extensibility/internals/creating-project-types.md)
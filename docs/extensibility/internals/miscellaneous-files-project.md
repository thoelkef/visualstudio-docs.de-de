---
title: "Projekt verschiedene Dateien | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Dateien, Hinzufügen von vorhandenen Dateien zu Projektmappen"
  - "Projekt für verschiedene Dateien"
  - "Ordner "Projektmappenelemente""
  - "Dateien mit Projekt verschiedene Dateien öffnen"
ms.assetid: 93a278a8-d4f4-400b-8945-4f1b0a2b5bac
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# Projekt verschiedene Dateien
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Wenn ein Benutzer Projektelemente öffnet, weist die IDE dem Projekt Verschiedene Dateien alle Elemente, die nicht Mitglied aller Projekte in einer Projektmappe befinden.  
  
 Projekte geben eine wesentliche Rolle noch einmal, wenn sie welchem Editor verwendet wird, wenn ein Benutzer ein Projektelement öffnet.  Ein Projekt kann entworfen werden, um bestimmte Dateien zu öffnen, indem Sie einen projektspezifischen Editor oder einen Standardwert des Editors verwendet.  
  
 Ein projektspezifischer Editor erfordert in der Regel, dass der Benutzer speziellen Kenntnisse besitzen oder bestimmte Schnittstellen aus dem Projekt.  Weitere Informationen finden Sie unter [Gewusst wie: Öffnen von Editoren projektspezifische](../../extensibility/how-to-open-project-specific-editors.md).  
  
 Ein standardmäßigen Editor kann jede Datei eine bestimmte Erweiterung in jedem Projekt öffnen.  Der Benutzer kann mehrere Standardwert editoren, wie der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Text\-Editor, dann Projekte weiterhin Zeichen öffentliches sie jedoch anpassen.  Standardwert editoren werden erstellt, indem die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>\-Methode.  
  
 Wenn kein Projekt in der Projektmappe reagiert, dass ein Projektelement öffnen kann, stellt die IDE ein bestimmtes Projekt, in dem das Projekt Verschiedene Dateien aufgerufen wird, das beliebige Datei geöffnet.  
  
 In diesem speziellen Projekt stellt für Öffnen einer Datei außerhalb des Kontexts eines Projekts bereit.  Während der Verarbeitung der <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A>\-Methode, reagiert das Projekt Verschiedene Dateien immer mit einer sehr Basispriorität.  Daher führt das Projekt Verschiedene Dateien immer auf jedes Projekt mit höherer Priorität, der geöffnete Dateien kann.  
  
 Das Projekt Verschiedene Dateien nicht erforderlich, den Benutzer mit dem **Neues Projekt** Dialogfeld explizit zu erstellen.  Außerdem wird das Projekt Verschiedene Dateien nicht permanent verwaltet eine Liste von Projektmitgliedern.  Sie verwendet eine optionale Funktion, um eine Liste der zuletzt verwendeten Dateien für jeden Benutzer aufzuzeichnen.  
  
## Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument>   
 <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>   
 [Gewusst wie: Öffnen von Editoren projektspezifische](../../extensibility/how-to-open-project-specific-editors.md)   
 [Gewusst wie: Öffnen Sie die Standard\-Editoren](../../extensibility/how-to-open-standard-editors.md)   
 [Hinzufügen von Projekt\- und Projektelementvorlagen](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 [Hinzufügen von Projekt\- und Projektelementvorlagen](../../extensibility/internals/adding-project-and-project-item-templates.md)
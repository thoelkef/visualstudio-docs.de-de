---
title: "Dienste, die in Beispielen verwendet werden | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Dienste, die in Beispielen verwendet werden"
  - "Beispiele, Dienste"
ms.assetid: 04864feb-9b8b-45c4-8233-fc2ed9273987
caps.latest.revision: 9
caps.handback.revision: 9
manager: "douge"
---
# Dienste, die in Beispielen verwendet werden
Die Beispiele in [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] eingeschlossen werden, verwenden zahlreiche Dienste aus.  In der folgenden Liste werden einige häufig verwendete Dienste und die Beispiele, die sie verwenden.  
  
> [!NOTE]
>  Wenn der Verweis nicht unterstützt und Beispiele zur Verfügung stehen, werden nur die Referenzmuster aufgeführt ist.  
  
|Dienst|Beispiel|  
|------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SLocalRegistry>|BscEdit, ProjectSubtype|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog>|[Gewusst wie: Verwenden Sie das Aktivitätsprotokoll](../extensibility/how-to-use-the-activity-log.md)|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsAddProjectItemDlg>|BscPrj, FigPkg|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsCreateAggregateProject>|BscPrj|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChange>|Veraltet.  Verwenden Sie stattdessen <xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx>.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx>|BscEdit, FigPkg|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsMonitorUserContext>|Reference.HelpIntegrations\-Beispiel.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>|SingleViewEditor\-Beispiel.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterEditors>|SingleViewEditor\-Beispiel.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterProjectTypes>|BscPrj, FigPkg|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsResourceManager>|Reference.Package, Reference.ToolWindow und viele weitere Beispiele|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>|SingleViewEditor\-Beispiel.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>|BscPrj, FigPkg|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>|Reference.Package, Reference.ToolWindow und viele weitere Beispiele|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellDebugger>|BscEdt, BscPrj, FigPkg|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>|BscPrj, FigPkg|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|BscPrj, FigPkg|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>|BscPrj, FigPkg|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx>|SingleViewEditor, BscPrj, FigPkg|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|Reference.ToolWindow, BscEdit und viele weitere Beispiele|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument>|BscEdit, FigPkg|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsWindowFrame>|Reference.ToolWindow|  
  
## Siehe auch  
 [Liste der verfügbaren Dienste](../extensibility/internals/list-of-available-services.md)   
 [Service – Grundlagen](../extensibility/internals/service-essentials.md)
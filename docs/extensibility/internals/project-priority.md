---
title: "Projektpriorit&#228;t | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Projekte [Visual Studio SDK] Elemente öffnen"
ms.assetid: 9f707592-2fb6-4f75-9269-f6d4700a998e
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# Projektpriorit&#228;t
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ein Projektelement ist normalerweise nur ein Mitglied von einem Projekt in der Projektmappe.  Daher kann die IDE auf einfache Weise ermitteln, welches Projekt zu öffnen, das Element verwendet wird.  Wenn jedoch ein Element ein Member von mehr als einem Projekt ist, verwendet die IDE ein Schema Priorität, das beste Projekt zum Öffnen des Elements zu bestimmen.  
  
 Die folgende Liste zeigt prioritäts Schema für das Projekt angezeigt:  
  
-   Die IDE ruft die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2.IsDocumentInProject%2A>\-Methode für jedes Projekt in der Projektmappe zu bestimmen, ob das Dokument an ein Member dieses Projekts ist.  
  
-   Wenn das Dokument ein Member des Projekts befindet, reagiert das Projekt mit einer Priorität, die das Projekt entsprechend ihrer Behandlung dieses Dokument zuordnet.  reagiert beispielsweise ein Sprachprojekt mit einer hohen Stellenwert für die Sprachen quelldateien reagiert jedoch mit einer niedrigeren Priorität für einen nicht erkannte Dateityp, der nicht als Teil des Buildprozesses verwendet wird.  
  
-   Projekte, die die benutzerdefinierten Editoren projektspezifischen, oder der Designer für ein Dokument ebenfalls bereitstellen, erhalten eine hohe Priorität.  
  
-   Die <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>\-Enumeration stellt die prioritäts Dokumente.  
  
-   Das Projekt, das die höchste Priorität angegeben wird, ist der Kontext angegeben, wenn das Dokument geöffnet wird.  Wenn zwei Projekte gleiche Priorität von Werten zurückgeben, ist das aktive Projekt bevorzugt.  Wenn kein Projekt in der Projektmappe reagiert, dass das Dokument öffnen kann, fügt die IDE das Dokument in das Projekt Verschiedene Dateien.  Weitere Informationen finden Sie unter [Projekt verschiedene Dateien](../../extensibility/internals/miscellaneous-files-project.md).  
  
## Siehe auch  
 [Projekt verschiedene Dateien](../../extensibility/internals/miscellaneous-files-project.md)   
 [Gewusst wie: Öffnen von Editoren für geöffnete Dokumente](../../extensibility/how-to-open-editors-for-open-documents.md)   
 [Hinzufügen von Projekt\- und Projektelementvorlagen](../../extensibility/internals/adding-project-and-project-item-templates.md)
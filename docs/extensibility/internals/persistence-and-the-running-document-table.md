---
title: "Persistenz und der Document-Tabelle ausgef&#252;hrt wird | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Persistenz, verwalten"
  - "IVsPersistHierarchyItem-Schnittstelle implementieren"
  - "Persistenz-Architektur"
  - "ausgeführten Dokumenttabelle (RDT), Architektur"
ms.assetid: 27117eae-6c58-4189-a61a-1397a43b5ecf
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# Persistenz und der Document-Tabelle ausgef&#252;hrt wird
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

In der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] \-IDE\-Projekte sind vollständig zuständig für die Verwaltung von der Dauerhaftigkeit von Projektelementen, die sie mit dem Dienst zu erreichen, <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>. Dokumente sind die grundlegende Einheit der Persistenz in Visual Studio\-Umgebung. Projekte koordinieren öffnen, speichern und Umbenennen von Dokumenten mit der ausgeführten Dokumenttabelle \(RDT\), eine Ressource, die den Status aller geöffneten Dokumente nachverfolgt.  
  
## Verwalten von Persistenz  
 Projekte Steuern der Umgebung Persistenzdienst durch Implementieren der <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> Schnittstelle. Während die Umgebung nie direkt einem Dokument selbst beibehalten anfordert, fordert er die besitzende Projekt \(oder Hierarchie\) zum Speichern des Dokuments. Dadurch kann für das Projekt, um die Project\-Element\-Daten in lokalen Dateien, remote\-Dateien, eine Datenbank, ein Repository oder ein anderes Medium zu speichern.  
  
 Die globale Umgebung verwaltet die RDT. Die Umgebung verwaltet Einträge für alle geöffneten Fenster, und Dokumente in der RDT, Sie werden Benachrichtigungen spezielle, z. B. wenn eine Projektmappe geschlossen wird. Darüber hinaus die RDT ermöglicht es der Umgebung zum Nachverfolgen von der entsprechenden Knoten in **Projektmappen\-Explorer**. Die RDT verwaltet einen Datensatz pro öffnen, dauerhafte Objekt, einschließlich der Projektdateien und Projektelement Dokumente.  
  
## Siehe auch  
 [Dokumenttabelle der ausgeführten](../../extensibility/internals/running-document-table.md)   
 [Auswahl und Währung, in der IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)
---
title: "Projekt-Persistenz | Microsoft Docs"
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
  - "Persistenz, Projekte"
  - "Projekte [Visual Studio SDK], Persistenz"
ms.assetid: 42907bcf-4e27-46bd-a8cb-01c2ccd2bde5
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# Projekt-Persistenz
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Persistenz ist eine wichtige entwurfs überlegung für das Projekt.  Die meisten Projekten können Sie Projektelemente, die Dateien darstellen. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] auch Unterstützungsprojekt, deren Daten nicht\-FILE\-basiert ist.  müssen die Dateien, die im Besitz des Projekts sind und die Projektdatei beibehalten werden.  Die IDE fügt das Projekt, bzw. eines Projektelements zu speichern.  
  
 Vorlagen für Projekte werden zur Projektfactory übergeben.  Die Vorlagen sollten die Initialisierung aller Projektelemente gemäß den Anforderungen des speziellen Projekttyps unterstützen.  Diese Vorlagen können später als Projektdateien gespeichert sind und von der IDE durch die Projektmappe verwaltet werden.  Weitere Informationen finden Sie unter [Erstellen von Instanzen von Project mithilfe von Project\-Factorys](../../extensibility/internals/creating-project-instances-by-using-project-factories.md) und [Projektmappen](../../extensibility/internals/solutions.md).  
  
 Projektelemente können oder dateibasierten nicht\-FILE\-basiert sein:  
  
-   Grundgrössen können lokal oder Remot sein.  In Webprojekten in C\# Verbindungen bestehen, z. B. auf Dateien auf einem Remotesystem weiter lokal, während die Dateien selbst auf dem Remotesystem beibehalten werden.  
  
-   Nicht\-FILE\-basierte Elemente können Elemente einer Datenbank oder einem Repository gespeichert werden.  
  
## Commit\-Modelle  
 Nachdem Sie sich entschieden haben, wo die Projektelemente befinden, müssen Sie das entsprechende Modell Commit auswählen.  Beispielsweise kann in einem dateibasierten Modells mit lokalen Dateien, kann jedes Projekt autonom gespeichert werden.  In einem Repository Modells können Sie einige Elemente in einer Transaktion speichern.  Weitere Informationen finden Sie unter [Projekt Typ Designentscheidungen](../../extensibility/internals/project-type-design-decisions.md).  
  
 Um Dateinamenerweiterungen zu bestimmen, implementieren die Projekte <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>\-Schnittstelle, die Informationen enthält den Clients eines Objekts aktiviert, um das Dialogfeld **Speichern unter** zu implementieren Feld\-dass ist, um die **Dateityp** Dropdownliste zu füllen und die ursprüngliche Dateinamenerweiterung zu erreichen.  
  
 Die IDE ruft die `IPersistFileFormat`\-Schnittstelle für das Projekt festlegen, wird das Projekt deren Projektelemente je nach Bedarf beibehalten werden sollen.  Deshalb besitzt das Objekt alle Aspekte der Datei und im angegebenen Format.  Dies umfasst auch den Namen des Formats des Objekts ein.  
  
 Wenn keine Elemente sind Dateien, ist `IPersistFileFormat` , z. B. weiterhin nicht\-FILE\-basierte Elemente beibehalten werden.  Projektdateien, wie .vbp\-Dateien für [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] Projekte oder .vcproj\-Dateien für [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] Projekte, müssen ebenfalls beibehalten werden.  
  
 Für Speicheraktionen überprüft die IDE die Dokumente \(Drehtransformator\) und die Hierarchie werden die Befehle zu <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2>\-Schnittstellen.  Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.IsItemDirty%2A>\-Methode implementiert wird, um zu bestimmen, ob das Element geändert wurde.  Wenn das Element verfügt, wird die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.SaveItem%2A>\-Methode implementiert, um das geänderte Element zu speichern.  
  
 Die Methoden der Schnittstelle `IVsPersistHierarchyItem2` verwendet werden, um zu bestimmen, ob ein Element neu geladen werden kann, und wenn das Element sein kann, um ihn erneut zu laden.  Darüber hinaus kann die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IgnoreItemFileChanges%2A>\-Methode implementiert werden, um geänderte Elemente zu veranlassen, verworfen werden, ohne gespeichert werden soll.  
  
## Siehe auch  
 [Prüfliste: Erstellen von neuen Typen](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Erstellen von Instanzen von Project mithilfe von Project\-Factorys](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)
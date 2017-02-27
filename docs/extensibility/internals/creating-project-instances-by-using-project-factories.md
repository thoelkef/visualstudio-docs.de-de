---
title: "Erstellen von Instanzen von Project mithilfe von Project-Factorys | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Projekt-Factorys"
  - "Projekte [Visual Studio SDK], Projekt-Factorys"
ms.assetid: 94c90012-8669-459c-af8e-307ac242c8c4
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# Erstellen von Instanzen von Project mithilfe von Project-Factorys
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Projekttypen in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]*factory Projekt* verwenden, um Instanzen von Projektobjekten zu erstellen.  Eine Projekt factory ist mit einer standardmäßigen klassenfactory für cocreatable einen sehr ähnlich.  Projektobjekte sind jedoch nicht cocreatable: Sie können nur erstellt werden, indem eine Projekt factory verwenden.  
  
 Das [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE zeigt die Projekt factory in einem VSPackage implementieren, wenn ein Benutzer ein vorhandenes Projekt lädt oder ein neues Projekt in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]erstellt.  Das neue Projektobjekt stellt die IDE mit genügend Informationen, um Projektmappen\-Explorer zu füllen.  Das neue Projektobjekt stellt auch die erforderlichen Schnittstellen zur Unterstützung aller relevanten Benutzeroberflächenaktionen bereit, die von der IDE initiiert werden.  
  
 Sie können die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>\-Schnittstelle in einer Klasse im Projekt implementieren.  In der Regel befindet sich diese in einem eigenen Moduls.  
  
 Ein Beispiel für eine Implementierung der `IVsProjectFactory`\-Schnittstelle finden Sie in PrjFac.cpp B. [Basic Project](http://msdn.microsoft.com/de-de/385fd2a3-d9f1-4808-87c2-a3f05a91fc36) im Verzeichnis enthalten ist.  
  
 Projekte, die von einem Besitzer aggregiert werden, unterstützen, müssen eine Besitzers Schlüssels in der Projektdatei beibehalten werden.  Wenn die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>\-Methode die einem Projekt mit einer Besitzers Taste aufgerufen wird, konvertiert das Besitze Projekt, dessen Besitzer einer Taste factory Projekt GUID ruft dann die `CreateProject` factory Projekt für diese Methode aufrufen, um die tatsächliche Build durchzuführen.  
  
## Ein Besitz Projekt erstellen  
 Ein Besitzer erstellt ein Besitz Projekt in zwei Phasen:  
  
1.  Durch Aufrufen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.PreCreateForOwner%2A>\-Methode.  Dies gibt dem Besitzen Projekt eine Möglichkeit, ein aggregiertes Projektobjekt auf Grundlage der Eingaben zu erstellen, die `IUnknown`steuert.  Das Besitze Projekt führt innere `IUnknown` und das zusammengesetzte Projekt Besitzers zum Objekt zurück.  Dies gibt dem Besitzen Projekt eine Möglichkeit zur inneren `IUnknown`zu speichern.  
  
2.  Durch Aufrufen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A>\-Methode.  Das Besitze Projekt führt die gesamte Instanziierung, wenn diese Methode aufgerufen wird, anstatt `IVsProjectFactory::CreateProject` aufrufen, wie das Argument für Projekte, die nicht im Besitz sind.  Die Eingabe `VSOWNEDPROJECTOBJECT`\-Enumeration ist i. d. R. das aggregierte Besitze Projekt.  Das Besitze Projekt kann diese Variable verwenden, um zu ermitteln, ob das Projektobjekt bereits erstellt wurde \(Cookie entspricht nicht null\) oder gleichgestellte Cookie erstellt werden muss \(null\).  
  
 Projekttypen werden durch eine eindeutige Projekt\-GUID identifiziert, die auf die CLSID eines cocreatable COM\-Objekts ähnelt.  In der Regel ein Projekt mit Handles factorys, die Instanzen eines bestimmten Projekttyps erstellen, obwohl es möglich ist, ein Projekt factory behandelt haben mehrere Projekttyp\-GUID.  
  
 Projekttypen werden mit einer bestimmten Dateinamenerweiterung zugeordnet.  Wenn ein Benutzer versucht, eine vorhandene Projektdatei öffnen oder ein neues Projekt erstellen, indem Sie eine Vorlage verwendet, klont die IDE die Erweiterung der Datei, um die entsprechende Projekt\-GUID zu bestimmen.  
  
 Sobald die IDE bestimmt, ob überhaupt ein neues Projekt erstellen oder ein vorhandenes Projekt eines bestimmten Typs geöffnet werden muss, verwendet die IDE die Informationen in der Systemregistrierung unter \[HKEY\_LOCAL\_MACHINE \\ Software \\ Microsoft \\ VisualStudio \\ 8.0 \\ Projects\] nach denen gesucht werden soll, die einem VSPackage die erforderliche Projekt factory implementiert.  Die IDE lädt diese VSPackage.  In der <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>\-Methode muss die VSPackages factory Projekt mit der IDE registriert, indem die <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes.RegisterProjectType%2A>\-Methode aufgerufen wird.  
  
 Die primäre Methode der `IVsProjectFactory`\-Schnittstelle ist <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> , die zwei Szenarien behandeln soll: ein vorhandenes Projekt und zum Erstellen eines neuen Projekts öffnen.  Die meisten Projekten speichern ihre Projekt Zustand in einer Projektdatei.  In der Regel werden neue Projekte erstellt, indem eine Kopie der Vorlagendatei erstellt, die auf die `CreateProject`\-Methode übergeben wird und die Kopie dann öffnet.  Vorhandene Projekte direkt instanziiert werden, indem Sie die Projektdatei öffnet, die `CreateProject`\-Methode übergeben wird.  Die `CreateProject`\-Methode kann bei Bedarf zusätzliche Benutzeroberflächenfunktionen für den Benutzer angezeigt werden.  
  
 Ein Projekt kann auch keine Dateien verwenden und seinen Zustand Projekt in einem Speichermechanismus Gegensatz zum Dateisystem, z. B. eine Datenbank oder einen Webserver stattdessen auf Speichern.  In diesem Fall lautet der Dateiname `CreateProject`\-Parameter, der an die Methode übergeben wird, nicht tatsächlich ein Dateisystempfad STRING\-ein eindeutige, sondern identifiziert die URL\-zu Projektdaten.  Sie müssen keine die Vorlagendateien zu kopieren, die `CreateProject` übergeben werden, um die richtige Konstruktion sequence Ausführung auszulösen.  
  
## Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes>   
 [Prüfliste: Erstellen von neuen Typen](../../extensibility/internals/checklist-creating-new-project-types.md)
---
title: Erstellen von Instanzen von Project mithilfe von Projektfactorys | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project factories
- projects [Visual Studio SDK], project factories
ms.assetid: 94c90012-8669-459c-af8e-307ac242c8c4
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 8a331c131eaf48eb7be8bc3709599412aa01b1ca
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="creating-project-instances-by-using-project-factories"></a>Erstellen von Instanzen von Project mithilfe von Projektfactorys
Projekttypen in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] verwenden eine *Projekt Factory* zum Erstellen von Instanzen von Projektobjekten. Eine Factory Projekt ähnelt einer standard-Klassenfactory für cocreatable COM-Objekte. Projektobjekte sind jedoch nicht cocreatable: sie können nur mit einem Project-Factory erstellt werden.  
  
 Die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE Ruft die Projekt-Factory, die in Ihrem VSPackage implementiert werden, wenn ein Benutzer ein vorhandenes Projekt geladen oder ein neues Projekt in erstellt [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Das neue Objekt stellt die IDE genügend Informationen zum Auffüllen der Projektmappen-Explorer bereit. Das neue Objekt bietet zudem die erforderlichen Schnittstellen unterstützen alle relevanten UI-Aktionen, die von der IDE initiiert.  
  
 Sie können implementieren die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> Schnittstelle in einer Klasse in Ihrem Projekt. In der Regel befindet sich in einem eigenen Modul.  
  
 Ein Beispiel für eine Implementierung der `IVsProjectFactory` Benutzeroberfläche, siehe PrjFac.cpp, die in enthalten ist das [Basic-Projekts](http://msdn.microsoft.com/en-us/385fd2a3-d9f1-4808-87c2-a3f05a91fc36) Beispielverzeichnis.  
  
 Projekte, die durch einen Besitzer aggregiert unterstützen müssen einen Besitzer Schlüssel in ihrer Projektdatei beibehalten. Wenn die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> Methode für ein Projekt mit einem Schlüssel Besitzer aufgerufen wird, das zugehörige Projekt konvertiert seinen Besitzer Schlüssel in einem Projekt Factory GUID dann Ruft die `CreateProject` Methode in diesem Projekt Factory möchten die tatsächliche Erstellung.  
  
## <a name="creating-an-owned-project"></a>Erstellen eines Eigentümer-Projekts  
 Ein Besitzer erstellt ein Eigentümer-Projekts in zwei Phasen:  
  
1.  Durch Aufrufen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.PreCreateForOwner%2A> Methode. Auf diese Weise können dem zugehörige Projekt zum Erstellen eines aggregierte Projektdatei-Objekts, das basierend auf der Eingabe steuern `IUnknown`. Das zugehörige Projekt übergibt die innere `IUnknown` und die aggregierten-Objekt wieder mit dem Besitzer-Projekt. Dies ermöglicht dem zugehörige Projekt Möglichkeit zum Speichern des inneren `IUnknown`.  
  
2.  Durch Aufrufen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A> Methode. Das zugehörige Projekt aller seiner Instanziierung ist, wenn diese Methode, statt aufgerufen wird `IVsProjectFactory::CreateProject` wie bei Projekten der Fall wäre, die nicht im Besitz sind. Die Eingabe `VSOWNEDPROJECTOBJECT` Enumeration ist in der Regel die aggregierte Projektdatei Eigentum ist. Das zugehörige Projekt kann die Variable verwenden, um festzustellen, ob die Projektobjekt bereits erstellt wurde (Cookie nicht gleich NULL) oder (Cookie gleich NULL) erstellt werden muss.  
  
 Projekttypen werden durch ein einzigartiges Projekt-GUID, ähnlich wie die CLSID des cocreatable COM-Objekt identifiziert. Ein Projekt Factory Handles Erstellen von Instanzen der einen einzelnen Projekttyp, obwohl es möglich ist, haben ein Projekt Factory verarbeiten in der Regel mehr als einem Projekttyp GUID.  
  
 Projekttypen sind mit einer bestimmten Dateinamenerweiterung verknüpft. Wenn ein Benutzer versucht, eine vorhandene Projektdatei an öffnen oder versucht, ein neues Projekt erstellen, indem Sie eine Vorlage klonen, verwendet die IDE die Erweiterung für die Datei zum Bestimmen von des entsprechenden Projekts-GUID an.  
  
 Sobald die IDE stellt fest, ob er muss ein neues Projekt erstellen oder öffnen Sie ein vorhandenes Projekt eines bestimmten Typs, die IDE die Informationen in der Registrierung unter [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Projects] verwendet, um die suchen VSPackage implementiert die erforderlichen Projekt--Factory. Die IDE lädt diese VSPackage. In der <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> -Methode, das VSPackage muss bei der IDE ab Werk Projekt registrieren, durch Aufrufen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes.RegisterProjectType%2A> Methode.  
  
 Die wichtigste Methode der `IVsProjectFactory` Schnittstelle ist <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> der beiden Szenarien behandelt werden sollen: Öffnen ein vorhandenes Projekt und Erstellen eines neuen Projekts. Die meisten Projekte speichern ihre Projektzustands in einer Projektdatei. In der Regel werden neue Projekte erstellt, durch Festlegen, dass eine Kopie der Vorlagendatei an die `CreateProject` -Methode, und klicken Sie dann die Kopie öffnen. Vorhandene Projekte sind instanziiert, indem direkt öffnen die Projektdatei übergeben `CreateProject` Methode. Die `CreateProject` Methode zusätzliche Features der Benutzeroberfläche für die Benutzer nach Bedarf anzeigen kann.  
  
 Ein Projekt kann auch keine Dateien verwenden und stattdessen Datenbankzustands Projekt in ein Speichermechanismus als Dateisystem, z. B. eine Datenbank oder Web-Server zu speichern. In diesem Fall der File-Name-Parameter übergeben, um die `CreateProject` Methode ist nicht tatsächlich einen Dateisystempfad jedoch eine eindeutige Zeichenfolge – eine URL, um den Projektdaten zu identifizieren. Sie müssen nicht die Vorlagendateien kopieren, die übergeben werden `CreateProject` zum Auslösen der entsprechenden Konstruktion Sequenz ausgeführt werden.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes>   
 [Prüfliste: Erstellen neuer Projekttypen](../../extensibility/internals/checklist-creating-new-project-types.md)
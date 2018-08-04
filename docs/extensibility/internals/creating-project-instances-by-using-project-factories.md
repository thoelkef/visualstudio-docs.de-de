---
title: Erstellen von Projektinstanzen mithilfe von Projektfactorys | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project factories
- projects [Visual Studio SDK], project factories
ms.assetid: 94c90012-8669-459c-af8e-307ac242c8c4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e25fd72601618fc02c27f3f01e6673229e526d52
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/03/2018
ms.locfileid: "39498912"
---
# <a name="create-project-instances-by-using-project-factories"></a>Erstellen von Projektinstanzen mithilfe von projektfactorys
Projekttypen in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] verwenden eine *Projektzuordnungsinstanz* zum Erstellen von Instanzen von Project-Objekte. Eine Projektzuordnungsinstanz ähnelt einer standard-Klassenfactory für cocreatable COM-Objekte. Project-Objekte sind jedoch nicht cocreatable; Sie können nur erstellt werden, mithilfe einer Projektfactory.  
  
 Die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE Ruft die Projekt-Factory, die in einem VSPackage implementiert werden, wenn ein Benutzer ein vorhandenes Projekt lädt oder ein neues Projekt in erstellt [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Das neue Projektobjekt stellt die IDE mit genügend Informationen zum Auffüllen **Projektmappen-Explorer**. Das neue Projektobjekt bietet auch die erforderlichen Schnittstellen für die Unterstützung aller relevanten UI-Aktionen, die von der IDE initiiert.  
  
 Sie können die implementieren die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> Schnittstelle in einer Klasse in Ihrem Projekt. In der Regel befindet sich in ein eigenes Modul.  
  
 Ein Beispiel für die Implementierung von der `IVsProjectFactory` Benutzeroberfläche, siehe *PrjFac.cpp*, der in enthalten ist die [Basisprojekt](http://msdn.microsoft.com/en-us/385fd2a3-d9f1-4808-87c2-a3f05a91fc36) Beispielverzeichnis.  
  
 Projekte, die unterstützen, die aggregiert wird durch einen Besitzer müssen es sich um einen Besitzer-Schlüssel in der Projektdatei beibehalten. Wenn die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> Methode mit einem Besitzer-Schlüssel an einem Projekt aufgerufen wird, das besessenen Projekt konvertiert seinen Besitzer-Schlüssel in eine Projektzuordnungsinstanz GUID dann Ruft die `CreateProject` Methode für dieses Projekt-Factory die tatsächliche Erstellung zu tun.  
  
## <a name="create-an-owned-project"></a>Erstellen Sie ein Projekt im Besitz des Benutzers  
 Ein Besitzer erstellt ein Projekt im Besitz in zwei Phasen:  
  
1.  Durch Aufrufen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.PreCreateForOwner%2A> Methode. Dies gibt dem besessenen Projekt eine Chance, erstellen Sie ein aggregiertes Projektobjekt auf Grundlage der Eingabe steuern `IUnknown`. Das Projekt im Besitz übergibt die innere `IUnknown` und des aggregierten Objekts wieder zum Projekt Besitzer. Dies gibt dem besessenen Projekt eine Möglichkeit zum Speichern von des inneren `IUnknown`.  
  
2.  Durch Aufrufen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A> Methode. Das Projekt im Besitz ist alle seine Instanziierung, wenn diese Methode, statt aufgerufen wird `IVsProjectFactory::CreateProject` wie bei Projekten, die nicht besitzt. Die Eingabe `VSOWNEDPROJECTOBJECT` Enumeration ist in der Regel im Besitz des Benutzers aggregierte Projekt. Das Projekt im Besitz kann diese Variable verwenden, um zu bestimmen, ob die Project-Objekt bereits erstellt wurde (Cookie nicht gleich NULL) bzw. (Cookie gleich NULL) erstellt werden muss.  
  
 Projekttypen werden durch eine eindeutige Projekt-GUID, ähnlich wie die CLSID des cocreatable COM-Objekt identifiziert. In der Regel Verarbeiten einer Factory projekthandles Erstellen von Instanzen der einen einzelnen Projekttyp, obwohl es möglich, dass ein Projekt-Factory ist mehr als ein Projekttyp-GUID.  
  
 Projekttypen sind eine bestimmte Dateinamenerweiterung zugeordnet. Wenn ein Benutzer versucht, eine vorhandene Projektdatei zu öffnen oder versucht, ein neues Projekt erstellen, indem Sie eine Vorlage zu klonen, verwendet die IDE die Erweiterung für die Datei um zu bestimmen, das entsprechende Projekt-GUID an.  
  
 Sobald die IDE stellt fest, ob sie ein neues Projekt erstellen oder öffnen Sie ein vorhandenes Projekt eines bestimmten Typs muss, verwendet die IDE die Informationen in der Registrierung unter **[HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Projects]**  finden Sie das VSPackage implementiert die erforderliche Projekt-Factory. Die IDE wird dieses VSPackage geladen. In der <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> -Methode, die VSPackages muss die Projekt-Factory mit der IDE registrieren, durch Aufrufen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes.RegisterProjectType%2A> Methode.  
  
 Die primäre Methode für die `IVsProjectFactory` Schnittstelle ist <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>, sollten die zwei Szenarien behandelt: Öffnen ein vorhandenes Projekt, und Erstellen eines neuen Projekts. Die meisten Projekte speichern ihren Projektzustand in einer Projektdatei. Neue Projekte werden in der Regel erstellt, durch Nutzung, die eine Kopie der Datei der Vorlage an die `CreateProject` -Methode, und öffnen Sie anschließend auf die Kopie. Vorhandene Projekte zur Instanziierung von werden direkt öffnen der Projektdatei übergeben `CreateProject` Methode. Die `CreateProject` Methode können zusätzliche Funktionen der Benutzeroberfläche angezeigt, für den Benutzer nach Bedarf.  
  
 Ein Projekt kann auch keine Dateien verwenden und stattdessen den Projektzustand in einem Speichermechanismus, als das Dateisystem, wie z. B. eine Datenbank oder Web-Server speichern. In diesem Fall der File-Name-Parameter übergeben, um die `CreateProject` Methode ist nicht tatsächlich einen Dateisystempfad jedoch eine eindeutige Zeichenfolge – eine URL, um die Projektdaten zu identifizieren. Sie müssen sich nicht um die Vorlagendateien kopieren, die übergeben werden `CreateProject` zum Auslösen der entsprechenden Konstruktionsreihenfolge ausgeführt werden.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes>   
 [Prüfliste: Erstellen Sie neuer Projekttypen](../../extensibility/internals/checklist-creating-new-project-types.md)
---
title: Wählen das Installationsverzeichnis für ein VSPackage | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- VSPackages, installation directory
ms.assetid: 01fbbb5b-f747-446c-afe0-2a081626a945
caps.latest.revision: 17
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 085c3bea9b9edc726fa09dd5d7658aff4a55e568
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="choosing-the-installation-directory-for-a-vspackage"></a>Das Installationsverzeichnis auswählen für ein VSPackage
Dateisystem des Benutzers muss ein VSPackage und die unterstützenden Dateien. Der Speicherort hängt davon ab, ob das VSPackage wird verwaltet oder nicht verwaltet, die Seite-an-Seite-Versionsschema und Benutzerauswahl.  
  
## <a name="unmanaged-vspackages"></a>Nicht verwaltete VSPackages  
 Eine nicht verwaltete VSPackage ist ein COM-Server, der an einem beliebigen Speicherort installiert werden kann. Registrierungsinformationen muss genau widerspiegelt, dessen Speicherort. Der Installer-Benutzeroberfläche (UI) zu versehen einen Standardspeicherort als Unterverzeichnis der ProgramFilesFolder Windows Installer-Eigenschaft. Zum Beispiel:  
  
 [ProgramFilesFolder] MyCompany\MyVSPackageProduct\V1.0\  
  
 Der Benutzer zugelassen werden sollte, ändern das Standardverzeichnis, um Benutzer aufnehmen zu können, die eine kleine Startpartition beibehalten und Anwendungen und Tools auf einem anderen Volume installieren möchten.  
  
 Wenn Ihr Schema Seite-an-Seite eine mit versionsverwaltung durch das VSPackage verwendet, können Sie die Unterverzeichnisse zum Speichern von unterschiedlichen Versionen verwenden. Zum Beispiel:  
  
 [ProgramFilesFolder] MyCompany\MyVSPackageProduct\V1.0\2002\  
  
 [ProgramFilesFolder] MyCompany\MyVSPackageProduct\V1.0\2003\  
  
 [ProgramFilesFolder] MyCompany\MyVSPackageProduct\V1.0\2005\  
  
## <a name="managed-vspackages"></a>Verwaltete VSPackages  
 Verwaltete VSPackages können auch an einem beliebigen Speicherort installiert werden. Allerdings sollten Sie immer installiert werden, im globalen Assemblycache (GAC), um die Assembly Ladezeiten zu reduzieren. Da verwaltete VSPackages immer Assemblys mit starkem Namen sind, bedeutet das im GAC installiert werden, dass die Überprüfung der Signatur mit starkem Namen nur zum Installationszeitpunkt verwendet. Assemblys mit starken Namen an anderer Stelle im Dateisystem installiert benötigen ihre Signaturen überprüft jedes Mal, wenn sie geladen werden. Wenn Sie verwaltete VSPackages im GAC installieren, verwenden Sie des Regpkg-Tools **/Assembly** Switch zum Schreiben der Registrierungseinträge, die auf den starken Namen der Assembly verweist.  
  
 Wenn Sie verwaltete VSPackages in einem anderen Speicherort als im GAC installieren, führen Sie die früheren Hinweise für nicht verwaltete VSPackages, die für die Auswahl Verzeichnishierarchien. Verwenden Sie das Regpkg-Tool **/ codebase** Switch zum Schreiben der Registrierungseinträge, die auf den Pfad der VSPackage-Assembly verweist.  
  
 Weitere Informationen finden Sie unter [registrieren und Aufheben der Registrierung von VSPackages](../../extensibility/registering-and-unregistering-vspackages.md).  
  
## <a name="satellite-dlls"></a>Satelliten-DLLs  
 Gemäß der Konvention VSPackage Satelliten-DLLs – die Ressourcen für ein bestimmtes Gebietsschema enthalten – befinden sich in Unterverzeichnissen des Verzeichnisses VSPackage. Die Unterverzeichnisse entsprechen den Gebietsschema-ID (LCID)-Werte.  
  
 [Verwalten von VSPackages](../../extensibility/managing-vspackages.md) gibt an, dass die Registrierungseinträge Where steuern [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tatsächlich sucht einer VSPackages Satelliten-DLL. Allerdings [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] versucht wird, laden eine Satelliten-DLL in einem Unterverzeichnis mit dem Namen für einen LCID-Wert in der folgenden Reihenfolge:  
  
1.  Standard-LCID (VS-LCID, z. B. \1033 für Englisch)  
  
2.  Standard-LCID mit die standardmäßige Sprachvariante an.  
  
3.  Systemstandard LCID.  
  
4.  Systemstandard LCID mit die standardmäßige Sprachvariante an.  
  
5.  USA Englisch (. \1033 oder. \0x409).  
  
 Die VSPackage-DLL enthält Ressourcen und die SatelliteDll\DllName Registrierung-Einstiegspunkte, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] versucht, die sie in der oben genannten Reihenfolge zu laden.  
  
## <a name="see-also"></a>Siehe auch  
 [Auswählen zwischen freigegebenen und mit Versionsangabe VSPackages](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)   
 [Verwalten von VSPackages](../../extensibility/managing-vspackages.md)   
 [Managed Package-Registrierung](http://msdn.microsoft.com/en-us/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)
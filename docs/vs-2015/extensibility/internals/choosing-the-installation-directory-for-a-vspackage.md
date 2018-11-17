---
title: Auswählen des Installationsverzeichnisses für ein VSPackage | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- VSPackages, installation directory
ms.assetid: 01fbbb5b-f747-446c-afe0-2a081626a945
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 385877b8a682574946bfd43e1e51acd771d00a2b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51775172"
---
# <a name="choosing-the-installation-directory-for-a-vspackage"></a>Auswählen des Installationsverzeichnisses für ein VSPackage
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ein VSPackage und die unterstützenden Dateien müssen auf dem System eines Benutzers Datei sein. Der Speicherort hängt davon ab, ob das VSPackage wird verwaltet oder nicht verwaltet, Ihr Schema für die versionsverwaltung von Seite-an-Seite, und klicken Sie auf Benutzerauswahl.  
  
## <a name="unmanaged-vspackages"></a>Nicht verwaltete VSPackages  
 Eine nicht verwaltete VSPackage ist ein COM-Server, der an einem beliebigen Speicherort installiert werden kann. Registrierungsinformationen muss genau widerspiegelt, den Speicherort. Der Installer-Benutzeroberfläche (UI) sollte es sich um einen Standardspeicherort als Unterverzeichnis der ProgramFilesFolder Windows Installer-Eigenschaft bereitstellen. Zum Beispiel:  
  
 [ProgramFilesFolder] MyCompany\MyVSPackageProduct\V1.0\  
  
 Der Benutzer sollte ermöglicht werden, ändern das Standardverzeichnis, um Benutzern zu ermöglichen, die eine kleine Startpartition zu halten, und Anwendungen und Tools auf einem anderen Volume installieren möchten.  
  
 Wenn das Schema für die Seite-an-Seite eine mit versionsverwaltung durch das VSPackage verwendet, können Sie Unterverzeichnisse, um verschiedene Versionen zu speichern. Zum Beispiel:  
  
 [ProgramFilesFolder] MyCompany\MyVSPackageProduct\V1.0\2002\  
  
 [ProgramFilesFolder] MyCompany\MyVSPackageProduct\V1.0\2003\  
  
 [ProgramFilesFolder] MyCompany\MyVSPackageProduct\V1.0\2005\  
  
## <a name="managed-vspackages"></a>Verwaltete VSPackages  
 Verwaltete VSPackages können auch an einem beliebigen Speicherort installiert werden. Allerdings sollten Sie immer installiert werden, im globalen Assemblycache (GAC), um die Assembly Ladezeiten zu reduzieren. Da verwaltete VSPackages immer Assemblys mit starkem Namen sind, bedeutet, dass im GAC installieren, dass die Überprüfung der Signatur mit starkem Namen nur zum Installationszeitpunkt dauert. Assemblys mit starkem Namen an anderer Stelle im Dateisystem installiert müssen die Signaturen überprüft jedes Mal, wenn sie geladen werden. Wenn Sie verwaltete VSPackages im GAC installieren, verwenden Sie des Regpkg-Tools **/Assembly** Switch zum Schreiben der Registrierungseinträge auf dem starken Namen der Assembly verweist.  
  
 Wenn Sie verwaltete VSPackages in einem anderen Speicherort als im GAC installieren, führen Sie die früheren Hinweise, die für nicht verwaltete VSPackages, die für die Auswahl Verzeichnishierarchien. Verwenden Sie das Regpkg-Tool **/ codebase** Switch zum Schreiben der Registrierungseinträge, die auf den Pfad der VSPackage-Assembly verweist.  
  
 Weitere Informationen finden Sie unter [registrieren und Aufheben der Registrierung des VSPackages](../../extensibility/registering-and-unregistering-vspackages.md).  
  
## <a name="satellite-dlls"></a>Satelliten-DLLs  
 Gemäß der Konvention VSPackage Satelliten-DLLs, die Ressourcen für ein bestimmtes Gebietsschema enthalten, befinden sich in den Unterverzeichnissen des Verzeichnisses VSPackage. Die Unterverzeichnisse entsprechen Gebietsschema-ID (LCID) Werten.  
  
 [Verwalten von VSPackages](../../extensibility/managing-vspackages.md) gibt an, dass die Registrierungseinträge steuern, wo [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] tatsächlich sucht einer VSPackages Satelliten-DLL. Allerdings [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] versucht, eine Satelliten-DLL in einem Unterverzeichnis mit dem Namen für einen LCID-Wert, in der folgenden Reihenfolge zu laden:  
  
1. Standard-LCID (Visual Studio-LCID, z. B. \1033 für Englisch)  
  
2. Standard-LCID mit der standardmäßigen Sprachvariante an.  
  
3. Systemstandard LCID.  
  
4. Systemstandard LCID mit der standardmäßigen Sprachvariante an.  
  
5. USA Englisch (. \1033 oder. \0x409).  
  
   Wenn Ihre VSPackage-DLL-Ressourcen und Registry Einstiegspunkte SatelliteDll\DllName, beinhaltet [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] versucht, die sie in der oben genannten Reihenfolge zu laden.  
  
## <a name="see-also"></a>Siehe auch  
 [Auswählen zwischen freigegebenen und mit versionsverwaltung durch das VSPackages](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)   
 [Verwalten von VSPackages](../../extensibility/managing-vspackages.md)   
 [Managed Package-Registrierung](http://msdn.microsoft.com/en-us/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)


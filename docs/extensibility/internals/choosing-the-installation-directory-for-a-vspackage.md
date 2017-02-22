---
title: "W&#228;hlen das Installationsverzeichnis f&#252;r ein VSPackage | Microsoft Docs"
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
  - "VSPackages Installationsverzeichnis"
ms.assetid: 01fbbb5b-f747-446c-afe0-2a081626a945
caps.latest.revision: 17
caps.handback.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
---
# W&#228;hlen das Installationsverzeichnis f&#252;r ein VSPackage
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

VSPackages und die unterstützenden Dateien müssen im Dateisystem eines Benutzers sein.  Die Position richtet an, ob verwaltete VSPackages oder das Schema für parallele Versioning und Benutzerauswahl nicht verwaltet ist.  
  
## Nicht verwaltete VSPackages  
 Nicht verwaltete VSPackages ist ein COM\-Server, der an einem beliebigen Speicherort installiert werden kann.  Sein Registrierungsdaten genau wiedergegeben muss mit seinen Speicherort.  Das Installationsprogramm Benutzeroberfläche sollte einen Standardspeicherort als Unterverzeichnis der ProgramFilesFolder\-Windows Installer\-Eigenschaft bereitstellen.  Beispiele:  
  
 \[ProgramFilesFolder\] MyCompany \\ \\. \\ MyVSPackageProduct V1.0  
  
 Dem Benutzer muss zulässig sind, um das Standardverzeichnis ändern, um Benutzer zu verwalten, die eine kleine Startpartition halten und lieber Anwendungen und Tools auf einem anderen Volume zu installieren.  
  
 Wenn das parallele Schema Gibt ein VSPackage können Sie Unterverzeichnisse verwenden, um unterschiedliche Versionen gespeichert werden.  Beispiele:  
  
 \[ProgramFilesFolder\] MyCompany \\ MyVSPackageProduct \\ V1.0 \\ 2002 \\  
  
 \[ProgramFilesFolder\] MyCompany \\ MyVSPackageProduct \\ V1.0 \\ 2003 \\  
  
 \[ProgramFilesFolder\] MyCompany \\ MyVSPackageProduct \\ V1.0 \\ 2005 \\  
  
## Verwaltetes VSPackages  
 Verwaltetes VSPackages kann auch an einem beliebigen Speicherort installiert werden.  Allerdings sollten Sie sie im globalen Assemblycache \(GAC\) zu installieren, sollten immer die Assembly ladezeit zu reduzieren.  Da verwaltete VSPackages immer Assemblys mit starkem Namen werden sie im GAC installieren bedeutet, dass die Signaturüberprüfung mit starkem Namen nur bei der Installation verwendet.  Die Assembly mit starkem Namen, die an anderer Stelle im Dateisystem installiert werden, müssen deren Signaturen überprüfen lassen, wenn sie geladen werden.  Wenn Sie einen verwalteten VSPackages im GAC installieren, verwenden Sie den Schalter **\/assembly** regpkg des Tools, um die Registrierungseinträge zu schreiben, die auf den starken Namen der Assembly zeigen.  
  
 Wenn Sie einen verwalteten VSPackages in einem anderen Speicherort als dem GAC installieren, geben Sie nach dem vorherigen Hinweise, der für nicht verwaltete VSPackages zum Auswählen von hierarchien Verzeichnis angegeben ist.  Verwenden Sie den Schalter **\/codebase** regpkg des Tools, um die Registrierungseinträge zu schreiben, die auf den Pfad der VSPackage\-Assemblys zeigen.  
  
 Weitere Informationen finden Sie unter [Registrieren und Aufheben der Registrierung von VSPackages](../../extensibility/registering-and-unregistering-vspackages.md).  
  
## Satelliten\-DLLs  
 Standardmäßig sind VSPackage\-Satelitte DLL, die Ressourcen für ein bestimmtes Gebietsschema enthalten — VSPackage\-Verzeichnisses in Unterverzeichnissen des.  Die Unterverzeichnisse entsprechen den Werten der Gebietsschemas\-ID \(LCID\).  
  
 [Verwalten von VSPackages](../../extensibility/managing-vspackages.md) gibt an, dass die Registrierungseinträge steuern, wo tatsächlich [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nach einem VSPackages Satelliten\-DLL gesucht werden soll.  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] jedoch versucht, eine Satelliten\-DLL in einem Unterverzeichnis zu laden, das für einen LCID\-Wert in der folgenden Reihenfolge:  
  
1.  Standard GEGEN LCID \(LCID \\ z. B. 1033 für Englisch\)  
  
2.  standardmäßigen LCID mit der standardmäßigen Teilsprache.  
  
3.  Systemstandard LCID.  
  
4.  Systemstandard LCID mit der standardmäßigen Teilsprache.  
  
5.  US  Englisch \(.  \\ oder 1033.  0x409 \\\).  
  
 Wenn das VSPackage DLL Ressourcen und Einsprungadressen des SatelliteDll \\ DllName Registrierungseintrags enthält, darauf [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] versucht, sie in der oben genannten Reihenfolge zu laden.  
  
## Siehe auch  
 [Auswählen zwischen freigegebenen und versioniert VSPackages](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)   
 [Verwalten von VSPackages](../../extensibility/managing-vspackages.md)   
 [Managed Package Registration](http://msdn.microsoft.com/de-de/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)
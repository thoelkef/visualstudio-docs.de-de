---
title: Auswählen des Installationsverzeichnisses für ein VSPackage | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, installation directory
ms.assetid: 01fbbb5b-f747-446c-afe0-2a081626a945
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: be54c19a1e09b610611c8791d62d012ebdaf5ae8
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60106266"
---
# <a name="choose-the-installation-directory-for-a-vspackage"></a>Wählen Sie das Installationsverzeichnis für ein VSPackage
Ein VSPackage und die unterstützenden Dateien müssen auf dem System eines Benutzers Datei sein. Der Speicherort hängt davon ab, ob das VSPackage wird verwaltet oder nicht verwaltet, Ihr Schema für die versionsverwaltung von Seite-an-Seite, und klicken Sie auf Benutzerauswahl.

## <a name="unmanaged-vspackages"></a>Nicht verwaltete VSPackages
 Eine nicht verwaltete VSPackage ist ein COM-Server, der an einem beliebigen Speicherort installiert werden kann. Registrierungsinformationen muss die Position genau wiedergeben. Der Installer-Benutzeroberfläche (UI) sollte einen Standardspeicherort als Unterverzeichnis des Bereitstellen der `ProgramFilesFolder` Windows Installer-Eigenschaftswert. Zum Beispiel:

*&lt;ProgramFilesFolder&gt;\\&lt;MyCompany&gt;\\&lt;MyVSPackageProduct&gt;\V1.0\\*

 Der Benutzer sollte ermöglicht werden, ändern das Standardverzeichnis, um Benutzern zu ermöglichen, die eine kleine Startpartition zu halten, und Anwendungen und Tools auf einem anderen Volume installieren möchten.

 Wenn das Schema für die Seite-an-Seite eine mit versionsverwaltung durch das VSPackage verwendet, können Sie Unterverzeichnisse, um verschiedene Versionen zu speichern. Zum Beispiel:

 *&lt;ProgramFilesFolder&gt;\\&lt;MyCompany&gt;\\&lt;MyVSPackageProduct&gt;\\V1.0\\2002\\*

 *&lt;ProgramFilesFolder&gt;\\&lt;MyCompany&gt;\\&lt;MyVSPackageProduct&gt;\\V1.0\\2003\\*

 *&lt;ProgramFilesFolder&gt;\\&lt;MyCompany&gt;\\&lt;MyVSPackageProduct&gt;\\V1.0\\2005\\*

## <a name="managed-vspackages"></a>Verwaltete VSPackages
 Verwaltete VSPackages können auch an einem beliebigen Speicherort installiert werden. Allerdings sollten Sie immer installiert werden, im globalen Assemblycache (GAC), um die Assembly Ladezeiten zu reduzieren. Da verwaltete VSPackages immer Assemblys mit starkem Namen sind, bedeutet, dass im GAC installieren, dass die Überprüfung der Signatur mit starkem Namen nur zum Installationszeitpunkt dauert. Assemblys mit starkem Namen an anderer Stelle im Dateisystem installiert müssen die Signaturen überprüft jedes Mal, wenn sie geladen werden. Wenn Sie verwaltete VSPackages im GAC installieren, verwenden Sie des Regpkg-Tools **/Assembly** Switch zum Schreiben der Registrierungseinträge auf dem starken Namen der Assembly verweist.

 Wenn Sie verwaltete VSPackages in einem anderen Speicherort als im GAC installieren, führen Sie die früheren Hinweise, die für nicht verwaltete VSPackages, die für die Auswahl Verzeichnishierarchien. Verwenden Sie das Regpkg-Tool **/ codebase** Switch zum Schreiben der Registrierungseinträge, die auf den Pfad der VSPackage-Assembly verweist.

 Weitere Informationen finden Sie unter [registrieren und Aufheben der Registrierung von VSPackages](../../extensibility/registering-and-unregistering-vspackages.md).

## <a name="satellite-dlls"></a>Satelliten-DLLs
 Gemäß der Konvention VSPackage Satelliten-DLLs, die Ressourcen für ein bestimmtes Gebietsschema enthalten, befinden sich in Unterverzeichnissen von der *VSPackage* Verzeichnis. Die Unterverzeichnisse entsprechen Gebietsschema-ID (LCID) Werten.

 Die [verwalten VSPackages](../../extensibility/managing-vspackages.md) Artikel gibt an, dass die Registrierungseinträge steuern, wo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tatsächlich sucht einer VSPackages Satelliten-DLL. Allerdings [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] versucht, eine Satelliten-DLL in einem Unterverzeichnis mit dem Namen für einen LCID-Wert, in der folgenden Reihenfolge zu laden:

1. Standard-LCID (Visual Studio-LCID, z. B. *\1033* für Englisch)

2. Standard-LCID mit der standardmäßigen Sprachvariante an.

3. Systemstandard LCID.

4. Systemstandard LCID mit der standardmäßigen Sprachvariante an.

5. USA Englisch (*. \1033* oder *. \0x409*).

Wenn Ihre VSPackage-DLL-Ressourcen enthält und die **SatelliteDll\DllName** Registrierungseintrag verweist, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] versucht, die sie in der oben genannten Reihenfolge zu laden.

## <a name="see-also"></a>Siehe auch
- [Wählen Sie zwischen freigegebenen und mit versionsverwaltung durch das VSPackages](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)
- [Verwalten von VSPackages](../../extensibility/managing-vspackages.md)
- [Verwalten der Registrierung des Anwendungspakets](https://msdn.microsoft.com/library/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)
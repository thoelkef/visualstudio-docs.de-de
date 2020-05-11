---
title: Auswählen des Installationsverzeichnisses für ein VSPackage | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, installation directory
ms.assetid: 01fbbb5b-f747-446c-afe0-2a081626a945
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b8391cbdd3a857ea4ebaf3a36655520935f1a128
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709761"
---
# <a name="choose-the-installation-directory-for-a-vspackage"></a>Wählen Sie das Installationsverzeichnis für ein VSPackage
Ein VSPackage und seine unterstützenden Dateien müssen sich im Dateisystem eines Benutzers befinden. Der Speicherort hängt davon ab, ob das VSPackage verwaltet oder nicht verwaltet wird, ihr side-by-side Versionsschema und die Benutzerauswahl.

## <a name="unmanaged-vspackages"></a>Nicht verwaltete VSPackages
 Ein nicht verwaltetes VSPackage ist ein COM-Server, der an jedem Speicherort installiert werden kann. Seine Registrierungsinformationen müssen seinen Standort genau widerspiegeln. Die Benutzeroberfläche des Installationsprogramms sollte einen Standardspeicherort als `ProgramFilesFolder` Unterverzeichnis des Windows Installer-Eigenschaftswerts bereitstellen. Beispiel:

*&lt;ProgramFilesFolder&gt;\\&lt;&gt;\\&lt;MyCompany MyVSPackageProduct&gt;\\*

 Der Benutzer sollte das Standardverzeichnis ändern können, um Benutzer aufzunehmen, die eine kleine Startpartition beibehalten und es vorziehen, Anwendungen und Tools auf einem anderen Volume zu installieren.

 Wenn Ihr Side-by-Side-Schema ein versioniertes VSPackage verwendet, können Sie Unterverzeichnisse verwenden, um verschiedene Versionen zu speichern. Beispiel:

 *&lt;ProgramFilesFolder&gt;\\&lt;MyCompany&gt;\\&lt;MyVSPackageProduct&gt;\\V1.0\\2002\\*

 *&lt;ProgramFilesFolder&gt;\\&lt;MyCompany&gt;\\&lt;MyVSPackageProduct&gt;\\V1.0\\2003\\*

 *&lt;ProgramFilesFolder&gt;\\&lt;MyCompany&gt;\\&lt;MyVSPackageProduct&gt;\\V1.0\\2005\\*

## <a name="managed-vspackages"></a>Verwaltete VSPackages
 Verwaltete VSPackages können auch an jedem Beliebigen ortmöglich installiert werden. Sie sollten jedoch immer in Betracht ziehen, sie im globalen Assemblycache (GAC) zu installieren, um die Auslastung der Assembly zu reduzieren. Da verwaltete VSPackages immer Assemblys mit starkem Namen sind, bedeutet die Installation im GAC, dass ihre Überprüfung der Signatur mit starkem Namen nur zur Installationszeit erfolgt. Assemblys mit starkem Namen, die an anderer Stelle im Dateisystem installiert sind, müssen ihre Signaturen bei jedem Laden überprüfen lassen. Wenn Sie verwaltete VSPackages im GAC installieren, verwenden Sie den **Schalter /assembly** des werkzeugs regpkg, um Registrierungseinträge zu schreiben, die auf den starken Namen der Assembly verweisen.

 Wenn Sie verwaltete VSPackages an einem anderen Speicherort als dem GAC installieren, befolgen Sie die früheren Empfehlungen für nicht verwaltete VSPackages zur Auswahl von Verzeichnishierarchien. Verwenden Sie den Schalter **/codebase** des werkzeugs regpkg, um Registrierungseinträge zu schreiben, die auf den Pfad der VSPackage-Assembly verweisen.

 Weitere Informationen finden Sie unter [Registrieren und Aufheben der Registrierung von VSPackages](../../extensibility/registering-and-unregistering-vspackages.md).

## <a name="satellite-dlls"></a>Satelliten-DLLs
 Gemäß der Konvention befinden sich VSPackage-Satelliten-DLLs, die Ressourcen für ein *VSPackage* bestimmtes Gebietsschema enthalten, in Unterverzeichnissen des VSPackage-Verzeichnisses. Die Unterverzeichnisse entsprechen den LCID-Werten (Locale ID).

 Der Artikel [VSPackages verwalten](../../extensibility/managing-vspackages.md) gibt [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] an, dass Registrierungseinträge steuern, wo tatsächlich nach der Satelliten-DLL eines VSPackage gesucht wird. Versucht [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] jedoch, eine Satelliten-DLL in einem Unterverzeichnis zu laden, das nach einem LCID-Wert benannt ist, in der folgenden Reihenfolge:

1. Standard-LCID (Visual Studio LCID; z. B. *1033 USD* für Englisch)

2. Standard-LCID mit der Standarduntersprache.

3. Systemstandard-LCID.

4. Systemstandard-LCID mit der Standarduntersprache.

5. Us-Englisch (*.1033* oder *.'0x409*).

Wenn Ihre VSPackage-DLL Ressourcen enthält und der **Registrierungseintrag SatelliteDll-DllName** darauf verweist, versucht, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sie in der oben genannten Reihenfolge zu laden.

## <a name="see-also"></a>Weitere Informationen
- [Wählen Sie zwischen freigegebenen und versionierten VSPackages](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)
- [Verwalten von VSPackages](../../extensibility/managing-vspackages.md)
- [Verwalten der Paketregistrierung](https://msdn.microsoft.com/library/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)

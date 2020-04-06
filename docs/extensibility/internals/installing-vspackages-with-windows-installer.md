---
title: VsPackages mit Windows Installer installieren | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- installation [Visual Studio SDK], with Windows Installer
- VSPackages, deploying
ms.assetid: 41d2c72c-0a97-4fcd-b3aa-33a8d3aa962a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2eb90dbffa9f04cd17afa70d2bdfc59205bc99cb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707460"
---
# <a name="installing-vspackages-with-windows-installer"></a>Installieren von VSPackages mit Windows Installer
Die Integration Ihres [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] VSPackage in erfordert mehr als nur das Kopieren von Dateien auf den Computer eines Benutzers. Das Installationsprogramm Ihres VSPackage muss das VSPackage und seine abhängigen Dateien installieren, registrieren und in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]integrieren. Ihr VSPackage kann Integrationsfunktionen nutzen, z. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] B. die Anzeige eines Symbols auf dem Begrüßungsbildschirm und das Dialogfeld "Info".

 Microsoft Windows Installer-Dateien sind die empfohlene Methode zum Verteilen Ihrer VSPackages. Benutzerfreundliche Windows Installer-Pakete können auf jedem Windows-Betriebssystem ausgeführt werden, das von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]unterstützt wird. Weitere Informationen finden Sie unter [Windows Installer](https://msdn.microsoft.com/library/121be21b-b916-43e2-8f10-8b080516d2a0).

## <a name="in-this-section"></a>In diesem Abschnitt
- [Grundlagen zu Windows Installer](../../extensibility/internals/windows-installer-basics.md)

 Bietet einen Überblick über das Windows Installer.

- [VSPackage-Setupszenarien](../../extensibility/internals/vspackage-setup-scenarios.md)

 Erläutert verschiedene Möglichkeiten, wie Sie nebeneinander Installationen Ihrer VSPackages und [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]unterstützen können.

- [Erstellen eines Windows Installer-Pakets](../../extensibility/internals/authoring-a-windows-installer-package.md)

 Bietet einen Überblick über die typischen Schritte, die Installateure ausführen, um VSPackages korrekt zu installieren und in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]zu integrieren.

- [Ermitteln von Systemanforderungen](../../extensibility/internals/detecting-system-requirements.md)

 Beschreibt, wie ein [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Installationsprogramm die Installation erkennen und deren Komponenten abbrechen kann, wenn die VSPackage-Anforderungen nicht erfüllt werden.

- [Verwaltung von Komponenten](../../extensibility/internals/component-management.md)

 Erläutert die Entwicklung eines Installationsprogramms, das die Integrität früherer Produktversionen aufrechtzuerhalten.

- [Auswählen des Installationsverzeichnisses für ein VSPackage](../../extensibility/internals/choosing-the-installation-directory-for-a-vspackage.md)

 Fasst die Optionen zum Auffinden von VSPackages zusammen.

- [VSPackage-Registrierung](../../extensibility/internals/vspackage-registration.md)

 Erläutert, wie VSPackages zur Installationszeit registriert werden und warum die Selbstregistrierung eine schlechte Idee ist.

- [Bereitstellen von Projekttypen](../../extensibility/internals/deploying-project-types.md)

 Erläutert die Verwendung des neuen Projektaggregators für Projekttypen mit verwaltetem Code.

- [Gewusst wie: Generieren von Registrierungsinformationen für einen Installer](../../extensibility/internals/how-to-generate-registry-information-for-an-installer.md)

 Erläutert, wie RegPkg.exe verwendet wird, um ein Registrierungsmanifest für ein verwaltetes VSPackage zu generieren.

- [Befehle, die nach der Installation ausgeführt werden müssen](../../extensibility/internals/commands-that-must-be-run-after-installation.md)

 Erläutert, wie Nachinstallationsbefehle ausgeführt werden, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]um VSPackages in zu integrieren.

- [Deinstallieren eines VSPackage mit Windows Installer](../../extensibility/internals/uninstalling-a-vspackage-with-windows-installer.md)

 Beschreibt die Schritte, die Ihr Installationsprogramm ausführen muss, wenn Benutzer Ihr VSPackage deinstallieren.

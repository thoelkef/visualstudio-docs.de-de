---
title: Installieren von VSPackages mit Windows Installer | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- installation [Visual Studio SDK], with Windows Installer
- VSPackages, deploying
ms.assetid: 41d2c72c-0a97-4fcd-b3aa-33a8d3aa962a
caps.latest.revision: 31
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 35942f6babf18967e11f268ef0412acb4cc8edf7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65687467"
---
# <a name="installing-vspackages-with-windows-installer"></a>Installieren von VSPackages mit Windows Installer
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die Integration des VSPackage in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] erfordert mehr als nur das Kopieren von Dateien auf den Computer eines Benutzers. Das VSPackage-Installationsprogramm muss das VSPackage und seine abhängigen Dateien installieren und Sie registrieren und in integrieren [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Das VSPackage kann Integrations Features wie das Anzeigen eines Symbols auf dem Begrüßungs [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Bildschirm und das Dialogfeld "Info" nutzen.  
  
 Microsoft Windows Installer Dateien sind die empfohlene Vorgehensweise zum Verteilen von VSPackages. Leicht zu verwendende Windows Installer Pakete können unter allen Windows-Betriebssystemen ausgeführt werden, die von unterstützt werden [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Weitere Informationen finden Sie unter [Windows Installer](https://msdn.microsoft.com/121be21b-b916-43e2-8f10-8b080516d2a0).  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Grundlagen zu Windows Installer](../../extensibility/internals/windows-installer-basics.md)  
 Bietet eine Übersicht über die Windows Installer.  
  
 [VSPackage-Setupszenarien](../../extensibility/internals/vspackage-setup-scenarios.md)  
 Erläutert verschiedene Methoden, mit denen Sie parallele Installationen Ihrer VSPackages und unterstützen können [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
 [Erstellen eines Windows Installer-Pakets](../../extensibility/internals/authoring-a-windows-installer-package.md)  
 Bietet eine Übersicht über die typischen Schritte, die Installationsprogramme befolgen, um VSPackages ordnungsgemäß zu installieren und in zu integrieren [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
 [Ermitteln von Systemanforderungen](../../extensibility/internals/detecting-system-requirements.md)  
 Beschreibt, wie ein Installer [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] und seine Komponenten erkennen und Setup abbrechen kann, wenn die VSPackage-Anforderungen nicht erfüllt werden.  
  
 [Verwaltung von Komponenten](../../extensibility/internals/component-management.md)  
 Erläutert, wie ein Installationsprogramm entwickelt wird, das die Integrität früherer Produktversionen beibehält.  
  
 [Auswählen des Installationsverzeichnisses für ein VSPackage](../../extensibility/internals/choosing-the-installation-directory-for-a-vspackage.md)  
 Fasst die Optionen zum Suchen von VSPackages zusammen.  
  
 [VSPackage-Registrierung](../../extensibility/internals/vspackage-registration.md)  
 Erläutert, wie VSPackages zur Installationszeit registriert werden und warum die Selbstregistrierung eine gute Idee ist.  
  
 [Bereitstellen von Projekttypen](../../extensibility/internals/deploying-project-types.md)  
 Erläutert, wie der neue Projekttyp Aggregator für Projekttypen mit verwaltetem Code verwendet wird.  
  
 [Gewusst wie: Generieren von Registrierungsinformationen für einen Installer](../../extensibility/internals/how-to-generate-registry-information-for-an-installer.md)  
 Erläutert, wie RegPkg.exe verwendet wird, um ein Registrierungs Manifest für ein verwaltetes VSPackage zu generieren.  
  
 [Befehle, die nach der Installation ausgeführt werden müssen](../../extensibility/internals/commands-that-must-be-run-after-installation.md)  
 Erläutert das Ausführen von Befehlen nach der Installation, um VSPackages in zu integrieren [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
 [Deinstallieren eines VSPackage mit Windows Installer](../../extensibility/internals/uninstalling-a-vspackage-with-windows-installer.md)  
 Beschreibt die Schritte, die das Installationsprogramm ausführen muss, wenn Benutzer das VSPackage deinstallieren.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Installieren von VSPackages](../../misc/installing-vspackages.md)  
 Erläutert, wie VSPackages erstellt und installiert und wie Benutzer unterstützt werden, die mehrere Versionen von [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] gleichzeitig ausführen.

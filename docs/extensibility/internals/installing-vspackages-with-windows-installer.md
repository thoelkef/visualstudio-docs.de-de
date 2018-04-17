---
title: Installieren von VSPackages mit Windows Installer | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- installation [Visual Studio SDK], with Windows Installer
- VSPackages, deploying
ms.assetid: 41d2c72c-0a97-4fcd-b3aa-33a8d3aa962a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6fafebe0dc2bb8e13c99be8b340e7f5663a9930f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="installing-vspackages-with-windows-installer"></a>Installieren von VSPackages mit Windows Installer
Integrieren Ihr VSPackage in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] erfordert mehr als nur kopieren von Dateien auf dem Computer eines Benutzers. Ihr VSPackage-Installer muss das VSPackage und seinen abhängigen Dateien installieren und registrieren und integrieren Sie sie in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Das VSPackage nutzen Integrationsfunktionen, z. B. ein Symbol angezeigt, auf die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] splash-Bildschirm und Info (Dialogfeld).  
  
 Microsoft Windows Installer-Dateien sind die empfohlene Methode, um Ihre VSPackages zu verteilen. Einfach zu verwendende Windows Installer-Pakete können auf alle von unterstützten Windows-Betriebssystem ausführen [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Weitere Informationen finden Sie unter [Windows Installer](http://msdn.microsoft.com/en-us/121be21b-b916-43e2-8f10-8b080516d2a0).  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Grundlagen zu Windows Installer](../../extensibility/internals/windows-installer-basics.md)  
 Bietet eine Übersicht über die Windows Installer.  
  
 [VSPackage-Setupszenarien](../../extensibility/internals/vspackage-setup-scenarios.md)  
 Beschreibt verschiedene Möglichkeiten können Sie die Seite-an-Seite-Installationen von sowohl Ihre VSPackages unterstützen und [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 [Erstellen eines Windows Installer-Pakets](../../extensibility/internals/authoring-a-windows-installer-package.md)  
 Bietet eine Übersicht über die typischen Schritte Installationsprogramme befolgen, um ordnungsgemäß zu installieren und Integrieren von VSPackages in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 [Ermitteln von Systemanforderungen](../../extensibility/internals/detecting-system-requirements.md)  
 Beschreibt, wie ein Installationsprogramm erkennt [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] und richten Sie die Komponenten und "Abbrechen", falls VSPackage-Anforderungen nicht erfüllt werden.  
  
 [Verwaltung von Komponenten](../../extensibility/internals/component-management.md)  
 Erläutert, wie ein Installationsprogramm entwickeln, die die Integrität der früheren Produktversionen beibehalten wird.  
  
 [Auswählen des Installationsverzeichnisses für ein VSPackage](../../extensibility/internals/choosing-the-installation-directory-for-a-vspackage.md)  
 Werden die Optionen zum Suchen von VSPackages zusammengefasst.  
  
 [VSPackage-Registrierung](../../extensibility/internals/vspackage-registration.md)  
 Erläutert, wie VSPackages Zeitpunkt der Installation registriert sind und warum Self-Registrierung ist nicht sinnvoll.  
  
 [Bereitstellen von Projekttypen](../../extensibility/internals/deploying-project-types.md)  
 Erläutert, wie die neuen Projekttyp Aggregator für verwalteten Code Projekttypen zur Verfügung.  
  
 [Gewusst wie: Generieren von Registrierungsinformationen für einen Installer](../../extensibility/internals/how-to-generate-registry-information-for-an-installer.md)  
 Erläutert das RegPkg.exe verwenden, um ein Manifest für die Registrierung für ein verwaltetes VSPackage zu generieren.  
  
 [Befehle, die nach der Installation ausgeführt werden müssen](../../extensibility/internals/commands-that-must-be-run-after-installation.md)  
 Erläutert, wie nach der Installation-Befehle zum Integrieren von VSPackages in ausführen [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 [Deinstallieren eines VSPackage mit Windows Installer](../../extensibility/internals/uninstalling-a-vspackage-with-windows-installer.md)  
 Beschreibt die Schritte, die das Installationsprogramm ausführen muss, wenn Benutzer Ihr VSPackage deinstallieren.  
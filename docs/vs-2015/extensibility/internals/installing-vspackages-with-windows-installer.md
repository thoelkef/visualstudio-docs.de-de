---
title: Installieren von VSPackages mit Windows Installer | Microsoft-Dokumentation
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
- installation [Visual Studio SDK], with Windows Installer
- VSPackages, deploying
ms.assetid: 41d2c72c-0a97-4fcd-b3aa-33a8d3aa962a
caps.latest.revision: 31
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ae0e99b278924a123410f5590cea9f8239acd9ad
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49227967"
---
# <a name="installing-vspackages-with-windows-installer"></a>Installieren von VSPackages mit Windows Installer
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Integrieren Ihr VSPackage in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] erfordert mehr als nur kopieren von Dateien auf dem Computer eines Benutzers. Ihre VSPackage Installer muss installieren Sie das VSPackage und dessen abhängigen Dateien hinzu, und registrieren und integrieren Sie sie in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Das VSPackage kann nutzen Integrationsfeatures wie z. B. das Anzeigen eines Symbols auf die [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] splash-Bildschirm und Informationen zum Dialogfeld.  
  
 Microsoft Windows Installer-Dateien sind die empfohlene Methode zum Verteilen Ihre VSPackages. Einfach zu bedienende Windows Installer-Pakete können auf jedem Windows-Betriebssystem, die von unterstützt ausgeführt [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Weitere Informationen finden Sie unter [Windows Installer](http://msdn.microsoft.com/en-us/121be21b-b916-43e2-8f10-8b080516d2a0).  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Grundlagen zu Windows Installer](../../extensibility/internals/windows-installer-basics.md)  
 Bietet eine Übersicht über die Windows Installer.  
  
 [VSPackage-Setupszenarien](../../extensibility/internals/vspackage-setup-scenarios.md)  
 Beschreibt verschiedene Möglichkeiten, Sie können die Seite-an-Seite-Installationen von sowohl Ihre VSPackages unterstützen und [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
 [Erstellen eines Windows Installer-Pakets](../../extensibility/internals/authoring-a-windows-installer-package.md)  
 Bietet eine Übersicht über die typischen Schritte Installationsprogramme zu befolgen, um ordnungsgemäß zu installieren und integrieren VSPackages in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
 [Ermitteln von Systemanforderungen](../../extensibility/internals/detecting-system-requirements.md)  
 Beschreibt, wie ein Installationsprogramm erkannt werden kann [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] und zugehörigen Komponenten und "Abbrechen" einrichten, wenn VSPackage-Anforderungen nicht erfüllt werden.  
  
 [Verwaltung von Komponenten](../../extensibility/internals/component-management.md)  
 Erläutert, wie ein Installationsprogramm zu entwickeln, die die Integrität der früheren Produktversionen beibehält.  
  
 [Auswählen des Installationsverzeichnisses für ein VSPackage](../../extensibility/internals/choosing-the-installation-directory-for-a-vspackage.md)  
 Sind die Optionen für die Suche nach VSPackages zusammengefasst.  
  
 [VSPackage-Registrierung](../../extensibility/internals/vspackage-registration.md)  
 Erläutert, wie VSPackages bei der Installation registriert werden, und warum selbstregistrierung ist keine gute Idee.  
  
 [Bereitstellen von Projekttypen](../../extensibility/internals/deploying-project-types.md)  
 Erläutert, wie den neue Projekttyp Aggregator für Projekttypen von verwaltetem Code.  
  
 [Gewusst wie: Generieren von Registrierungsinformationen für einen Installer](../../extensibility/internals/how-to-generate-registry-information-for-an-installer.md)  
 Erläutert, wie RegPkg.exe verwenden, um ein Manifest für die Registrierung für ein verwaltetes VSPackage zu generieren.  
  
 [Befehle, die nach der Installation ausgeführt werden müssen](../../extensibility/internals/commands-that-must-be-run-after-installation.md)  
 Erläutert, wie führen Sie nach der Installation Befehle aus, um die Integration von VSPackages in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
 [Deinstallieren eines VSPackage mit Windows Installer](../../extensibility/internals/uninstalling-a-vspackage-with-windows-installer.md)  
 Beschreibt die Schritte, die das Installationsprogramm ausführen muss, wenn Benutzer Ihr VSPackage deinstallieren.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Installieren von VSPackages](../../misc/installing-vspackages.md)  
 Erläutert, wie VSPackages erstellt und installiert und wie Benutzer unterstützen, die Ausführen mehrerer Versionen der [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] zur gleichen Zeit.


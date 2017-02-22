---
title: "Installieren von VSPackages mit Windows Installer | Microsoft Docs"
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
  - "[Visual Studio SDK]-Installation mit Windows Installer"
  - "Bereitstellen von VSPackages"
ms.assetid: 41d2c72c-0a97-4fcd-b3aa-33a8d3aa962a
caps.latest.revision: 30
caps.handback.revision: 30
ms.author: "gregvanl"
manager: "ghogen"
---
# Installieren von VSPackages mit Windows Installer
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Die Integration VSPackages in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] erfordert mehr als nur Dateien auf den Computer eines Benutzers kopieren.  Das Installationsprogramm VSPackages muss ein VSPackage und ihre abhängigen Dateien installieren und registrieren und in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]integrieren.  VSPackages Integrationsfunktionen kann z. B. das Anzeigen eines Symbols für das Dialogfeld Info und Begrüßungsbildschirm [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nutzen.  
  
 Microsoft Windows Installer\-Dateien ist die empfohlene Methode, die VSPackages zu verteilen.  Benutzerfreundliche von Windows Installer\-Paketen können auf jedes Windows\-Betriebssystem ausgeführt werden, das von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]unterstützt wird.  Weitere Informationen finden Sie unter [Windows Installer](http://msdn.microsoft.com/de-de/121be21b-b916-43e2-8f10-8b080516d2a0).  
  
## In diesem Abschnitt  
 [Windows Installer\-Grundlagen](../../extensibility/internals/windows-installer-basics.md)  
 Bietet eine Übersicht über den Windows Installer\-Dateien bereit.  
  
 [VSPackage\-Setup\-Szenarien](../../extensibility/internals/vspackage-setup-scenarios.md)  
 Erläutert verschiedene Möglichkeiten, die Sie parallele Installationen von VSPackages und des [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]unterstützen können.  
  
 [Erstellen ein Windows Installer\-Paket](../../extensibility/internals/authoring-a-windows-installer-package.md)  
 Bietet eine Übersicht über die typischen Schritte, die alle Installationsprogramme in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]VSPackages ausführen, um ordnungsgemäß zu installieren und zu integrieren.  
  
 [Ermitteln von Systemanforderungen](../../extensibility/internals/detecting-system-requirements.md)  
 Beschreibt, wie ein Installationsprogramm [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] und seine Komponenten und Löschungen setup erkennen kann, wenn VSPackage\-Bedingungen nicht erfüllt werden.  
  
 [Verwaltung von Komponenten](../../extensibility/internals/component-management.md)  
 Erläutert, wie ein Installationsprogramm entwickelt, das die Integrität von früheren Versionen Produkt aufweist.  
  
 [Wählen das Installationsverzeichnis für ein VSPackage](../../extensibility/internals/choosing-the-installation-directory-for-a-vspackage.md)  
 Fasst die Optionen zum Suchen von VSPackages zusammen.  
  
 [VSPackage\-Registrierung](../../extensibility/internals/vspackage-registration.md)  
 Erläutert, wie VSPackages bei der Installation SELF Registrierung registriert werden und warum eine ungültige Idee ist.  
  
 [Bereitstellen von Projekttypen](../../extensibility/internals/deploying-project-types.md)  
 Erläutert, wie Sie den neuen Projekttyp aggregator für Projekttypen mit verwaltetem Code verwendet.  
  
 [Gewusst wie: Generieren von Informationen in der Registrierung für ein Installationsprogramm](../../extensibility/internals/how-to-generate-registry-information-for-an-installer.md)  
 Erläutert, wie ein RegPkg.exe Registrierungsdaten manifest für verwaltete VSPackages zu generieren.  
  
 [Befehle, die nach der Installation ausgeführt werden müssen](../../extensibility/internals/commands-that-must-be-run-after-installation.md)  
 Erläutert, wie die Befehle nach der Installation ausgeführt wird, VSPackages in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]zu integrieren.  
  
 [Deinstallieren ein VSPackage mit Windows Installer](../../extensibility/internals/uninstalling-a-vspackage-with-windows-installer.md)  
 Beschreibt die Schritte, die das Installationsprogramm ausgeführt werden muss, wenn Benutzer ein VSPackage deinstallieren.  
  
## Verwandte Abschnitte  
 [Installieren von VSPackages](../../misc/installing-vspackages.md)  
 Erläutert, wie VSPackages erstellt und installiert und wie Benutzer unterstützt, die mehrere Versionen von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] gleichzeitig ausgeführt werden.
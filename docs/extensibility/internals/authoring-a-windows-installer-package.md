---
title: "Erstellen ein Windows Installer-Paket | Microsoft Docs"
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
  - "MSI-Dateien, VSPackages"
  - "MSI-Dateien, die VSPackages"
ms.assetid: 0ce7c21d-0d3f-47fe-a0bb-eed506e32609
caps.latest.revision: 20
caps.handback.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
---
# Erstellen ein Windows Installer-Paket
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Daten auf den Laufwerken des Windows Installer\-Modells. Statt eines prozeduralen Skripts zum Kopieren von Dateien und Registrierungseinträge schreiben, erstellen z. B. Sie Zeilen und Spalten in Datenbanktabellen, die Datei\- und Registrierungsvirtualisierung Daten enthalten können.  
  
## Datenbankeinträge  
 Um ein VSPackage zu installieren, muss Windows Installer\-Paket\-Datenbankeinträge für die folgenden Aufgaben enthalten:  
  
-   Suchen Sie das System, um die Versionen suchen [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Ihr VSPackage unterstützt \(mithilfe von Windows Installer\-Tabellen, die AppSearch, CompLocator, RegLocator, DrLocator und Signatur enthalten\).  
  
-   Die Installation Abbrechen, wenn keine unterstützte Version von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] installiert ist oder wenn ein anderes System\-Anforderung des VSPackage nicht erfüllt ist \(mithilfe der LaunchCondition\-Tabelle\).  
  
-   Installieren Sie das VSPackage und abhängigen Dateien \(mit dem Verzeichnis, Komponente und File\-Tabellen\).  
  
-   Fügen Sie entsprechende Informationen für das VSPackage in die Registrierung \(mithilfe der Tabelle Registry hinzu\).  
  
-   Integrieren des VSPackage in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] durch Aufrufen von **devenv.exe \/setup** \(verwenden die CustomAction\-Tabelle\).  
  
 Weitere Informationen finden Sie unter [Windows Installer](http://msdn.microsoft.com/library/cc185688\(VS.85\).aspx).  
  
## Setup\-Tools  
 Eine Reihe von Drittanbieter\-Setup\-Tools stellen eine Entwicklungsumgebung für Windows Installer\-Pakete. Zwei kostenlose Tools sind die folgenden:  
  
-   InstallShield Limited Edition  
  
     Sie erhalten eine eingeschränkte Version von InstallShield mithilfe von Visual Studio **Neues Projekt** Dialogfeld. Erweitern Sie **Andere Projekttypen** und wählen Sie dann **Setup und Bereitstellung**. Wählen Sie die InstallShield\-Vorlage.  
  
-   Windows Installer XML Toolset  
  
     Das Toolset erstellt Windows Installer\-Pakete aus XML\-Quelldateien. Das Toolset ist ein Microsoft\-Open\-Source\-Projekt. Sie können den Quellcode und ausführbare Dateien aus herunterladen [http:\/\/sourceforge.net\/projects\/wix](http://sourceforge.net/projects/wix).  
  
 Für kommerzielle Produkte, die Integration in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] mithilfe der [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], finden Sie unter [http:\/\/visualstudiogallery.com](http://visualstudiogallery.com/).  
  
## Siehe auch  
 [Installieren von VSPackages mit Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
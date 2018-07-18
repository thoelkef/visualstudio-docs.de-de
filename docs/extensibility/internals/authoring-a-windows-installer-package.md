---
title: Erstellen ein Windows Installer-Paket | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- .msi files, VSPackages
- msi files, VSPackages
ms.assetid: 0ce7c21d-0d3f-47fe-a0bb-eed506e32609
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 215e1496d35059448cf11457658b7d1270b5677d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31127925"
---
# <a name="authoring-a-windows-installer-package"></a>Erstellen ein Windows Installer-Paket
Daten auf den Laufwerken des Windows Installer-Modells. Anstatt ein prozeduralen Skript zum Kopieren von Dateien und Schreiben Registrierungseinträge geschrieben, dienstautor z. B. Zeilen und Spalten in Datenbanktabellen, die Datei- und Registrierungsberechtigungen Daten enthalten.  
  
## <a name="database-entries"></a>Datenbankeinträge  
 Um ein VSPackage zu installieren, darf ein Windows Installer-Paket Datenbankeinträge, um die folgenden Aufgaben ausführen:  
  
-   Suchen Sie das System, um die Versionen zu suchen [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Ihr VSPackage unterstützt (mit dem Windows Installer-Tabellen, die AppSearch, CompLocator RegLocator, DrLocator und Signatur enthalten).  
  
-   Brechen Sie die Installation aus, wenn keine unterstützte Version von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] installiert ist oder wenn ein anderes System-Anforderung des VSPackage nicht erfüllt wird (unter Verwendung der LaunchCondition-Tabelle).  
  
-   Installieren Sie das VSPackage und abhängigen Dateien (mit dem Verzeichnis, Komponente und File-Tabellen).  
  
-   Fügen Sie entsprechende Informationen für das VSPackage in die Registrierung (mithilfe der Tabelle Registry) hinzu.  
  
-   Integrieren Sie das VSPackage in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] durch Aufrufen von **devenv.exe/Setup /** (verwenden die CustomAction-Tabelle).  
  
 Weitere Informationen finden Sie unter [Windows Installer](http://msdn.microsoft.com/library/cc185688\(VS.85\).aspx).  
  
## <a name="setup-tools"></a>Setup-Tools  
 Eine Vielzahl von Drittanbieter-Setup-Tools bieten eine Entwicklungsumgebung für Windows Installer-Pakete. Zwei kostenlose Tools lauten wie folgt:  
  
-   InstallShield Limited Edition  
  
     Sie erhalten eine eingeschränkte Version von InstallShield mithilfe von Visual Studio **neues Projekt** Dialogfeld. Erweitern Sie **andere Projekttypen** und wählen Sie dann **Setup und Bereitstellung**. Wählen Sie die InstallShield-Vorlage.  
  
-   Windows Installer XML Toolset  
  
     Das Toolset erstellt Windows Installer-Pakete aus XML-Quelldateien. Das Toolset ist eine Open-Source-Projekte von Microsoft. Sie können den Quellcode und ausführbare Dateien aus [ http://sourceforge.net/projects/wix ](http://sourceforge.net/projects/wix).  
  
 Für kommerzielle Produkte, die Integration in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] mithilfe der [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], finden Sie unter [ http://visualstudiogallery.com ](http://visualstudiogallery.com/).  
  
## <a name="see-also"></a>Siehe auch  
 [Installieren von VSPackages mit Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
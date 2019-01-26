---
title: Erstellen eines Windows Installer-Pakets | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .msi files, VSPackages
- msi files, VSPackages
ms.assetid: 0ce7c21d-0d3f-47fe-a0bb-eed506e32609
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 93c69b2fba2bc866673b294a4f5c975a6ce3eb6a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55020944"
---
# <a name="author-a-windows-installer-package"></a>Erstellen Sie ein Windows Installer-Paket
Daten auf den Laufwerken des Windows Installer-Modells. Statt eines prozeduralen-Skripts zum Kopieren von Dateien und Registrierungseinträge schreiben, erstellen z. B. Sie Zeilen und Spalten in Tabellen, die Datei- und Daten enthalten können.  
  
## <a name="database-entries"></a>Datenbankeinträge  
Um ein VSPackage zu installieren, darf ein Windows Installer-Paket-Datenbankeinträge, um die folgenden Aufgaben ausführen:  
  
- Suchen Sie das System, um die Versionen zu suchen [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Ihr VSPackage unterstützt werden (mithilfe von Windows Installer-Tabellen, die AppSearch, CompLocator, RegLocator, DrLocator und Signatur enthalten).  
  
- Die Installation abzubrechen, wenn keine unterstützte Version von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] installiert ist oder wenn eine andere Systemanforderungen des VSPackage nicht erfüllt ist (unter Verwendung der LaunchCondition-Tabelle).  
  
- Installieren Sie das VSPackage und abhängigen Dateien (mit dem Verzeichnis, Komponente und File-Tabellen).  
  
- Fügen Sie entsprechende Informationen für das VSPackage in der Registrierung (unter Verwendung der Tabelle Registry) hinzu.  
  
- Integrieren Sie das VSPackage in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] durch Aufrufen von **devenv.exe/Setup /** (unter Verwendung der CustomAction-Tabelle).  
  
Weitere Informationen finden Sie unter [Windows Installer](/windows/desktop/Msi/windows-installer-portal).
  
## <a name="setup-tools"></a>Setup-tools  
Eine Vielzahl von Drittanbieter-Setup-Tools bieten eine Entwicklungsumgebung für Windows Installer-Pakete. Die folgenden kostenlosen Tools sind verfügbar:  
  
- InstallShield Limited-edition  
  
   Sie erhalten eine eingeschränkte Version von InstallShield über Visual Studio **neues Projekt** Dialogfeld. Erweitern Sie **andere Projekttypen** und wählen Sie dann **Setup und Bereitstellung**. Wählen Sie die InstallShield-Vorlage.  
  
- Windows Installer XML toolset  
  
   Das Windows Installer XML (WiX)-Toolset erstellt Windows Installer-Pakete aus XML-Quelldateien. Das WiX-Toolset ist eine Open-Source-Projekte von Microsoft. Sie können den Quellcode und die ausführbaren Dateien von [Wix-Toolset](http://sourceforge.net/projects/wix).  
  
   Für kommerzielle Produkte, die Integration in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] mithilfe der [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], finden Sie unter [ http://visualstudiogallery.com ](http://visualstudiogallery.com/).  
  
## <a name="see-also"></a>Siehe auch  
 [Installieren von VSPackages mit Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
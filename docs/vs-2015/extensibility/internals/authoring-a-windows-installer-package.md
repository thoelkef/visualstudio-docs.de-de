---
title: Erstellen eines Windows Installer-Pakets | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- .msi files, VSPackages
- msi files, VSPackages
ms.assetid: 0ce7c21d-0d3f-47fe-a0bb-eed506e32609
caps.latest.revision: 21
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a9b56ea9120e3cbee18d8018420a94748dc52eec
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47509420"
---
# <a name="authoring-a-windows-installer-package"></a>Erstellen eines Windows Installer-Pakets
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [erstellen ein Windows Installer-Paket](https://docs.microsoft.com/visualstudio/extensibility/internals/authoring-a-windows-installer-package).  
  
Daten auf den Laufwerken des Windows Installer-Modells. Statt eines prozeduralen-Skripts zum Kopieren von Dateien und Registrierungseinträge schreiben, erstellen z. B. Sie Zeilen und Spalten in Tabellen, die Datei- und Daten enthalten können.  
  
## <a name="database-entries"></a>Datenbankeinträge  
 Um ein VSPackage zu installieren, darf ein Windows Installer-Paket-Datenbankeinträge, um die folgenden Aufgaben ausführen:  
  
-   Suchen Sie das System, um die Versionen zu suchen [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Ihr VSPackage unterstützt werden (mithilfe von Windows Installer-Tabellen, die AppSearch, CompLocator, RegLocator, DrLocator und Signatur enthalten).  
  
-   Die Installation abzubrechen, wenn keine unterstützte Version von [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] installiert ist oder wenn eine andere Systemanforderungen des VSPackage nicht erfüllt ist (unter Verwendung der LaunchCondition-Tabelle).  
  
-   Installieren Sie das VSPackage und abhängigen Dateien (mit dem Verzeichnis, Komponente und File-Tabellen).  
  
-   Fügen Sie entsprechende Informationen für das VSPackage in der Registrierung (unter Verwendung der Tabelle Registry) hinzu.  
  
-   Integrieren Sie das VSPackage in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] durch Aufrufen von **devenv.exe/Setup /** (unter Verwendung der CustomAction-Tabelle).  
  
 Weitere Informationen finden Sie unter [Windows Installer](http://msdn.microsoft.com/library/cc185688\(VS.85\).aspx).  
  
## <a name="setup-tools"></a>Setup-Tools  
 Eine Vielzahl von Drittanbieter-Setup-Tools bieten eine Entwicklungsumgebung für Windows Installer-Pakete. Zwei kostenlose Tools lauten wie folgt:  
  
-   InstallShield Limited Edition  
  
     Sie erhalten eine eingeschränkte Version von InstallShield über Visual Studio **neues Projekt** Dialogfeld. Erweitern Sie **andere Projekttypen** und wählen Sie dann **Setup und Bereitstellung**. Wählen Sie die InstallShield-Vorlage.  
  
-   Windows Installer XML Toolset  
  
     Das Toolset erstellt Windows Installer-Pakete aus XML-Quelldateien. Das Toolset ist eine Open-Source-Projekte von Microsoft. Sie können den Quellcode und die ausführbaren Dateien von [ http://sourceforge.net/projects/wix ](http://sourceforge.net/projects/wix).  
  
 Für kommerzielle Produkte, die Integration in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] mithilfe der [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)], finden Sie unter [ http://visualstudiogallery.com ](http://visualstudiogallery.com/).  
  
## <a name="see-also"></a>Siehe auch  
 [Installieren von VSPackages mit Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)


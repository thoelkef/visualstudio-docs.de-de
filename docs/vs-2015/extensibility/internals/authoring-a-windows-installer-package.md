---
title: Erstellen eines Windows Installer Pakets | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- .msi files, VSPackages
- msi files, VSPackages
ms.assetid: 0ce7c21d-0d3f-47fe-a0bb-eed506e32609
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 58529dabbb52ceb751c67be24beb1d21285a1de6
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2019
ms.locfileid: "74301135"
---
# <a name="authoring-a-windows-installer-package"></a>Erstellen eines Windows Installer-Pakets
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Daten steuern das Windows Installer Modell. Anstatt ein prozedurales Skript zum Kopieren von Dateien und zum Schreiben von Registrierungs Einträgen zu schreiben, schreiben Sie z. b. Zeilen und Spalten in Datenbanktabellen, die Datei-und Registrierungsdaten enthalten.  
  
## <a name="database-entries"></a>Datenbankeinträge  
 Um ein VSPackage zu installieren, muss ein Windows Installer Paketdaten Bank Einträge enthalten, um die folgenden Aufgaben auszuführen:  
  
- Durchsuchen Sie das System, um die Versionen von [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], die das VSPackage unterstützt (mithilfe Windows Installer Tabellen, die AppSearch, complocator, reglocator, drlocator und Signature enthalten) zu suchen.  
  
- Brechen Sie die Installation ab, wenn keine unterstützte Version von [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] installiert ist oder eine andere System Anforderung des VSPackage nicht erfüllt wird (mithilfe der LaunchCondition-Tabelle).  
  
- Installieren Sie das VSPackage und abhängige Dateien (mithilfe der Verzeichnis-, Komponenten-und Datei Tabellen).  
  
- Fügen Sie die entsprechenden Informationen für das VSPackage zur Registrierung hinzu (mithilfe der Registrierungs Tabelle).  
  
- Integrieren Sie das VSPackage in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], indem Sie " **devenv. exe/Setup** " aufrufen (mithilfe der Tabelle "CustomAction").  
  
  Weitere Informationen finden Sie unter [Windows Installer](https://msdn.microsoft.com/library/cc185688\(VS.85\).aspx).  
  
## <a name="setup-tools"></a>Setup Tools  
 Eine Reihe von Setup Tools von Drittanbietern bieten eine Entwicklungsumgebung für Windows Installer Pakete. Zwei kostenlose Tools sind die folgenden:  
  
- InstallShield Limited Edition  
  
   Sie können eine begrenzte Version von InstallShield über das Visual Studio-Dialogfeld " **Neues Projekt** " erhalten. Erweitern Sie **andere Projekttypen** , und wählen Sie dann **Setup und Bereitstellung**aus. Wählen Sie die Vorlage InstallShield aus.  
  
- Windows Installer XML Toolset  
  
   Das Toolset erstellt Windows Installer Pakete aus XML-Quelldateien. Das Toolset ist ein Microsoft-Open-Source-Projekt. Sie können den Quellcode und ausführbare Dateien aus [http://sourceforge.net/projects/wix](https://sourceforge.net/projects/wix/)herunterladen.  
  
  Informationen zu kommerziellen Produkten, die mithilfe des [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)]in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] integriert werden, finden Sie unter [https://marketplace.visualstudio.com/](https://marketplace.visualstudio.com/).  
  
## <a name="see-also"></a>Siehe auch  
 [Installieren von VSPackages mit Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)

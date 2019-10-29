---
title: Erstellen eines Windows Installer Pakets | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .msi files, VSPackages
- msi files, VSPackages
ms.assetid: 0ce7c21d-0d3f-47fe-a0bb-eed506e32609
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aa967b5f23ff9f4e5afa67b9b1cb4e83707616c6
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/28/2019
ms.locfileid: "72982230"
---
# <a name="author-a-windows-installer-package"></a>Erstellen eines Windows Installer Pakets
Daten steuern das Windows Installer Modell. Anstatt ein prozedurales Skript zum Kopieren von Dateien und zum Schreiben von Registrierungs Einträgen zu schreiben, schreiben Sie z. b. Zeilen und Spalten in Datenbanktabellen, die Datei-und Registrierungsdaten enthalten.

## <a name="database-entries"></a>Datenbankeinträge
Um ein VSPackage zu installieren, muss ein Windows Installer Paketdaten Bank Einträge enthalten, um die folgenden Aufgaben auszuführen:

- Durchsuchen Sie das System, um die Versionen von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], die das VSPackage unterstützt (mithilfe Windows Installer Tabellen, die AppSearch, complocator, reglocator, drlocator und Signature enthalten) zu suchen.

- Brechen Sie die Installation ab, wenn keine unterstützte Version von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] installiert ist oder eine andere System Anforderung des VSPackage nicht erfüllt wird (mithilfe der LaunchCondition-Tabelle).

- Installieren Sie das VSPackage und abhängige Dateien (mithilfe der Verzeichnis-, Komponenten-und Datei Tabellen).

- Fügen Sie die entsprechenden Informationen für das VSPackage zur Registrierung hinzu (mithilfe der Registrierungs Tabelle).

- Integrieren Sie das VSPackage in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], indem Sie " **devenv. exe/Setup** " aufrufen (mithilfe der Tabelle "CustomAction").

Weitere Informationen finden Sie unter [Windows Installer](/windows/desktop/Msi/windows-installer-portal).

## <a name="setup-tools"></a>Setup Tools
Eine Reihe von Setup Tools von Drittanbietern bieten eine Entwicklungsumgebung für Windows Installer Pakete. Die folgenden kostenlosen Tools sind verfügbar:

- InstallShield Limited Edition

   Sie können eine begrenzte Version von InstallShield über das Visual Studio-Dialogfeld " **Neues Projekt** " erhalten. Erweitern Sie **andere Projekttypen** , und wählen Sie dann **Setup und Bereitstellung**aus. Wählen Sie die Vorlage InstallShield aus.

- Windows Installer XML-Toolset

   Das WiX-Toolset (Windows Installer XML) erstellt Windows Installer Pakete aus XML-Quelldateien. Das WiX-Toolset ist ein Microsoft-Open-Source-Projekt. Sie können den Quellcode und ausführbare Dateien aus dem [WiX-Toolset](https://sourceforge.net/projects/wix/)herunterladen.

   Informationen zu kommerziellen Produkten, die mithilfe des [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integriert werden, finden Sie unter [Visual Studio Marketplace](https://marketplace.visualstudio.com/).

## <a name="see-also"></a>Siehe auch
- [Installieren von VSPackages mit Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
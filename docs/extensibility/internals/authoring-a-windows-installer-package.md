---
title: Erstellen eines Windows Installer-Pakets | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .msi files, VSPackages
- msi files, VSPackages
ms.assetid: 0ce7c21d-0d3f-47fe-a0bb-eed506e32609
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 03d30c0e2b3b375e6e0efedddd3a017fbfb8646a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710038"
---
# <a name="author-a-windows-installer-package"></a>Erstellen eines Windows Installer-Pakets
Daten werden für das Windows Installer-Modell verwendet. Anstatt beispielsweise ein prozedurales Skript zum Kopieren von Dateien und Schreiben von Registrierungseinträgen zu schreiben, erstellen Sie Zeilen und Spalten in Datenbanktabellen, die Datei- und Registrierungsdaten enthalten.

## <a name="database-entries"></a>Datenbankeinträge
Um ein VSPackage zu installieren, muss ein Windows Installer-Paket Datenbankeinträge enthalten, um die folgenden Aufgaben ausführen zu können:

- Durchsuchen Sie das System, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] um die Versionen Ihrer VSPackage-Unterstützung zu finden (mit Windows Installer-Tabellen, die AppSearch, CompLocator, RegLocator, DrLocator und Signature enthalten).

- Brechen Sie die Installation [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ab, wenn keine unterstützte Version von installiert ist oder wenn eine andere Systemanforderung des VSPackage nicht erfüllt ist (mit der Tabelle LaunchCondition).

- Installieren Sie das VSPackage und die abhängigen Dateien (mit den Verzeichnis-, Komponenten- und Dateitabellen).

- Fügen Sie der Registrierung (mit der Registrierungstabelle) geeignete Informationen für das VSPackage hinzu.

- Integrieren Sie das [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] VSPackage in, indem Sie **devenv.exe /setup** aufrufen (mit der Tabelle CustomAction).

Weitere Informationen finden Sie unter [Windows Installer](/windows/desktop/Msi/windows-installer-portal).

## <a name="setup-tools"></a>Setup-Tools
Eine Vielzahl von Setup-Tools von Drittanbietern stellen eine Entwicklungsumgebung für Windows Installer-Pakete bereit. Folgende kostenlose Tools stehen zur Verfügung:

- InstallShield Limited Edition

   Sie können eine eingeschränkte Version von InstallShield über das Dialogfeld Visual Studio **New Project** abrufen. Erweitern **Sie andere Projekttypen,** und wählen Sie dann **Setup und Bereitstellung**aus. Wählen Sie die InstallShield-Vorlage aus.

- Windows Installer XML-Toolset

   Das Windows Installer XML (WiX)-Toolset erstellt Windows Installer-Pakete aus XML-Quelldateien. Das WiX-Toolset ist ein Open-Source-Projekt von Microsoft. Sie können den Quellcode und die ausführbaren Dateien von [Wix Toolset](https://sourceforge.net/projects/wix/)herunterladen.

   Für kommerzielle Produkte, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] die [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]mithilfe der integriert werden, finden Sie unter [Visual Studio Marketplace](https://marketplace.visualstudio.com/).

## <a name="see-also"></a>Weitere Informationen
- [Installieren von VSPackages mit Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)

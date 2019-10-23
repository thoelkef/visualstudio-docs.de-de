---
title: Deinstallieren eines VSPackage mit Windows Installer | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- packages, uninstalling
- VSPackages, uninstalling
- uninstalling VSPackages
ms.assetid: c4575ac7-82da-4af8-a375-ea756a101fbf
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a8e92937e848d124c18dc91b9bdfa0f020f27f20
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72722130"
---
# <a name="uninstalling-a-vspackage-with-windows-installer"></a>Deinstallieren eines VSPackage mit Windows Installer
Windows Installer können das VSPackage zum größten Teil deinstallieren, indem Sie einfach "rückgängig machen", was für die Installation des VSPackage geschehen ist. Die benutzerdefinierten Aktionen, die in [Befehlen erläutert werden, die nach der Installation ausgeführt werden müssen,](../../extensibility/internals/commands-that-must-be-run-after-installation.md) müssen auch nach der Deinstallation ausgeführt werden. Da die Aufrufe von "devenv. exe" direkt vor der "InstallFinalize Standard"-Aktion für die Installation und Deinstallation auftreten, dienen die Tabelleneinträge "CustomAction" und "InstallExecuteSequence" beiden Fällen.

> [!NOTE]
> Führen Sie `devenv /setup` nach der Deinstallation eines MSI-Pakets aus.

 Wenn Sie einem Windows Installer Paket benutzerdefinierte Aktionen hinzufügen, müssen Sie diese Aktionen als allgemeine Regel während der deinstalstallation und des Rollbacks behandeln. Wenn Sie benutzerdefinierte Aktionen hinzufügen, um Ihr VSPackage selbst zu registrieren, müssen Sie z. b. benutzerdefinierte Aktionen hinzufügen, um die Registrierung aufzuheben.

> [!NOTE]
> Es ist möglich, dass ein Benutzer das VSPackage installiert und dann die Versionen von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] deinstalliert, mit denen es integriert ist. Sie können sicherstellen, dass die Deinstallation des VSPackages in diesem Szenario funktioniert, indem Sie benutzerdefinierte Aktionen eliminieren, die Code mit Abhängigkeiten auf [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ausführen.

## <a name="handling-launch-conditions-at-uninstall-time"></a>Behandeln von Startbedingungen zum Zeitpunkt der Deinstallation
 Mit der Standardaktion LaunchConditions werden die Zeilen der LaunchCondition-Tabelle gelesen, um Fehlermeldungen anzuzeigen, wenn die Bedingungen nicht erfüllt werden. Wenn im allgemeinen Startbedingungen verwendet werden, um sicherzustellen, dass die Systemanforderungen erfüllt sind, können Sie die Startbedingungen während der deinstalstallation im allgemeinen überspringen, indem Sie die Bedingung (`NOT Installed`) der Zeile LaunchConditions der LaunchCondition-Tabelle hinzufügen.

 Eine Alternative besteht darin, `OR Installed` zum Starten von Bedingungen hinzuzufügen, die während der Installation nicht wichtig sind. Dadurch wird sichergestellt, dass die Bedingung bei der nicht Installation immer true ist, und daher wird die Fehlermeldung der Startbedingung nicht angezeigt.

> [!NOTE]
> `Installed` ist die Eigenschaft Windows Installer legt fest, wann das VSPackage bereits auf dem System installiert ist.

## <a name="see-also"></a>Siehe auch
- [Windows Installer](https://msdn.microsoft.com/library/187d8965-c79d-4ecb-8689-10930fa8b3b5)
- [Ermitteln von Systemanforderungen](../../extensibility/internals/detecting-system-requirements.md)
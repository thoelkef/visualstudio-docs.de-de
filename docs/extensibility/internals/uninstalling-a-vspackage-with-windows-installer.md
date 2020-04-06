---
title: Deinstallieren eines VSPackage mit Windows Installer | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- packages, uninstalling
- VSPackages, uninstalling
- uninstalling VSPackages
ms.assetid: c4575ac7-82da-4af8-a375-ea756a101fbf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fee88e895d40d42114eaf53422503524594b485f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704279"
---
# <a name="uninstalling-a-vspackage-with-windows-installer"></a>Deinstallieren eines VSPackage mit Windows Installer
Zum größten Teil kann Windows Installer Ihr VSPackage deinstallieren, indem es einfach "rückgängig macht", was es getan hat, um Ihr VSPackage zu installieren. Die benutzerdefinierten [Aktionen,](../../extensibility/internals/commands-that-must-be-run-after-installation.md) die in Befehlen behandelt werden müssen, die nach der Installation ausgeführt werden müssen, müssen auch nach einer Deinstallation ausgeführt werden. Da die Aufrufe von devenv.exe kurz vor der InstallFinalize-Standardaktion für die Installation und Deinstallation erfolgen, dienen die Tabelleneinträge CustomAction und InstallExecuteSequence beiden Fällen.

> [!NOTE]
> Führen `devenv /setup` Sie aus, nachdem Sie ein MSI-Paket deinstalliert haben.

 Wenn Sie einem Windows Installer-Paket benutzerdefinierte Aktionen hinzufügen, müssen Sie diese Aktionen in der Regel während der Deinstallation und des Rollbacks behandeln. Wenn Sie z. B. benutzerdefinierte Aktionen zur Selbstregistrierung Ihres VSPackage hinzufügen, müssen Sie auch benutzerdefinierte Aktionen hinzufügen, um die Registrierung zu aufheben.

> [!NOTE]
> Es ist möglich, dass ein Benutzer Ihr VSPackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] installiert und dann die Versionen deinstalliert, mit denen es integriert ist. Sie können sicherstellen, dass die Deinstallation Ihres VSPackage in diesem Szenario funktioniert, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]indem Sie benutzerdefinierte Aktionen eliminieren, die Code mit Abhängigkeiten von ausführen.

## <a name="handling-launch-conditions-at-uninstall-time"></a>Handhabung der Startbedingungen zur Deinstallationszeit
 Die LaunchConditions-Standardaktion liest die Zeilen der LaunchCondition-Tabelle, um Fehlermeldungen anzuzeigen, wenn die Bedingungen nicht erfüllt sind. Da die Startbedingungen im Allgemeinen verwendet werden, um sicherzustellen, dass die Systemanforderungen `NOT Installed`erfüllt sind, können Sie die Startbedingungen während der Deinstallation im Allgemeinen überspringen, indem Sie die Bedingung , zur Zeile LaunchConditions der Tabelle LaunchCondition hinzufügen.

 Eine Alternative besteht `OR Installed` darin, Startbedingungen hinzuzufügen, die während der Deinstallation nicht wichtig sind. Dadurch wird sichergestellt, dass die Bedingung während der Deinstallation immer wahr ist und daher die Fehlermeldung "Startbedingung" nicht angezeigt wird.

> [!NOTE]
> `Installed`ist die Eigenschaft, die Windows Installer festlegt, wenn erkannt wird, dass Ihr VSPackage bereits auf dem System installiert wurde.

## <a name="see-also"></a>Weitere Informationen
- [Windows Installer](https://msdn.microsoft.com/library/187d8965-c79d-4ecb-8689-10930fa8b3b5)
- [Ermitteln von Systemanforderungen](../../extensibility/internals/detecting-system-requirements.md)

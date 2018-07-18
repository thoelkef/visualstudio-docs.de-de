---
title: Deinstallieren eine VSPackage mit Windows Installer | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- packages, uninstalling
- VSPackages, uninstalling
- uninstalling VSPackages
ms.assetid: c4575ac7-82da-4af8-a375-ea756a101fbf
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d8a62692003b26afcd5b7814bdc03320fa1c453a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31141095"
---
# <a name="uninstalling-a-vspackage-with-windows-installer"></a>Deinstallieren eine VSPackage mit Windows Installer
Meistens, Windows Installer können deinstallieren das VSPackage nur durch "Rückgängig", was es geschehen ist, um Ihr VSPackage zu installieren. Die benutzerdefinierten Aktionen, die in beschriebenen [Befehle, muss werden führen Sie nach der Installation](../../extensibility/internals/commands-that-must-be-run-after-installation.md) nach einer Deinstallation ebenfalls ausgeführt werden muss. Da die Aufrufe von devenv.exe unmittelbar vor der InstallFinalize Standardaktionen für die Installation und Deinstallation ausgeführt werden, dienen die CustomAction und InstallExecuteSequence Tabelleneinträge beide Fälle.  
  
> [!NOTE]
>  Führen Sie `devenv /setup` nach der Deinstallation eines MSI-Pakets.  
  
 Als allgemeine Regel Wenn Sie ein Windows Installer-Paket, benutzerdefinierte Aktionen hinzufügen müssen diese Aktionen während der Deinstallation und Rollback behandelt werden. Wenn Sie benutzerdefinierte Aktionen zum Registrieren Ihres VSPackages hinzufügen, z. B. müssen Sie die benutzerdefinierte Aktionen zum aufheben zu hinzufügen.  
  
> [!NOTE]
>  Es ist möglich, dass ein Benutzer auf Ihr VSPackage zu installieren und deinstallieren Sie die Versionen der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] mit dem er integriert wird. Können Sie sicherstellen, dass Ihr VSPackage Deinstallation in diesem Szenario funktioniert durch die Beseitigung von benutzerdefinierter Aktionen, die Code mit Abhängigkeiten ausgeführt [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="handling-launch-conditions-at-uninstall-time"></a>Startbedingungen zur Behandlung der Deinstallation  
 Die Standardaktionen LaunchConditions liest die Zeilen der Tabelle LaunchCondition Fehler angezeigt werden soll, wenn die Bedingung nicht erfüllt sind. Wie Startbedingungen in der Regel verwendet werden, um sicherzustellen, dass die Systemanforderungen erfüllt sind, können Sie in der Regel Startbedingungen während der Deinstallation durch Hinzufügen der Bedingung überspringen `NOT Installed`, auf die LaunchConditions Zeile der Tabelle LaunchCondition.  
  
 Eine Alternative besteht darin, hinzufügen `OR Installed` um Bedingungen zu starten, die bei der Deinstallation nicht wichtig sind. Hierdurch wird sichergestellt, dass die Bedingung wird immer "true" bei der Deinstallation und Start Bedingung Fehlermeldung wird nicht angezeigt.  
  
> [!NOTE]
>  `Installed` ist die Eigenschaft, die Windows Installer legt fest, wenn er erkennt, dass Ihr VSPackage bereits auf dem System installiert wurde.  
  
## <a name="see-also"></a>Siehe auch  
 [Windows Installer](http://msdn.microsoft.com/en-us/187d8965-c79d-4ecb-8689-10930fa8b3b5)   
 [Ermitteln von Systemanforderungen](../../extensibility/internals/detecting-system-requirements.md)
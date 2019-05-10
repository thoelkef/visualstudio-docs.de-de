---
title: Deinstallieren eines VSPackage mit Windows Installer | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- packages, uninstalling
- VSPackages, uninstalling
- uninstalling VSPackages
ms.assetid: c4575ac7-82da-4af8-a375-ea756a101fbf
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6175b89db774598463d1f8ffaa03057ecb50a69b
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63441183"
---
# <a name="uninstalling-a-vspackage-with-windows-installer"></a>Deinstallieren eines VSPackage mit Windows Installer
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Zum größten Teil, Windows Installer können deinstallieren, das VSPackage nur durch "rückgängig zu machen, was dabei durchgeführt wurde, um Ihr VSPackage zu installieren. Die benutzerdefinierten Aktionen, die in beschriebenen [Befehle, muss sein ausführen nach der Installation](../../extensibility/internals/commands-that-must-be-run-after-installation.md) muss nach einer Deinstallation ebenfalls ausgeführt werden. Da die Aufrufe von devenv.exe direkt vor die InstallFinalize Standardaktionen für die Installation und Deinstallation ausgeführt werden, dienen die CustomAction und InstallExecuteSequence Tabelleneinträge beiden Fällen.  
  
> [!NOTE]
> Führen Sie `devenv /setup` nach der Deinstallation eines MSI-Pakets.  
  
 Als allgemeine Regel Wenn Sie ein Windows Installer-Paket, benutzerdefinierte Aktionen hinzufügen müssen Sie diese Aktionen während der Deinstallation und Rollback behandeln. Wenn Sie benutzerdefinierte Aktionen zum Registrieren Ihres VSPackages hinzufügen, beispielsweise müssen Sie benutzerdefinierte Aktionen aus, um es zu Aufheben der Registrierung hinzufügen.  
  
> [!NOTE]
> Es ist möglich, dass ein Benutzer aus, um Ihr VSPackage zu installieren und deinstallieren Sie die Versionen der [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] mit der er integriert ist. Sie können, stellen Sie sicher, dass Ihre VSPackage Deinstallation in diesem Szenario funktioniert Gerätetreiberschnittstellen einzufügen, benutzerdefinierte Aktionen, die auf Code mit Abhängigkeiten ausgeführt [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
## <a name="handling-launch-conditions-at-uninstall-time"></a>Behandlung von Startbedingungen am Zeitpunkt der Deinstallation  
 Die Standardaktionen LaunchConditions liest die Zeilen der Tabelle LaunchCondition, Fehler angezeigt werden soll, wenn die Bedingungen nicht erfüllt sind. Wie Starten von Bedingungen in der Regel verwendet werden, um sicherzustellen, dass die Systemanforderungen erfüllt sind, können Sie in der Regel Startbedingungen bei der Deinstallation durch Hinzufügen der Bedingung, `NOT Installed`, auf die LaunchConditions Zeile der Tabelle LaunchCondition.  
  
 Eine Alternative besteht darin hinzufügen `OR Installed` zum Starten von Bedingungen, die bei der Deinstallation nicht wichtig sind. Damit wird sichergestellt, dass die Bedingung ist bei der Deinstallation immer "true", und die Fehlermeldung des Start-Bedingung wird nicht angezeigt.  
  
> [!NOTE]
> `Installed` ist die Eigenschaft, die Windows Installer legt fest, wenn er erkennt, dass das VSPackage auf dem System bereits installiert wurde.  
  
## <a name="see-also"></a>Siehe auch  
 [Windows Installer](http://msdn.microsoft.com/187d8965-c79d-4ecb-8689-10930fa8b3b5)   
 [Ermitteln von Systemanforderungen](../../extensibility/internals/detecting-system-requirements.md)

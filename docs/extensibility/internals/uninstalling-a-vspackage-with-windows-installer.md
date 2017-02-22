---
title: "Deinstallieren ein VSPackage mit Windows Installer | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Deinstallieren von Paketen"
  - "Deinstallieren von VSPackages"
  - "die Deinstallation von VSPackages"
ms.assetid: c4575ac7-82da-4af8-a375-ea756a101fbf
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# Deinstallieren ein VSPackage mit Windows Installer
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Zum größten Teil, Windows Installer können deinstallieren das VSPackage nur von "rückgängig zu machen, was dabei durchgeführt wurde, um das VSPackage zu installieren. Die benutzerdefinierten Aktionen erläutert [Befehle, die nach der Installation ausgeführt werden müssen](../../extensibility/internals/commands-that-must-be-run-after-installation.md) muss nach der Deinstallation ebenfalls ausgeführt werden. Da die Aufrufe von devenv.exe unmittelbar vor der standardmäßigen InstallFinalize\-Aktion für die Installation und Deinstallation ausgeführt werden, dienen die Tabelleneinträge CustomAction und InstallExecuteSequence beide Fälle.  
  
> [!NOTE]
>  Führen Sie `devenv /setup` nach der Deinstallation eines MSI\-Pakets.  
  
 Als allgemeine Regel Wenn Sie ein Windows Installer\-Paket, benutzerdefinierte Aktionen hinzufügen müssen Sie diese Aktionen während der Deinstallation und Rollback behandeln. Wenn Sie benutzerdefinierte Aktionen zum Registrieren Ihrer VSPackages hinzufügen, z. B. müssen Sie benutzerdefinierte Aktionen zum aufheben zu hinzufügen.  
  
> [!NOTE]
>  Es ist möglich, dass ein Benutzer das VSPackage installieren und deinstallieren Sie die Versionen der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] mit der er integriert ist. Sie können sicherstellen, dass Ihr VSPackage\-Deinstallation in diesem Szenario funktioniert durch Eliminierung von benutzerdefinierten Aktionen, die auf Code mit Abhängigkeiten ausgeführt [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## Behandlung von Startbedingungen bei der Deinstallation  
 Die standardmäßige LaunchConditions\-Aktion liest die Zeilen der Tabelle LaunchCondition Fehler angezeigt werden soll, wenn die Bedingung nicht erfüllt sind. Startbedingungen in der Regel verwendet werden, um sicherzustellen, dass das System erfüllt sind, können Sie im Allgemeinen Startbedingungen bei der Deinstallation durch Hinzufügen der Bedingung `NOT Installed`, in die LaunchConditions Zeile der Tabelle LaunchCondition.  
  
 Eine Alternative ist die hinzufügen `OR Installed` Bedingungen zu starten, die bei der Deinstallation nicht wichtig sind. Damit wird sichergestellt, dass die Bedingung wird immer true während der Deinstallation und Launch Bedingung Fehlermeldung wird nicht angezeigt.  
  
> [!NOTE]
>  `Installed` ist die Eigenschaft, die Windows Installer legt fest, wenn es erkennt, dass Ihr VSPackage bereits auf dem System installiert wurde.  
  
## Siehe auch  
 [Windows Installer](http://msdn.microsoft.com/de-de/187d8965-c79d-4ecb-8689-10930fa8b3b5)   
 [Ermitteln von Systemanforderungen](../../extensibility/internals/detecting-system-requirements.md)
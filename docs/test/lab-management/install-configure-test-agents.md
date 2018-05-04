---
title: Installieren von Test-Agents und Testcontrollern für Visual Studio
ms.date: 03/02/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- configure test agents, test lab
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 20570d0a2d0173ca2322cb6ab1e888c7335cb4c0
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="install-test-agents-and-test-controllers"></a>Installieren von Test-Agents und Testcontrollern

Für Testszenarios, die Visual Studio und Visual Studio Team Services (VSTS) oder Team Foundation Server (TFS) verwenden, benötigen Sie keinen Testcontroller. Agents für Visual Studio behandeln die Orchestrierung durch Kommunikation mit VSTS oder TFS. In einem möglichen Szenario führen Sie fortlaufende Tests für Build-und-Release-Workflows in VSTS oder TFS durch.

Sie könnten auch erwägen, ob es besser wäre, stattdessen [Build- oder Releaseverwaltung](use-build-or-rm-instead-of-lab-management.md) zu verwenden.

## <a name="system-requirements"></a>Systemanforderungen

| Element | Anforderungen |
| ---- | ------------ |
| **Agent** | Windows 10<br />Windows 8, Windows 8.1<br />Windows 7 Service Pack 1<br />Windows XP Service Pack 3<br />Windows Server 2012, Windows Server 2012 R2<br />Windows Server 2008 Release 2, Service Pack 1 |
| **Controller** | Windows 10<br />Windows 8, Windows 8.1<br />Windows 7 Service Pack 1<br />Windows Server 2012, Windows Server 2012 R2<br />Windows Server 2008 Release 2, Service Pack 1 |
| **.NET Framework** | .NET Framework 4.5 |

## <a name="install-the-test-controller-and-test-agents"></a>Installieren von Testcontroller und Test-Agents

Sie können Agents für Visual Studio 2017 von [visualStudio.com](https://www.visualstudio.com/downloads/?q=agents) herunterladen. Scrollen Sie auf der Seite nach unten, und suchen Sie nach *Agents für Visual Studio 2017*. Wählen Sie entweder *Agent* oder *Controller* aus, und klicken Sie dann auf *Herunterladen*. Führen Sie zum Installieren des Test-Agents oder -controllers die ausführbare Datei aus, die Sie heruntergeladen haben.

Sie können Agents für Visual Studio 2015 und Visual Studio 2013 von der Seite mit [älteren Downloads](https://www.visualstudio.com/vs/older-downloads/) herunterladen.

Diese Installer stehen als ISO-Dateien für die unkomplizierte Installation auf virtuellen Computern zur Verfügung.

## <a name="compatible-versions-of-tfs-microsoft-test-manager-the-test-controller-and-test-agent"></a>Kompatible Versionen von TFS, Microsoft Test Manager, Testcontroller und Test-Agent

Sie können verschiedene Versionen von TFS, Microsoft Test Manager (MTM), Testcontroller und Test-Agent entsprechend der folgenden Tabelle kombinieren:

| TFS | MTM mit Lab-Center | Controller | Agent |
| --- | -------------------------------------- | ---------- | ----- |
| 2017: Upgrade von 2015 oder Neuinstallation | 2017 | 2017 | 2017 |
| 2017: Upgrade von 2015 oder Neuinstallation | 2017 | 2013 Update 5 | 2013 Update 5 |
| 2017: Upgrade von 2015 oder Neuinstallation | 2015 | 2013 Update 5 | 2013 Update 5 |
| 2015: Upgrade von 2013 | 2013 | 2013 |2013 |
| 2015: Neuinstallation | 2013 | 2013 | 2013 |
| 2015: Upgrade von 2013 oder Neuinstallation | 2015 | 2013 | 2013 |
| 2013 | 2015 | 2013 | 2013 |

## <a name="upgrade-from-visual-studio-2013-test-agents"></a>Aktualisieren von Visual Studio 2013-Test-Agents

Sie sollten Agents für Visual Studio in allen neuen automatisierten Testszenarios verwenden. Sie können die Aufgabe *Test-Agent bereitstellen* in einer Builddefinition verwenden, um die Test-Agents auf Ihren Computer herunterzuladen und zu installieren.

In der folgenden Tabelle werden die von Agents für Visual Studio 2013 unterstützten Szenarios und die Alternativen für Team Foundation Server (TFS) 2015 und VSTS dargestellt:

| Szenarios, die von Agents für Visual Studio 2013 unterstützt werden | Alternativen in TFS und VSTS |
| --- | --- |
| Erstellen-Bereitstellen-Testen-Workflow in Visual Studio | Benutzer können eine [Builddefinition](/vsts/build-release/) (kein XAML-Build) für Szenarios zum Erstellen, Bereitstellen und Testen in TFS verwenden. |
| Auslastungstests (Leistungstests) mit lokalen Remotecomputern | Verwenden Sie das Testcontroller und Test-Agents 2013 Update 5, um Auslastungstests lokal auszuführen. |
| Remoteausführung von automatisierten Tests von Microsoft Test Manager mit einer Laborumgebung | Es gibt aktuell keine Alternative für dieses Szenario. Es wird empfohlen, dass Sie den Task „Funktionstests ausführen“ in Build- und Releasedefinitionen verwenden (nicht in XAML-Builds), um Tests remote auszuführen. |
| Entwickler, die Remotetests in Visual Studio ausführen | Wird nicht mehr unterstützt. |

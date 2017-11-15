---
title: Installieren und Konfigurieren von Test-Agents | Microsoft-Dokumentation
ms.custom: 
ms.date: 05/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: configure test agents, test lab
ms.assetid: EBAA2E04-A97A-4047-B739-8DBA7F2D5074
caps.latest.revision: "56"
ms.author: douge
manager: douge
ms.openlocfilehash: 738cdab9bcc93408e1bb53df205328d2bc5e917f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="install-and-configure-test-agents"></a>Installieren und Konfigurieren von Test-Agents

Sie benötigen für Testszenarios mit Visual Studio und Visual Studio Team Services oder Team Foundation Server (TFS) keinen Testcontroller, da Agents für Microsoft Visual Studio die Orchestrierung behandeln, indem Sie mit Team Services oder TFS kommunizieren. Sie führen z.B. kontinuierliche Tests mit Ihren Build- und Release-Workflows in Team Services oder TFS aus.

Wenn Sie für das Arbeiten mit TFS 2013 den Test-Agent oder Testcontroller benötigen, verwenden Sie Agents für Microsoft Visual Studio 2013 Update 5 und konfigurieren den Testcontroller.

Ziehen Sie auch in Betracht, ob es leichter wäre, [stattdessen Build oder Release Management zu verwenden](lab-management/use-build-or-rm-instead-of-lab-management.md).

## <a name="what-do-i-need"></a>Was benötige ich?

**Wie bekomme ich den Testcontroller und die Test-Agents?**

* Wenn Sie Tests mit Tasks von Build vNext verwenden und Agents aus einem lokalen Verzeichnis installieren möchten: 

  * [Laden Sie Agents für Microsoft Visual Studio 2015 RTM und Update 1 herunter](http://go.microsoft.com/fwlink/p/?LinkId=619266). 

  * [Laden Sie Agents für Microsoft Visual Studio 2017 und Visual Studio 2015 Update 2 herunter](https://www.visualstudio.com/downloads/download-visual-studio-vs). Klicken Sie auf **Tools für Visual Studio 2015** und dann auf **Agents für Visual Studio 2015** in der linken Navigationsleiste.

* [Laden Sie Agents für Microsoft Visual Studio 2013 Update 5 herunter](http://go.microsoft.com/fwlink/p/?LinkId=619264), wenn Sie Folgendes ausführen möchten:

  * Auslastungstests mit lokalen Remotecomputern

  * Kontinuierliche Tests, die Microsoft Test Manager oder MSTest remote verwenden sowie Testeinstellungen für Laborumgebungen

  * Kontinuierliche Tests mit TFS 2013

Diese Installer stehen als ISO-Dateien (virtuelle CD) für die unkomplizierte Installation auf virtuellen Computern zur Verfügung. 

[Kann ich Versionen von TFS, Microsoft Test Manager, dem Testcontroller und Test-Agent mischen?](#MixedVersions)

**Welche Systemanforderungen benötige ich für die Installation des Testcontrollers und der Test-Agents?**

| Element | Anforderungen |
| ---- | ------------ |
| **Agent** | Windows 10<br />Windows 8, Windows 8.1<br />Windows 7 Service Pack 1<br />Windows XP Service Pack 3<br />Windows Server 2012, Windows Server 2012 R2<br />Windows Server 2008 Release 2, Service Pack 1 |
| **Controller** | Windows 10<br />Windows 8, Windows 8.1<br />Windows 7 Service Pack 1<br />Windows Server 2012, Windows Server 2012 R2<br />Windows Server 2008 Release 2, Service Pack 1 |
| **.NET Framework** | .NET Framework 4.5 |

## <a name="q--a"></a>Fragen und Antworten

<!-- BEGINSECTION class="m-qanda" -->

<a name="MixedVersions"></a>

####<a name="q-can-i-mix-versions-of-tfs-microsoft-test-manager-the-test-controller-and-test-agent"></a>F: Kann ich Versionen von TFS, Microsoft Test Manager, dem Testcontroller und Test-Agent mischen?

A: Ja, hier sind die kompatiblen und unterstützten Kombinationen aufgelistet:

| TFS | Microsoft Test Manager mit Lab-Center | Controller | Agent |
| --- | -------------------------------------- | ---------- | ----- |
| 2015: Upgrade von 2013 | 2013 | 2013 |2013 |
| 2015: Neuinstallation | 2013 | 2013 | 2013 |
| 2015: Upgrade von 2013 oder Neuinstallation | 2015 | 2013 | 2013 |
| 2013 | 2015 | 2013 | 2013 |

####<a name="q-will-the-test-agent-2015-support-all-the-scenarios-supported-by-test-controller-and-test-agent-of-visual-studio-2013"></a>F: Unterstützt der Test-Agent 2015 alle Szenarios, die auch vom Testcontroller und Test-Agent von Visual Studio 2013 unterstützt werden?

A: Es wird empfohlen, dass Sie Agents für Visual Studio in allen neuen automatisierten Testszenarios verwenden. Sie können den Task „Test-Agent bereitstellen“ in einer Builddefinition verwenden, um die Test-Agents auf Ihren Computer herunterzuladen und zu installieren.
In der folgenden Tabelle werden die von Agents für Visual Studio 2013 unterstützten Szenarios und die Alternativen für TFS 2015 und TS dargestellt.

| Szenarios, die von Agents für Visual Studio 2013 unterstützt werden | Alternativen in TFS und TS |
| --- | --- |
| Erstellen-Bereitstellen-Testen-Workflow in Visual Studio | Benutzer können eine [Builddefinition](https://www.visualstudio.com/team-services/continuous-integration/) (kein XAML-Build) für Szenarios zum Erstellen, Bereitstellen und Testen in TFS verwenden. |
| Auslastungstests (Leistungstests) mit lokalen Remotecomputern | Verwenden Sie das Testcontroller/Test-Agents 2013 Update 5, um Auslastungstests lokal auszuführen. [Weitere Informationen](https://msdn.microsoft.com/en-us/library/ff400223.aspx). |
| Remoteausführung von automatisierten Tests von Microsoft Test Manager mit einer Laborumgebung | Es gibt aktuell keine Alternative für dieses Szenario. Es wird empfohlen, dass Sie den Task „Funktionstests ausführen“ in Build- und Releasedefinitionen verwenden (nicht in XAML-Builds), um Tests remote auszuführen. |
| Entwickler, die Remotetests in Visual Studio ausführen | Wird nicht mehr unterstützt. |

<!-- ENDSECTION -->

## <a name="see-also"></a>Siehe auch

* [Einrichten von Computern und Sammeln von Diagnoseinformationen mithilfe von Testeinstellungen](https://msdn.microsoft.com/library/dd286743%28v=vs.140%29.aspx)

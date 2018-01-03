---
title: "Verwenden von Build oder Release Management für automatische Tests | Microsoft-Dokumentation"
ms.custom: 
ms.date: 05/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: automated testing, lab management, test lab
ms.assetid: F34B0D19-B430-4C01-B402-62A861007E71
caps.latest.revision: "56"
ms.author: douge
manager: douge
ms.workload: multiple
ms.openlocfilehash: d103e74c0f6cf40bfd0e6dc26dd5777c6fe11f2f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="use-build-and-release-management-instead-of-lab-management-for-automated-testing"></a>Verwenden von Build und Release Management anstelle von Lab Management für automatische Tests

Wenn Sie Microsoft Test Manager (MTM) und Lab Management für automatische Tests oder für automatisiertes Build-Bereitstellen-Testen verwenden, wird in diesem Thema erläutert, wie Sie mit den Funktionen [Build &amp; Release](https://www.visualstudio.com/team-services/continuous-integration/) in Team Foundation Server (TFS) und Visual Studio Team Services dasselbe Ergebnis erzielen können:

* [Automatisiertes Build-Bereitstellen-Testen](#bdtautomation)

* [Self-Service-Verwaltung von SCVMM-Umgebungen](#managescvmm)

Build und Release Management unterstützen keine Self-Service-Erstellung von netzwerkisolierten SCVMM-Umgebungen, und es ist nicht geplant, dies in Zukunft zu unterstützen. Allerdings werden einige [Alternativen vorgeschlagen](#isolatedenvir).

<a name="bdtautomation"></a>
## <a name="build-deploy-test-automation"></a>Automatisiertes Build-Bereitstellen-Testen

MTM und Lab Management basieren zum automatischen Erstellen, Bereitstellen und Testen Ihrer Anwendungen auf einer XAML-Builddefinition.
Der XAML-Build stützt sich zum Erreichen dieses Ziels auf verschiedene Konstrukte in MTM, wie z.B. einer Lab-Umgebung, Testsammlungen und Testeinstellungen, sowie auf verschiedenen Infrastrukturkomponenten, wie z.B. einen Buildcontroller, Build-Agents, Testcontroller und Test-Agents. Sie können das Gleiche mit weniger Schritten mithilfe des Build oder Release Managements in TFS und Team Services erzielen.

| Schritte | Mit XAML Build | Mit Build oder Release Management |
|-------|----------------------|-----------------|
| Identifizieren der Computer, auf denen der Build bereitgestellt und Tests ausgeführt werden sollen. | Erstellen einer Standard-Lab-Umgebung in MTM mit diesen Computern. | n/v |
| Identifizieren der auszuführenden Tests. | Erstellen Sie eine Testsammlung in MTM, erstellen Sie Testfälle, und ordnen Sie jedem Testfall Automatisierung zu. Erstellen Sie Testeinstellungen in MTM, welche die Rolle der Computer in der Lab-Umgebung identifizieren, auf denen die Tests ausgeführt werden sollen. | Erstellen Sie auf die gleiche Weise eine automatisierte Testsammlung in MTM, wenn Sie Ihre Tests über Testpläne verwalten möchten. Alternativ können Sie diesen Schritt überspringen, wenn Sie die Tests direkt aus den von Ihren Builds erzeugten Testbinärdateien ausführen möchten. In keinem der Fälle ist es notwendig, Testeinstellungen zu erstellen. |
| Automatisieren von Bereitstellung und Testen. | Erstellen Sie eine XAML-Builddefinition mit LabDefaultTemplate.*.xaml. Geben Sie Build, Testsammlungen und Lab-Umgebung in der Builddefinition an. | Erstellen Sie eine [Builddefinition oder eine Releasedefinition](https://www.visualstudio.com/team-services/continuous-integration/) mit einer einzigen Umgebung. Führen Sie das gleiche Bereitstellungsskript (aus der XAML-Builddefinition) mit dem Befehlszeilentask aus, und führen Sie automatische Tests mit den Tasks „Test Agent-Bereitstellung“ und „Funktionstests ausführen“ aus. Geben Sie die Liste der Computer und deren Anmeldeinformationen als Eingaben für diese Tasks an. |

Zu den Vorteilen der Verwendung von Build oder Release Management für dieses Szenario gehören:

* Sie benötigen keinen Buildcontroller oder Testcontroller.
* Der Test-Agent wird über einen Task als Teil des Builds oder des Releases installiert.
* Sie können die Bereitstellungsschritte leicht anpassen. Sie sind nicht mehr auf die Verwendung eines einzelnen Skripts beschränkt. Sie können außerdem die vielen Tasks nutzen, die innerhalb des Produkts und in Visual Studio Marketplace verfügbar sind.
* Sie müssen keine Testsammlungen verwalten. Sie können Tests direkt aus den Binärdateien ausführen.
* Sie erhalten eine umfangreichere Inline-Berichterstattung für die Tests, die in jedem Build oder Release ausgeführt werden.
* Sie können nachverfolgen, welche Objekte (Release, Build, Arbeitstasks, Commits) derzeit bereitgestellt und in jeder Umgebung getestet werden.
* Sie können die Automatisierung anpassen und erweitern, um sie ganz einfach für mehrere Testumgebungen und sogar die Produktion bereitzustellen.
* Sie können die Automatisierung so planen, dass sie immer dann, wenn ein Check-In oder ein Commit auftritt, oder täglich zu einem bestimmten Zeitpunkt durchgeführt wird.

<a name="managescvmm"></a>
## <a name="self-service-management-of-scvmm-environments"></a>Self-Service-Verwaltung von SCVMM-Umgebungen

Das [Lab-Center in Microsoft Test Manager](https://msdn.microsoft.com/library/dd997438.aspx) unterstützt die Fähigkeit, eine Bibliothek von Umgebungsvorlagen zu verwalten und Umgebungen bei Bedarf mit einem [SCVMM-Server](https://technet.microsoft.com/system-center-docs/vmm/vmm) bereitzustellen.

Die Self-Service-Bereitstellungsfunktion von Lab Center verfolgt zwei unterschiedliche Ziele:

* Eine einfachere Möglichkeit zum Verwalten der Infrastruktur bieten. Das Verwalten von virtuellen Computer- und Umgebungsvorlagen, sowie das automatische Erstellen von privaten Netzwerken, um Klone von Umgebungen voneinander zu isolieren, sind Beispiele für die Infrastrukturverwaltung.

* Teams ein vereinfachtes Verfahren bieten, die virtuellen Computer in ihren Test- und Bereitstellungsaktivitäten zu nutzen. Das Zugänglichmachen von Lab-Umgebungen durch das gleiche Teamprojekt-Sicherheitsmodell, und die integrierte Verwendung dieser virtuellen Computer in Testszenarios sind Beispiele für einfache Verarbeitung.

Allerdings gibt es angesichts der Weiterentwicklung umfangreicherer öffentlicher und privater Cloud-Verwaltungssysteme wie z.B. [Microsoft Azure](https://azure.microsoft.com/) und [Microsoft Azure-Stack](https://azure.microsoft.com/overview/azure-stack/), keine Weiterentwicklung der Infrastrukturverwaltungsfunktionen in TFS 2017 und höher. Stattdessen wird der Fokus auf die einfache Verarbeitung von Ressourcen, die über solche Cloud-Infrastrukturen verwaltet werden, beibehalten.

Die folgende Tabelle enthält die typischen Aktivitäten, die Sie in Lab Center ausgeführt haben, und zeigt, wie Sie dasselbe Ergebnis mit SCVMM oder Azure erreichen können (wenn es sich um Infrastrukturverwaltungsaktivitäten handelt) oder mit TFS und Team Services (wenn es sich um Test- oder Bereitstellungsaktivitäten handelt):

| Schritte | Mit Lab-Center | Mit Build oder Release Management |
|-------|----------------------|-----------------|
| Verwalten einer Bibliothek von Umgebungsvorlagen. | Erstellen einer Lab-Umgebung. Installieren Sie erforderliche Software auf den virtuellen Computern. Bereiten Sie das System vor und speichern Sie die Umgebung als Vorlage in der Bibliothek. | Verwenden Sie direkt die SCVMM-Administratorkonsole zum Erstellen und Verwalten von Vorlagen für virtuelle Computer oder Dienstvorlagen. Wenn Sie Azure verwenden, wählen Sie eine der vordefinierten [Azure Resource Manager-Vorlagen](https://azure.microsoft.com/documentation/templates/) aus [Azure Marketplace](https://azure.microsoft.com/marketplace/) oder [Azure-Schnellstartvorlagen](https://azure.microsoft.com/documentation/templates/) aus. |
| Erstellen einer Lab-Umgebung. | Wählen Sie in der Bibliothek eine Umgebungsvorlage aus und stellen Sie diese bereit. Geben Sie die erforderlichen Parameter zum Anpassen der Konfiguration der virtuellen Computer an. | Verwenden Sie direkt die SCVMM-Administratorkonsole, um virtuelle Computer oder Dienstinstanzen aus Vorlagen zu erstellen. Verwenden Sie direkt das Azure-Portal, um Ressourcen zu erstellen. Oder erstellen Sie eine Releasedefinition mit einer Umgebung. Verwenden Sie die Azure-Tasks oder Tasks aus der [SCVMM-Integrationserweiterung](https://marketplace.visualstudio.com/items?itemname=ms-vscs-rm.scvmmapp), um neue virtuelle Computer zu erstellen. Das Erstellen eines neuen Releases dieser Definition entspricht dem Erstellen einer neuen Umgebung in Lab-Center. |
| Verbinden mit Computern. | Öffnen Sie die Lab-Umgebung im Umgebungs-Viewer. | Verwenden Sie direkt die SCVMM-Administratorkonsole, um eine Verbindung mit dem virtuellen Computer herzustellen. Verwenden Sie alternativ die IP-Adresse oder den DNS-Namen der virtuellen Computer, um Remotedesktopsitzungen zu öffnen. |
| Erstellen Sie einen Prüfpunkt einer Umgebung oder stellen Sie eine Umgebung an einem sauberen Prüfpunkt wieder her. | Öffnen Sie die Lab-Umgebung im Umgebungs-Viewer. Wählen Sie die Option zur Erstellung eines Prüfpunkts oder zur Wiederherstellung an einem vorherigen Prüfpunkt aus. | Verwenden Sie direkt die SCVMM-Administratorkonsole, um diese Vorgänge auf virtuellen Computern auszuführen. Oder, um diese Schritte als Teil einer größeren Automatisierung ausführen zu können, schließen Sie die Prüfpunkttasks aus der [SCVMM-Integrationserweiterung](https://marketplace.visualstudio.com/items?itemname=ms-vscs-rm.scvmmapp) als Teil der Umgebung in die Releasedefinition ein. |

<a name="isolatedenvir"></a>
## <a name="self-service-creation-of-network-isolated-environments"></a>Self-Service-Erstellung von netzwerkisolierten Umgebungen

Eine netzwerkisolierte Lab-Umgebung ist eine Gruppe von virtuellen SCVMM-Computern, die sicher geklont werden kann, ohne dass es zu Netzwerkkonflikten kommt. Dies erfolgte in MTM mit einer Reihe von Anweisungen, welche die virtuellen Computer in einem privaten Netzwerk mit einem Satz von Netzwerk-Schnittstellenkarten konfigurierten und einen anderen Satz von Netzwerk-Schnittstellenkarten verwendeten, um die virtuellen Computer in einem öffentlichen Netzwerk zu konfigurieren.

Mit der Entwicklung von umfangreicheren öffentlichen und privaten Cloud-Verwaltungssystemen wie z.B. [Microsoft Azure](https://azure.microsoft.com/) und [Microsoft Azure Stack](https://azure.microsoft.com/overview/azure-stack/), können Sie sich für ähnliche Funktionen mehr direkt auf die Cloud-Verwaltungstools verlassen. Es gibt keine entsprechende Möglichkeit dies im Build- und Release Management zu erreichen.

Die folgenden Alternativen werden für die Netzwerkisolation empfohlen:

* Eine Motivation für die Netzwerkisolation war die einfache Konfiguration von mehreren Klonen. Da jeder Klon ein exaktes Replikat des Originals ist, werden Computernamen und die Konfigurationseinstellungen unverändert beibehalten, was die Einrichtung einer neuen Umgebung vereinfacht. Dieser Vorteil verursacht jedoch auch Probleme an einem späteren Zeitpunkt im Lebenszyklus (z.B. in der Produktion), da die Art, in der Anwendungen letztendlich bereitgestellt werden, nicht die gleiche ist. **Stattdessen** sollten Sie in Betracht ziehen, neue Umgebungen auf die gleiche Weise einzurichten, mit der Sie die Produktion eingerichtet haben, und die Verwendung der Netzwerkisolation zu vermeiden.

* Verwenden Sie eine öffentliche Cloud-Infrastruktur wie z.B. [Microsoft Azure](https://azure.microsoft.com/) für Ihre benötigten Tests. Sie können problemlos [Azure Resource Manager-Vorlagen](https://azure.microsoft.com/documentation/templates/) aus [Azure Marketplace](https://azure.microsoft.com/marketplace/) oder aus [Azure-Schnellstartvorlagen](https://azure.microsoft.com/documentation/templates/) verwenden, um Gruppen von virtuellen Computern einzurichten, die über ein privates Netzwerk verbunden sind, und im öffentlichen Netzwerk nur mit einem Proxy oder einer „Jumpbox“ verfügbar gemacht werden.

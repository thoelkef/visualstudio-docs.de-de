---
title: Verwenden von Build oder Release Management für automatische Tests in Visual Studio | Microsoft-Dokumentation
ms.date: 03/02/2018
ms.technology: vs-ide-test
ms.topic: article
helpviewer_keywords:
- automated testing, lab management, test lab
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 5596dbbe65dc57dcb1862b74ed6379d1e2c080cf
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2018
---
# <a name="use-build-and-release-management-instead-of-lab-management-for-automated-testing"></a>Verwenden von Build und Release Management anstelle von Lab Management für automatische Tests

Wenn Sie Microsoft Test Manager (MTM) und Lab Management für automatische Tests oder für automatisiertes Build-Bereitstellen-Testen verwenden, erfahren Sie in diesem Thema, wie Sie mit den Funktionen [Build und Release](/vsts/build-release/) in Team Foundation Server (TFS) und Visual Studio Team Services (VSTS) dasselbe Ergebnis erzielen können.

## <a name="build-deploy-test-automation"></a>Automatisiertes Build-Bereitstellen-Testen

MTM und Lab Management basieren zum automatischen Erstellen, Bereitstellen und Testen Ihrer Anwendungen auf einer XAML-Builddefinition. Der XAML-Build stützt sich zum Erreichen dieses Ziels auf verschiedene Konstrukte in MTM, wie z.B. einer Lab-Umgebung, Testsammlungen und Testeinstellungen, sowie auf verschiedenen Infrastrukturkomponenten, wie z.B. einen Buildcontroller, Build-Agents, Testcontroller und Test-Agents. Sie können das Gleiche mit weniger Schritten mithilfe des Build oder Release Managements in TFS und Team Services erzielen.

| Schritte | Mit XAML Build | Mit Build oder Release Management |
|-------|----------------------|-----------------|
| Identifizieren der Computer, auf denen der Build bereitgestellt und Tests ausgeführt werden sollen. | Erstellen einer Standard-Lab-Umgebung in MTM mit diesen Computern. | n/v |
| Identifizieren der auszuführenden Tests. | Erstellen Sie eine Testsammlung in MTM, erstellen Sie Testfälle, und ordnen Sie jedem Testfall Automatisierung zu. Erstellen Sie Testeinstellungen in MTM, welche die Rolle der Computer in der Lab-Umgebung identifizieren, auf denen die Tests ausgeführt werden sollen. | Erstellen Sie auf die gleiche Weise eine automatisierte Testsammlung in MTM, wenn Sie Ihre Tests über Testpläne verwalten möchten. Alternativ können Sie diesen Schritt überspringen, wenn Sie die Tests direkt aus den von Ihren Builds erzeugten Testbinärdateien ausführen möchten. In keinem der Fälle ist es notwendig, Testeinstellungen zu erstellen. |
| Automatisieren von Bereitstellung und Testen. | Erstellen Sie eine XAML-Builddefinition mit LabDefaultTemplate.*.xaml. Geben Sie Build, Testsammlungen und Lab-Umgebung in der Builddefinition an. | Erstellen Sie eine [Build- oder Releasedefinition](/vsts/build-release/) mit einer einzigen Umgebung. Führen Sie das gleiche Bereitstellungsskript (aus der XAML-Builddefinition) mit dem Befehlszeilentask aus, und führen Sie automatische Tests mit den Tasks „Test Agent-Bereitstellung“ und „Funktionstests ausführen“ aus. Geben Sie die Liste der Computer und deren Anmeldeinformationen als Eingaben für diese Tasks an. |

Zu den Vorteilen der Verwendung von Build oder Release Management für dieses Szenario gehören:

* Sie benötigen keinen Buildcontroller oder Testcontroller.
* Der Test-Agent wird über einen Task als Teil des Builds oder des Releases installiert.
* Sie können die Bereitstellungsschritte leicht anpassen. Sie sind nicht mehr auf die Verwendung eines einzelnen Skripts beschränkt. Sie können außerdem die vielen Tasks nutzen, die innerhalb des Produkts und in Visual Studio Marketplace verfügbar sind.
* Sie müssen keine Testsammlungen verwalten. Sie können Tests direkt aus den Binärdateien ausführen.
* Sie erhalten eine umfangreichere Inline-Berichterstattung für die Tests, die in jedem Build oder Release ausgeführt werden.
* Sie können nachverfolgen, welche Objekte (Release, Build, Arbeitstasks, Commits) derzeit bereitgestellt und in jeder Umgebung getestet werden.
* Sie können die Automatisierung anpassen und erweitern, um sie ganz einfach für mehrere Testumgebungen und sogar die Produktion bereitzustellen.
* Sie können die Automatisierung so planen, dass sie immer dann, wenn ein Check-In oder ein Commit auftritt, oder täglich zu einem bestimmten Zeitpunkt durchgeführt wird.

## <a name="self-service-management-of-scvmm-environments"></a>Self-Service-Verwaltung von SCVMM-Umgebungen

Das [Test-Center in Microsoft Test Manager](/vsts/manual-test/mtm/guidance-mtm-usage) unterstützt die Fähigkeit, eine Bibliothek von Umgebungsvorlagen zu verwalten und Umgebungen bei Bedarf mit einem [SCVMM-Server](/system-center/vmm/overview?view=sc-vmm-1801) bereitzustellen.

Die Self-Service-Bereitstellungsfunktion von Lab Center verfolgt zwei unterschiedliche Ziele:

* Eine einfachere Möglichkeit zum Verwalten der Infrastruktur bieten. Das Verwalten von virtuellen Computer- und Umgebungsvorlagen, sowie das automatische Erstellen von privaten Netzwerken, um Klone von Umgebungen voneinander zu isolieren, sind Beispiele für die Infrastrukturverwaltung.

* Teams ein vereinfachtes Verfahren bieten, die virtuellen Computer in ihren Test- und Bereitstellungsaktivitäten zu nutzen. Das Zugänglichmachen von Lab-Umgebungen durch das gleiche Teamprojekt-Sicherheitsmodell, und die integrierte Verwendung dieser virtuellen Computer in Testszenarios sind Beispiele für einfache Verarbeitung.

Allerdings gibt es angesichts der Weiterentwicklung umfangreicherer öffentlicher und privater Cloud-Verwaltungssysteme wie z.B. [Microsoft Azure](https://azure.microsoft.com/) und [Microsoft Azure-Stack](https://azure.microsoft.com/overview/azure-stack/), keine Weiterentwicklung der Infrastrukturverwaltungsfunktionen in TFS 2017 und höher. Stattdessen wird der Fokus auf die einfache Verarbeitung von Ressourcen, die über solche Cloud-Infrastrukturen verwaltet werden, beibehalten.

Die folgende Tabelle enthält die typischen Aktivitäten, die Sie in Lab Center ausgeführt haben, und zeigt, wie Sie dasselbe Ergebnis mit SCVMM oder Azure erreichen können (wenn es sich um Infrastrukturverwaltungsaktivitäten handelt) oder mit TFS und Team Services (wenn es sich um Test- oder Bereitstellungsaktivitäten handelt):

| Schritte | Mit Lab-Center | Mit Build oder Release Management |
|-------|----------------------|-----------------|
| Verwalten einer Bibliothek von Umgebungsvorlagen. | Erstellen einer Lab-Umgebung. Installieren Sie erforderliche Software auf den virtuellen Computern. Bereiten Sie das System vor und speichern Sie die Umgebung als Vorlage in der Bibliothek. | Verwenden Sie direkt die SCVMM-Administratorkonsole zum Erstellen und Verwalten von Vorlagen für virtuelle Computer oder Dienstvorlagen. Wenn Sie Azure verwenden, wählen Sie eine der [Azure-Schnellstartvorlagen](/resources/templates/) aus. |
| Erstellen einer Lab-Umgebung. | Wählen Sie in der Bibliothek eine Umgebungsvorlage aus und stellen Sie diese bereit. Geben Sie die erforderlichen Parameter zum Anpassen der Konfiguration der virtuellen Computer an. | Verwenden Sie direkt die SCVMM-Administratorkonsole, um virtuelle Computer oder Dienstinstanzen aus Vorlagen zu erstellen. Verwenden Sie direkt das Azure-Portal, um Ressourcen zu erstellen. Oder erstellen Sie eine Releasedefinition mit einer Umgebung. Verwenden Sie die Azure-Tasks oder Tasks aus der [SCVMM-Integrationserweiterung](https://marketplace.visualstudio.com/items?itemname=ms-vscs-rm.scvmmapp), um neue virtuelle Computer zu erstellen. Das Erstellen eines neuen Releases dieser Definition entspricht dem Erstellen einer neuen Umgebung in Lab-Center. |
| Verbinden mit Computern. | Öffnen Sie die Lab-Umgebung im Umgebungs-Viewer. | Verwenden Sie direkt die SCVMM-Administratorkonsole, um eine Verbindung mit dem virtuellen Computer herzustellen. Verwenden Sie alternativ die IP-Adresse oder den DNS-Namen der virtuellen Computer, um Remotedesktopsitzungen zu öffnen. |
| Erstellen Sie einen Prüfpunkt einer Umgebung oder stellen Sie eine Umgebung an einem sauberen Prüfpunkt wieder her. | Öffnen Sie die Lab-Umgebung im Umgebungs-Viewer. Wählen Sie die Option zur Erstellung eines Prüfpunkts oder zur Wiederherstellung an einem vorherigen Prüfpunkt aus. | Verwenden Sie direkt die SCVMM-Administratorkonsole, um diese Vorgänge auf virtuellen Computern auszuführen. Oder, um diese Schritte als Teil einer größeren Automatisierung ausführen zu können, schließen Sie die Prüfpunkttasks aus der [SCVMM-Integrationserweiterung](https://marketplace.visualstudio.com/items?itemname=ms-vscs-rm.scvmmapp) als Teil der Umgebung in die Releasedefinition ein. |

## <a name="creation-of-network-isolated-environments"></a>Erstellung von netzwerkisolierten Umgebungen

Eine netzwerkisolierte Lab-Umgebung ist eine Gruppe von virtuellen SCVMM-Computern, die sicher geklont werden kann, ohne dass es zu Netzwerkkonflikten kommt. Dies erfolgte in MTM mit einer Reihe von Anweisungen, welche die virtuellen Computer in einem privaten Netzwerk mit einem Satz von Netzwerk-Schnittstellenkarten konfigurierten und einen anderen Satz von Netzwerk-Schnittstellenkarten verwendeten, um die virtuellen Computer in einem öffentlichen Netzwerk zu konfigurieren.

VSTS und TFS können allerdings in Kombination mit der SCVMM-Build- und -Bereitstellungsaufgabe verwendet werden, um SCVMM-Umgebungen zu verwalten, isolierte virtuelle Netzwerke bereitzustellen und Build-, Bereitstellungs- und Testszenarios zu implementieren. Sie können die Aufgabe z.B. verwenden,

* um Prüfpunkte zu erstellen, wiederherzustellen und zu löschen.
* um neue virtuelle Computer mit einer Vorlage zu erstellen.
* um virtuelle Computer zu starten oder zu beenden.
* um benutzerdefinierte PowerShell-Skripts für SCVMM auszuführen.

Weitere Informationen finden Sie unter [Create a virtual network isolated environment for build-deploy-test scenarios (Erstellen einer virtuellen netzwerkisolierten Umgebung für Build-, Bereitstellungs- und Testszenarios)](/vsts/build-release/actions/virtual-networks/create-virtual-network).

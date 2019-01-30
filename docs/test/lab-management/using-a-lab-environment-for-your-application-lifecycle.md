---
title: Verwenden einer Laborumgebung für DevOps
ms.date: 05/02/2017
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- lab environment, test lab
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 6bf618f8d7f93ca19e788fe8e6e9e1486548fa06
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55000219"
---
# <a name="use-a-lab-environment-for-your-devops"></a>Verwenden einer Laborumgebung für Ihre DevOps

Eine Lab-Umgebung ist eine Sammlung virtueller und physischer Computer, die Sie verwenden können, um Anwendungen zu entwickeln und zu testen. Eine Lab-Umgebung kann mehrere Rollen enthalten, die zum Testen von Anwendungen mit mehreren Ebenen benötigt werden, z. B. Arbeitsstationen, Webserver und Datenbankserver. Außerdem können Sie einen Erstellungs-, Bereitstellungs- und Testworkflow mit der Lab-Umgebung verwenden, um den Vorgang der Erstellung, Bereitstellung und Ausführung automatisierter Tests in der Anwendung zu automatisieren.

* **Verwenden eines Testplans zum Ausführen automatisierter Tests**: Sie können eine Auflistung automatisierter Tests, einen sogenannten *Testplan*, ausführen und den Fortschritt anzeigen.

* **Verwenden eines Workflows zum Erstellen, Bereitstellen und Testen**: Sie können einen Workflow zum Erstellen, Bereitstellen und Testen zum automatischen Testen von Anwendungen mit mehreren Ebenen verwenden. Ein typisches Beispiel hierfür ist ein Workflow, der einen Build startet, die Builddateien auf den entsprechenden Computern in einer Lab-Umgebung bereitstellt und anschließend automatisierte Tests ausführt. Zusätzlich können Sie planen, dass Ihr Workflow in bestimmten Zeiträumen ausgeführt wird.

* **Sammeln von Diagnosedaten sämtlicher Computer, selbst während des manuellen Tests**: Sie können Diagnosedaten gleichzeitig von mehreren Computer sammeln. Beispielsweise können Sie während eines einzelnen Testlaufs IntelliTrace, die Auswirkung und andere Datenformen von einem Webserver, einem Datenbankserver und einem Client erfassen.

Im Folgenden finden Sie Beispiele von allgemeinen Lab-Umgebungstopologien:

| Topologie | Beschreibung |
|---|---|
|![Topologie "Nur Server"](../media/topology_backend.png)| Diese Lab-Umgebung weist eine *Servertopologie*auf, die oft verwendet wird, um manuelle Tests auf Serveranwendungen auszuführen. Sie ermöglicht Testern, die eigenen Clientcomputer zu verwenden, um Fehler in der Umgebung zu überprüfen. In einer Back-End-Topologie enthält Ihre Lab-Umgebung nur Server. Wenn Sie diesen Topologietyp verwenden, stellen Sie für gewöhnlich mithilfe eines Clientcomputers, der nicht Bestandteil der Umgebung ist, eine Verbindung zu den Servern in der Lab-Umgebung her.|
|![Laborumgebung in der Cloud](../media/topology_cloud.png)| Diese Laborumgebung bietet ähnliche Funktionen wie die _Servertopologie_, aber erfordert keine physischen oder virtuellen Computer, die in einer lokalen Umgebung ausgeführt werden. Dadurch kann die Einrichtungszeit gesenkt sowie die Wartung vereinfacht und die Kosten verringert werden. Das Einrichten mehrere Websites und virtueller Computer sowie das benutzerdefinierte Vernetzen können Sie in einer Cloudumgebung wie Microsoft Azure schnell und einfach durchführen.|
|![Client-Server-Lab-Umgebung](../media/topology_clientserver.png)| Diese Lab-Umgebung verfügt über eine *Client-/Servertopologie*, die oftmals zum Testen einer Anwendung verwendet wird, die Server- und Clientkomponenten aufweist. In einer Client-/Servertopologie befinden sich alle zum Testen Ihrer Anwendung verwendeten Clientcomputer und Server in Ihrer Lab-Umgebung. Bei Verwendung dieser Topologie können Sie Testdaten von jedem Computer erfassen, der sich auf Ihre Tests auswirkt.|

| | |
|---|---|
| ![Kamerasymbol für Video](../../install/media/video-icon.png) | [Schauen Sie sich ein Video an](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Managing-lab-environments-for-testing) zum Verwalten von Lab-Umgebungen für Tests. |

## <a name="use-the-cloud-with-azure-pipelines-or-team-foundation-server-build-and-release"></a>Verwenden der Cloud mit Azure Pipelines oder Build und Release in Team Foundation Server

Sie können automatisierte Tests und das automatisierte Erstellen, Bereitstellen und Testen mit den [Build und Release](/azure/devops/pipelines/index?view=vsts)-Features von Team Foundation Server (TFS) und Azure Test Plans durchführen. Vorteile sind unter anderem:

* Sie benötigen keinen Buildcontroller oder Testcontroller.
* Der Test-Agent wird über einen Task als Teil des Builds oder des Releases installiert.
* Sie können die Bereitstellungsschritte leicht anpassen. Sie sind nicht mehr auf die Verwendung eines einzelnen Skripts beschränkt. Sie können außerdem die vielen Tasks nutzen, die innerhalb des Produkts und in Visual Studio Marketplace verfügbar sind.
* Sie müssen keine Testsammlungen verwalten. Sie können Tests direkt aus den Binärdateien ausführen.
* Sie erhalten eine umfangreichere Inline-Berichterstattung für die Tests, die in jedem Build oder Release ausgeführt werden.
* Sie können nachverfolgen, welche Objekte (Release, Build, Arbeitselemente, Commits) derzeit bereitgestellt und in jeder Umgebung getestet werden.
* Sie können die Automatisierung anpassen und erweitern, um sie ganz einfach für mehrere Testumgebungen und sogar die Produktion bereitzustellen.
* Sie können die Automatisierung so planen, dass sie immer dann, wenn ein Check-In oder ein Commit auftritt oder täglich zu einem bestimmten Zeitpunkt durchgeführt wird.

Weitere Informationen finden Sie unter [Verwenden von Build und Release Management anstelle von Lab Management für automatische Tests](use-build-or-rm-instead-of-lab-management.md).

## <a name="use-the-visual-studio-lab-management-features-of-microsoft-test-manager"></a>Das Verwenden der Funktionen von Visual Studio Lab Management von Microsoft Test Manager

Sie können mit den Funktionen von Visual Studio Lab Management Laborumgebungen erstellen und verwalten, wenn Sie die Visual Studio 2017 Enterprise-Edition verwenden.

Lab Management installiert automatisch Test-Agents auf jedem Computer in Ihrer Umgebung .

Wenn Sie Lab Management zusammen mit System Center Virtual Machine Manager (SCVMM) verwenden, profitieren Sie auch von den folgenden Vorteilen, wenn Sie Lab-Umgebungen verwenden:

* **Schnelle Reproduzierung von Computerkonfigurationen**: Sie können Auflistungen virtueller Computer speichern, die konfiguriert sind, typische Produktionsumgebungen neu zu erstellen. Sie können anschließend jeden Testlauf auf einer neuen Kopie einer gespeicherten Umgebung ausführen.

* **Reproduzieren der genauen Bedingungen eines Fehlers**: Bei einem fehlerhaften Testlauf können Sie eine Kopie des Status Ihrer Lab-Umgebung speichern und in Ihren Buildergebnissen oder über ein Arbeitselement darauf zugreifen.

* **Gleichzeitiges Ausführen mehrerer Kopien einer Laborumgebung**: Sie können mehrere Kopien Ihrer Lab-Umgebung gleichzeitig ohne Namenskonflikte ausführen.

### <a name="standard-environments-and-scvmm-environments"></a>Standard- und SCVMM-Umgebungen

Es gibt zwei Lab-Umgebungstypen, die Sie mit Visual Studio Lab Management erstellen können: **Standard**- und **SCVMM**-Umgebungen. Die Funktionalitäten jedes Umgebungstyps ist jedoch unterschiedlich.

**Standardumgebungen**: Diese können eine Kombination aus virtuellen und physischen Computern enthalten. Sie können einer Standardumgebung auch virtuelle Computer hinzufügen, die durch Drittanbieter-Virtualisierungsframeworks verwendet werden. Zudem sind für Standardumgebungen keine zusätzlichen Serverressourcen wie eine SCVMM-Server erforderlich.

**SCVMM-Umgebungen**: Diese können nur virtuelle Computer enthalten, die von SCVMM (System Center Virtual Machine Manager) verwaltet werden, sodass die virtuellen Computer in SCVMM-Umgebungen nur auf dem Hyper-V-Virtualisierungsframework ausgeführt werden können. SCVMM-Umgebungen stellen jedoch die folgenden Automatisierungs- und Verwaltungsfunktionen bereit, die in Standardumgebungen nicht verfügbar sind:

- **Umgebungsmomentaufnahmen:** Diese enthalten den Status einer Laborumgebung, sodass Sie schnell eine Umgebung im Grundzustand wiederherstellen oder den Status einer geänderten Umgebung speichern können. Sie können auch einen Workflow zum Erstellen, Bereitstellen und Testen verwenden, um den Vorgang der Speicherung und Wiederherstellung von Umgebungsmomentaufnahmen zu automatisieren.

- **Gespeicherte Umgebungen:** Sie können eine Kopie einer SCVMM-Umgebung speichern und anschließend mehrere Kopien dieser Umgebung bereitstellen.

- **Netzwerkisolation:** Die Netzwerkisolation ermöglicht Ihnen, gleichzeitig mehrere identische Kopien einer SCVMM-Umgebung ohne Computernamenskonflikte auszuführen.

- **Vorlagen für virtuelle Computer:** Eine Vorlage für virtuelle Computer ist ein virtueller Computer, dessen Name sowie andere Bezeichner entfernt wurden. Wenn eine Vorlage für virtuelle Computer in einer SCVMM-Umgebung bereitgestellt wird, generiert neue IDs. Dadurch können Sie mehrere Kopien eines virtuellen Computers in derselben Umgebung oder in mehrere Umgebungen bereitstellen und die virtuellen Computer anschließend gleichzeitig ausführen.

- **Gespeicherte virtuelle Computer:** ein in Ihrer Projektbibliothek gespeicherter virtueller Computer, der eindeutige Bezeichner umfasst.

> [!NOTE]
> Lab Management unterstützt SCVMM 2016 nicht.

Informationen zu SCVMM finden Sie unter [Virutal Machine Manager](/azure/devops/pipelines/?view=vsts).

Standard- und SCVMM-Umgebungen unterstützen viele derselben Funktionen. Es müssen jedoch wichtige Unterschiede berücksichtigt werden. In der folgenden Tabelle werden die Features verglichen, die für Standard- und SCVMM-Umgebungen verfügbar sind.

|Funktion|SCVMM-Umgebungen|Standardumgebungen|
|-|------------------------|-|
|**Testen**|||
|Ausführen manueller Tests|Unterstützt|Unterstützt|
|Ausführen codierter UI und anderer automatisierter Tests|Unterstützt|Unterstützt|
|Erfassen von Funktionsfehlern mithilfe von Diagnoseadaptern|Unterstützt|Unterstützt|
|**Buildbereitstellung**|||
|Automatisierte Workflows zum Testen, Bereitstellen und Testen|Unterstützt|Unterstützt|
|**Umgebungserstellung und -verwaltung**|||
|Verwenden physischer Computer neben virtuellen Computern|Nicht unterstützt|Unterstützt|
|Verwenden virtueller Computer von Drittanbietern|Nicht unterstützt|Unterstützt|
|Automatischen Installieren von Test-Agents auf Computern in der Lab-Umgebung|Unterstützt|Unterstützt|
|Speichern und Bereitstellen des Status einer Lab-Umgebung mithilfe von Umgebungsmomentaufnahmen|Unterstützt|Nicht unterstützt|
|Erstellen von Lab-Umgebungen aus Vorlagen für virtuelle Computer|Unterstützt|Nicht unterstützt|
|Starten/Stoppen/Momentaufnahme der Umgebung|Unterstützt|Nicht unterstützt|
|Verbinden mit der Umgebung mithilfe des Umgebungs-Viewers|Unterstützt|Unterstützt|
|Gleichzeitiges Ausführen mehrerer Kopien einer Umgebung mithilfe der Netzwerkisolation|Unterstützt|Nicht unterstützt|

### <a name="lab-management-concepts"></a>Lab-Verwaltungskonzepte

Im Folgenden finden Sie ein paar zusätzliche Konzepte, mit denen Sie vertraut sein sollten, bevor Sie fortfahren:

|Begriff|Beschreibung|
|-|-----------------|
|Lab-Center|Der Bereich von Microsoft Test Manager, in dem Sie Lab-Umgebungen erstellen und verwalten können.|
|Azure DevOps-Projekt-Lab|Die Sammlung der eingerichteten Lab-Umgebungen, sodass Sie eine Verbindung damit herstellen und ihre virtuellen Computer ausführen können.|
|Azure DevOps-Projektbibliothek|Ein Archiv mit gespeicherten virtuellen Computern, Vorlagen und gespeicherten Laborumgebungen, die in die Hostgruppe Ihres Projekts importiert wurden. Sie können die Elemente in Ihrer Bibliothek mit SCVMM-Umgebungen verwenden. Sie können sie jedoch nicht direkt zu einer Standardumgebung hinzufügen. Sie können die Elemente in Ihrer Bibliothek nicht ausführen, Sie verwenden sie vielmehr dafür, um eine neue Umgebung bereitzustellen.|
|Bereitgestellte Umgebung|Eine Laborumgebung, die in Ihrem Projekt-Lab bereitgestellt wurde, sodass Sie eine Verbindung damit herstellen und ihre Computer ausführen können.|

Weitere Informationen zu Lab Management finden Sie unter:

* [Planen des Labs](https://msdn.microsoft.com/library/ff756575%28v=vs.140%29.aspx)
* [Verwalten Ihres Labors](https://msdn.microsoft.com/library/dd936084%28v=vs.140%29.aspx)
* [Einrichten für SCVMM-Umgebungen](https://msdn.microsoft.com/library/dd380687%28v=vs.140%29.aspx)
* [Verwalten von Berechtigungen](https://msdn.microsoft.com/library/dd380760%28v=vs.140%29.aspx)
* [Ändern der Einrichtung](https://msdn.microsoft.com/library/ee704508%28v=vs.140%29.aspx)
* [Problembehandlung](https://msdn.microsoft.com/library/ee853230%28v=vs.140%29.aspx)

Weitere Informationen zur Einrichtung von Umgebungen finden Sie unter:

* [Build und Release-Cloudumgebungen](use-build-or-rm-instead-of-lab-management.md)
* [Standardmäßige Lab-Umgebungen](https://msdn.microsoft.com/library/ee390842.aspx)
* [(Virtuelle) SCVMM-Umgebungen](https://msdn.microsoft.com/library/ee943322.aspx)
* [Erstellen und Verwenden einer netzwerkisolierten Umgebung](https://msdn.microsoft.com/library/ee518924.aspx)

## <a name="see-also"></a>Siehe auch

* [Installieren und Konfigurieren von Test-Agents](../../test/lab-management/install-configure-test-agents.md)
* [Handbuch zu Visual Studio Lab Management](https://aka.ms/vsarsolutions)
* [Microsoft DevOps-Blog](https://blogs.msdn.microsoft.com/devops/)

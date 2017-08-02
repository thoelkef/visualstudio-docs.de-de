---
title: "Vorlage für Azure Cloud Services-Projekte für Python | Microsoft-Dokumentation"
ms.custom: 
ms.date: 4/10/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a2ce82ee-8c73-419a-bbd2-4c3513fd394d
caps.latest.revision: 11
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 9328c347d548a03a536cea16bd5851817c03d5a2
ms.openlocfilehash: 5dd1c40c925327c9494e3a334cdf348692a4981d
ms.lasthandoff: 04/10/2017

---

# <a name="azure-cloud-service-projects-for-python"></a>Azure Cloud Services-Projekte für Python

Visual Studio enthält Vorlagen, die Ihnen bei der Verwendung von Azure Cloud Services mithilfe von Python helfen.

Ein [Clouddienst](http://go.microsoft.com/fwlink/?LinkId=306052) besteht aus einer beliebigen Anzahl von *Workerrollen* und *Webrollen*, von denen jede eine konzeptionell gesonderte Aufgabe ausführt und nach Skalierungsbedarf separat über virtuelle Computer repliziert werden kann. Webrollen bieten das Hosting für Front-End-Webanwendungen. Im Zusammenhang mit Python kann jedes Webframework, das WSGI unterstützt, zum Schreiben einer solchen Anwendung verwendet werden (wie von der [Webprojektvorlage](template-web.md) unterstützt). Workerrollen sind für lang andauernde Prozesse vorgesehen, die nicht direkt mit den Benutzern interagieren. Sie nutzen in der Regel die Bibliotheken mit [Daten](http://go.microsoft.com/fwlink/?LinkId=401571) und [Anwendungsdiensten](http://go.microsoft.com/fwlink/?LinkId=401572), die mit `pip install`&nbsp;[`azure`](http://pypi.org/project/azure) installiert werden können.

Dieses Thema enthält Details über die Projektvorlage und sonstige Unterstützung in Visual Studio 2017 (frühere Versionen sind ähnlich, es gibt jedoch einige Unterschiede). Weitere Informationen zum Verwenden von Azure über Python finden Sie im [Azure Python Developer Center](http://go.microsoft.com/fwlink/?linkid=254360).

## <a name="create-a-project"></a>Erstellen eines Projekts

1. Installieren Sie das [Azure .NET SDK für Visual Studio](https://www.visualstudio.com/vs/azure-tools/), das für die Verwendung der Clouddienstvorlage erforderlich ist.
1. Wählen Sie in Visual Studio **Datei > Neu > Projekt** aus, suchen Sie nach „Azure Python“, und wählen Sie **Azure-Clouddienst** aus der Liste aus:

    ![Azure-Cloudprojektvorlage für Python](~/docs/python/media/template-azure-cloud-project.png)

1. Wählen Sie eine oder mehrere aufzunehmende Rollen aus. In Cloudprojekten können Rollen, die in verschiedenen Sprachen geschrieben wurden, kombiniert werden, sodass Sie problemlos jeden Teil der Anwendung in der am besten geeigneten Sprache schreiben können. Um dem Projekt nach Abschluss dieses Dialogfelds neue Rollen hinzuzufügen, klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf **Rollen**, und wählen Sie eines der Elemente unter **Hinzufügen** aus.

    ![Hinzufügen von Rollen in der Azure-Cloudprojektvorlage](~/docs/python/media/template-azure-cloud-service-project-wizard.png)

1. Beim Erstellen der einzelnen Rollenprojekte werden Sie möglicherweise aufgefordert, zusätzliche Python-Pakete, z.B. die Django-, Bottle- oder Flask-Frameworks, zu installieren, wenn Sie eine Rolle ausgewählt haben, die eines davon verwendet.

1. Nachdem Sie dem Projekt eine neue Rolle hinzugefügt haben, sehen Sie einige Konfigurationsanweisungen. Diese sind in der Regel nicht erforderlich, können aber für die zukünftige Anpassung Ihrer Projekte hilfreich sein. Beachten Sie, dass nur die Anweisungen für die letzte Rolle geöffnet bleiben, wenn Sie mehrere Rollen gleichzeitig hinzufügen. Sie finden jedoch Anweisungen und Tipps zur Problembehandlung für die anderen Rollen in den jeweiligen `readme.mht`-Dateien, die sich im Stammverzeichnis der Rolle oder im Ordner `bin` befinden.

1. Der Ordner `bin` eines Projekts enthält auch ein oder zwei PowerShell-Skripts, die verwendet werden, um die virtuellen Remotecomputer zu konfigurieren. Dies umfasst die Installation von Python, [requirements.txt](#dependencies)-Dateien in Ihrem Projekt und bei Bedarf die Einrichtung von IIS. Sie können diese Dateien nach Bedarf für Ihre Bereitstellung bearbeiten. Allerdings können die am häufigsten verwendeten Optionen auf andere Weise verwaltet werden (siehe [Konfigurieren der Rollenbereitstellung](#configuring-role-deployment) weiter unten). Es empfiehlt sich nicht, diese Dateien zu entfernen, da ein älteres Konfigurationsskript verwendet wird, wenn sie nicht verfügbar sind.

    ![Unterstützungsdateien für Workerrollen](~/docs/python/media/template-azure-cloud-service-worker-role-support-files.png)

    Um diese Konfigurationsskripts einem neuen Projekt hinzuzufügen, klicken Sie mit der rechten Maustaste auf das Projekt, wählen Sie **Hinzufügen > Neues Element** und dann entweder **Webrollen-Unterstützungsdateien** oder **Workerrollen-Unterstützungsdateien** aus.
   

## <a name="configuring-role-deployment"></a>Konfigurieren der Rollenbereitstellung

Die PowerShell-Skripts im Ordner `bin` eines Rollenprojekts steuern die Bereitstellung der Rolle und können zum Anpassen der Konfiguration bearbeitet werden:

- `ConfigureCloudService.ps1` wird für Web- und Workerrollen verwendet und dient normalerweise zum Installieren und Konfigurieren von Abhängigkeiten und zum Festlegen der Python-Version.
- `LaunchWorker.ps1` wird nur für Workerrollen verwendet und dient dazu, das Startverhalten zu ändern und Befehlszeilenargumente oder Umgebungsvariablen hinzuzufügen.

Beide Dateien enthalten Anweisungen für die Anpassung. Sie können auch Ihre eigene Version von Python installieren, indem Sie eine weitere Aufgabe zur Datei `ServiceDefinition.csdef` des Clouddienst-Hauptprojekts hinzufügen und die `PYTHON`-Variable auf den Pfad der installierten Datei `python.exe` (oder einer entsprechenden Datei) festlegen. Wenn `PYTHON` festgelegt ist, wird Python nicht von NuGet installiert.

Die zusätzliche Konfiguration kann wie folgt durchgeführt werden:

1. Installieren Sie Pakete mit `pip`, indem Sie die Datei `requirements.txt` im Stammverzeichnis des Projekts aktualisieren. Das Skript `ConfigureCloudService.ps1` installiert diese Datei bei der Bereitstellung.
1. Legen Sie Umgebungsvariablen fest, indem Sie Ihre Datei `web.config` (Webrollen) oder den Abschnitt `Runtime` Ihrer Datei `ServiceDefinition.csdef` (Workerrollen) ändern.
1. Geben Sie das Skript und die Argumente für eine Workerrolle an, indem Sie die Befehlszeile im Abschnitt `Runtime/EntryPoint` Ihrer Datei `ServiceDefinitions.csdef` ändern .
1. Legen Sie das Hauptskript des Handlers für eine Webrolle über die Datei `web.config` fest.

## <a name="testing-role-deployment"></a>Testen der Rollenbereitstellung

Beim Schreiben der Rollen können Sie Ihr Cloudprojekt lokal mit dem Clouddienstemulator testen. Der Emulator ist in den Azure SDK-Tools enthalten. Er stellt eine eingeschränkte Version der Umgebung dar, die verwendet wird, wenn Ihr Clouddienst in Azure veröffentlicht wird.

Um den Emulator zu starten, stellen Sie zunächst sicher, dass Ihr Cloudprojekt das Startprojekt in der Projektmappe ist, indem Sie mit der rechten Maustaste klicken und **Als Startprojekt festlegen** auswählen. Wählen Sie dann **Debuggen > Debuggen starten** (F5) oder **Debuggen > Starten ohne Debugging** (STRG+F5) aus.

Beachten Sie, dass es aufgrund von Beschränkungen im Emulator nicht möglich ist, den Python-Code zu debuggen. Wir empfehlen Ihnen daher, Ihre Rollen zu debuggen, indem Sie sie unabhängig voneinander ausführen, und dann den Emulator für Integrationstests vor der Veröffentlichung zu verwenden.


## <a name="deploying-a-role"></a>Bereitstellen einer Rolle

Wählen Sie zum Öffnen des **Veröffentlichungs**-Assistenten das Rollenprojekt im Projektmappen-Explorer aus, und wählen Sie im Hauptmenü **Erstellen > Veröffentlichen** aus, oder klicken Sie mit der rechten Maustaste, und wählen Sie **Veröffentlichen** aus.

Der Veröffentlichungsvorgang umfasst zwei Phasen. Zunächst erstellt Visual Studio ein einzelnes Paket, das alle Rollen für den Clouddenst enthält. Dieses Paket wird in Azure bereitgestellt. Dadurch werden ein oder mehrere virtuelle Computer für jede Rolle initialisiert und die Quelle bereitgestellt.

Wenn die einzelnen virtuellen Computer aktiviert werden, führen das Skript `ConfigureCloudService.ps1` aus und installieren alle Abhängigkeiten. Mit diesem Skript werden standardmäßig eine aktuelle Python-Version von [NuGet](https://www.nuget.org/packages?q=Tags%3A%22python%22+Authors%3A%22Python+Software+Foundation%22) und alle Pakete gemäß einer `requirements.txt`-Datei installiert. 

Schließlich führen Workerrollen `LaunchWorker.ps1` aus. Damit wird die Ausführung des Python-Skripts gestartet. Webrollen initialisieren IIS und beginnen mit der Verarbeitung von Webanforderungen.


## <a name="dependencies"></a>Abhängigkeiten

Das Skript `ConfigureCloudService.ps1` verwendet für den Clouddienst `pip`, um einen Satz von Python-Abhängigkeiten zu installieren. Diese sollten in einer Datei namens `requirements.txt` angegeben werden (anpassbar durch Ändern von `ConfigureCloudService.ps1`). Die Datei wird mit `pip install -r requirements.txt` als Teil der Initialisierung ausgeführt.

Beachten Sie, dass Clouddienstinstanzen keine C-Compiler beinhalten. Daher müssen alle Bibliotheken mit C-Erweiterungen vorkompilierte Binärdateien bereitstellen.

pip und entsprechende Abhängigkeiten sowie die Pakete in `requirements.txt` werden automatisch heruntergeladen. Dies kann als fakturierbare Bandbreitennutzung gewertet werden. Unter [Verwalten von erforderlichen Paketen](python-environments.md#managing-required-packages) finden Sie ausführliche Informationen zum Verwalten von `requirements.txt`-Dateien.

## <a name="troubleshooting"></a>Problembehandlung

Wenn sich Ihre Web- oder Workerrolle nach der Bereitstellung nicht ordnungsgemäß verhält, überprüfen Sie Folgendes:

- Ihr Python-Projekt enthält einen Ordner „bin\“ mit (mindestens):
    - `ConfigureCloudService.ps1`
    - `LaunchWorker.ps1` (für Workerrollen)
    - `ps.cmd`

- Ihr Python-Projekt enthält eine Datei `requirements.txt` mit allen Abhängigkeiten (oder alternativ eine Sammlung von wheel-Dateien).
- Aktivieren Sie Remotedesktop für den Clouddienst, und untersuchen Sie die Protokolldateien.
- Protokolle für `ConfigureCloudService.ps1` und `LaunchWorker.ps1` befinden sich im Ordner `C:\Resources\Directory\%RoleId%.DiagnosticStore\LogFiles` auf dem Remotecomputer.
- Webrollen können weitere Protokolle in einen Pfad schreiben, der in `web.config` konfiguriert ist, und zwar in den Pfad in der appSetting `WSGI_LOG`. Normale IIS- oder FastCGI-Protokolle können auch verwendet werden.
- Derzeit ist die Datei `LaunchWorker.ps1.log` die einzige Möglichkeit zum Anzeigen von Ausgaben oder Fehlern, die von der Python-Workerrolle angezeigt werden.

---
title: Problembehandlung bei der Installation | Microsoft-Dokumentation
description: '{{PLATZHALTER}}'
ms.date: 04/14/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 556EDD3F-E365-43EE-B3DD-03AA4353F75B
author: timsneath
ms.author: tims
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 85576806818a6ed289c2f660f87b5c419016c600
ms.openlocfilehash: d8125873ab5a92d9af26c556cb2f953a606c28d9
ms.contentlocale: de-de
ms.lasthandoff: 05/09/2017

---
# <a name="troubleshooting-visual-studio-2017-installation-and-upgrade-failures"></a>Problembehandlung bei der Visual Studio 2017-Installation und Upgradefehlern

## <a name="symptoms"></a>Symptome
Wenn Sie versuchen, Microsoft Visual Studio 2017 zu installieren oder zu aktualisieren, schlägt der Vorgang fehl.

## <a name="workaround"></a>Problemumgehung
Führen Sie die folgenden Schritte aus, um dieses Problem zu umgehen.

### <a name="step-1---check-whether-this-problem-is-a-known-issue"></a>Schritt 1: Prüfen, ob das Problem bekannt ist
Es gibt einige bekannte Probleme mit dem Visual Studio-Installer, an deren Behebung Microsoft arbeitet. Überprüfen Sie in den [Anmerkungen zu dieser Version den Abschnitt „Bekannte Probleme“](https://www.visualstudio.com/en-us/news/releasenotes/vs2017-relnotes#KIinstall), um zu prüfen, ob es eine Lösung für Ihr Problem gibt.

### <a name="step-2---check-with-the-developer-community"></a>Schritt 2: Nachfragen in der Entwicklercommunity
Suchen Sie Ihre Fehlermeldung in der [Visual Studio-Entwicklercommunity](https://developercommunity.visualstudio.com/spaces/8/index.html. Andere Mitglieder der Community haben ggf. eine Lösung für Ihr Problem dokumentiert.

### <a name="step-3---delete-the-visual-studio-installer-directory-to-fix-upgrade-problems"></a>Schritt 3: Löschen des Visual Studio-Installer-Verzeichnisses, um Probleme mit Upgrades zu beheben
Der Visual Studio-Installer-Bootstrapper ist eine kleine schlanke ausführbare Datei, mit der der Rest des Visual Studio-Installers installiert wird. Das Löschen von Visual Studio-Installer-Dateien und anschließende erneute Ausführen des Bootstrappers hilft ggf. bei der Behebung einiger Updatefehler. Führen Sie dazu folgende Schritte aus:

1. Schließen Sie den Visual Studio-Installer.
2. Löschen Sie das Visual Studio-Installer-Verzeichnis. In der Regel heißt das Verzeichnis „C:\Program Files (x86) \Microsoft Visual Studio\Installer“.
3. Führen Sie den Visual Studio-Installer-Bootstrapper aus. Den Bootstrapper finden Sie ggf. in Ihrem Ordner „Downloads“ mit einem Dateiname mit dem Muster ```vs_[Visual Studio edition]__*.exe```. Wenn Sie die Anwendung nicht finden, können Sie den Bootstrapper herunterladen, indem Sie die [Visual Studio-Seite „Downloads“](https://www.visualstudio.com/downloads/) aufrufen und dann für Ihre Edition von Visual Studio auf **Herunterladen** klicken. Führen Sie diese ausführbare Datei aus, um die Metadaten für Ihre Installation zurückzusetzen.
4. Versuchen Sie, Visual Studio erneut zu installieren oder zu aktualisieren. Wenn der Installer weiterhin fehlschlägt, fahren Sie unmittelbar mit Schritt 4 unten fort.
<br/>**Hinweis:** In diesem Schritt werden die Visual Studio-Installer-Dateien neu installiert und die Metadaten der Installation zurückgesetzt. 

### <a name="step-4---report-a-problem"></a>Schritt 4: Melden eines Problems
In einigen Situationen, z. B. bei beschädigten Dateien, müssen die Probleme ggf. fallweise untersucht werden:

1. Laden Sie das [Protokollerfassungstool für Microsoft Visual Studio und .NET Framework](https://www.microsoft.com/en-us/download/details.aspx?id=12493) herunter, und führen Sie es aus. Dieses Tool sammelt und kompiliert für Visual Studio-, .NET Framework- und SQL Server-Installationen verfügbare Setupprotokolle.
2. Öffnen Sie den Visual Studio-Installer, und klicken Sie dann auf **Problem melden**, um das Visual Studio-Feedbacktool zu öffnen.
![Sie können zur Schaltfläche „Feedback geben“ navigieren, um das Feedbacktool zu öffnen](media/report-a-problem.png)
3. Versehen Sie Ihren Problembericht mit einem Titel, und geben Sie relevante Details an. Klicken Sie auf **Weiter**, um zum Abschnitt **Anlagen** zu wechseln. Fügen Sie die generierte Protokolldatei an (in der Regel befindet sich die Datei unter „%TEMP%\vslogs.zip“).
![Navigieren Sie zur Schaltfläche „Neues Problem melden“, und befolgen Sie dann die Anweisungen](media/problem-report-details.png)
4. Klicken Sie auf **Weiter**, um Ihren Problembericht zu überprüfen, und dann auf **Senden**.

### <a name="step-5---run-installcleanupexe-to-clean-up-installation-files"></a>Schritt 5: Ausführen von „InstallCleanup.exe“, um die Installationsdateien zu bereinigen
Als letzte Möglichkeit können Sie „InstallCleanup.exe“ ausführen. „InstallCleanup.exe“ ist ein Hilfsprogramm im Paket des Visual Studio-Installers zum Bereinigen von Installationsdateien. Dieses Hilfsprogramm führt keine vollständige Neuinstallation durch. Es löscht den Cache und die Instanzdaten für Visual Studio 2017.

1. Schließen Sie den Visual Studio-Installer.
2. Öffnen Sie eine Eingabeaufforderung als Administrator. Führen Sie dazu folgende Schritte aus:
   * Klicken Sie im **Startmenü** auf **Ausführen** (START+R).
   * Geben Sie **cmd** ein.
   * Klicken Sie mit der rechten Maustaste auf **Eingabeaufforderung**, und wählen Sie dann **Als Administrator ausführen**.
3. Geben Sie den vollständigen Pfad des Hilfsprogramms „InstallCleanup.exe“ ein, und übergeben Sie den folgenden Befehlszeilenschalter: -f. Der Pfad des Hilfsprogramms ist standardmäßig wie folgt:
   ```
   C:\Program Files (x86)\Microsoft Visual Studio\Installer\resources\app\layout\InstallCleanup.exe
   ```
4. Führen Sie den Bootstrapper erneut aus, was in Schritt 3 beschrieben ist.
5. Versuchen Sie, Visual Studio erneut zu installieren oder zu aktualisieren.

## <a name="how-to-troubleshoot-an-offline-installer"></a>Gewusst wie: Problembehandlung bei einem Offlineinstallationsprogramm
Es folgt eine Tabelle mit bekannten Problemen und einigen Problemumgehungen, die bei Installation mithilfe eines lokalen Layouts helfen können.

| Problem       | Element                   | Lösung |
| ----------- | ---------------------- | -------- |
| Benutzer haben keinen Zugriff auf Dateien. | Berechtigungen (ACLs) | Stellen Sie sicher, dass Sie die Berechtigungen (ACLs) so anpassen, dass anderen Benutzern Lesezugriff erteilt wird, *bevor* Sie die Offlineinstallation freigeben. |
| Neue Arbeitslasten, Komponenten oder Sprachen werden nicht installiert.  | `--layout`  | Stellen Sie sicher, dass Sie über Internetzugriff verfügen, wenn Sie eine Installation aus einem partiellen Layout heraus ausführen und Arbeitsauslastungen, Komponenten oder Sprachen auswählen, die im früheren Layout nicht verfügbar sind. |




---
title: Problembehandlung bei der Installation
description: Manchmal kann etwas schiefgehen. Wenn die Installation oder das Upgrade von Visual Studio fehlschlägt, kann diese Seite Ihnen helfen.
ms.date: 11/21/2017
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.topic: troubleshooting
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 556EDD3F-E365-43EE-B3DD-03AA4353F75B
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f0009aa15919cf04c3ff8e56edf4f10adcb7e0ea
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/20/2018
---
# <a name="troubleshooting-visual-studio-2017-installation-and-upgrade-issues"></a>Problembehandlung bei der Visual Studio 2017-Installation und Upgradefehlern

## <a name="symptoms"></a>Symptome

Wenn Sie versuchen, Visual Studio 2017 zu installieren oder zu aktualisieren, tritt ein Fehler auf.

## <a name="workaround"></a>Problemumgehung

Führen Sie die folgenden Schritte aus, um dieses Problem zu umgehen.

### <a name="step-1---check-whether-this-problem-is-a-known-issue"></a>Schritt 1: Prüfen, ob das Problem bekannt ist

Es gibt einige bekannte Probleme mit dem Visual Studio-Installer, an deren Behebung Microsoft arbeitet. Überprüfen Sie in den [Anmerkungen zu dieser Version den Abschnitt „Bekannte Probleme“](https://www.visualstudio.com/news/releasenotes/vs2017-relnotes#known-issues), um zu prüfen, ob es eine Lösung für Ihr Problem gibt.

### <a name="step-2---check-with-the-developer-community"></a>Schritt 2: Nachfragen in der Entwicklercommunity

Suchen Sie in der [Visual Studio-Entwicklercommunity](https://developercommunity.visualstudio.com/spaces/8/index.html) nach der Fehlermeldung. Andere Mitglieder der Community haben ggf. eine Lösung für Ihr Problem dokumentiert.

### <a name="step-3---delete-the-visual-studio-installer-directory-to-fix-upgrade-problems"></a>Schritt 3: Löschen des Visual Studio-Installer-Verzeichnisses, um Probleme mit Upgrades zu beheben

Der Visual Studio-Installer-Bootstrapper ist eine kleine schlanke ausführbare Datei, mit der der Rest des Visual Studio-Installers installiert wird. Das Löschen von Visual Studio-Installer-Dateien und anschließende erneute Ausführen des Bootstrappers hilft ggf. bei der Behebung einiger Updatefehler.

>[!NOTE]
Mithilfe der folgenden Aktionen werden die Visual Studio-Installer-Dateien neu installiert und die Installationsmetadaten zurückgesetzt.

1. Schließen Sie den Visual Studio-Installer.
2. Löschen Sie das Visual Studio-Installer-Verzeichnis. Das Verzeichnis ist in der Regel `C:\Program Files (x86)\Microsoft Visual Studio\Installer`.
3. Führen Sie den Visual Studio-Installer-Bootstrapper aus. Den Bootstrapper finden Sie ggf. in Ihrem Ordner „Downloads“ mit einem Dateiname mit dem Muster `vs_[Visual Studio edition]__*.exe`. Wenn Sie die Anwendung nicht finden, können Sie den Bootstrapper herunterladen, indem Sie die [Visual Studio-Seite „Downloads“](https://www.visualstudio.com/downloads/) aufrufen und dann für Ihre Edition von Visual Studio auf **Herunterladen** klicken. Führen Sie diese ausführbare Datei aus, um die Metadaten für Ihre Installation zurückzusetzen.
4. Versuchen Sie, Visual Studio erneut zu installieren oder zu aktualisieren. Wenn beim Installer weiterhin ein Fehler auftritt, fahren Sie mit dem nächsten Schritt fort.

### <a name="step-4---report-a-problem"></a>Schritt 4: Melden eines Problems

In einigen Situationen, z. B. bei beschädigten Dateien, müssen die Probleme ggf. fallweise untersucht werden:

1. Sammeln Sie Ihre Setupprotokolle. Nähere Informationen finden Sie unter [Abrufen der Visual Studio-Installationsprotokolle](#how-to-get-the-visual-studio-installation-logs).
2. Öffnen Sie den Visual Studio-Installer, und klicken Sie dann auf **Problem melden**, um das Visual Studio-Feedbacktool zu öffnen.
![Sie können zur Schaltfläche „Feedback geben“ navigieren, um das Feedbacktool zu öffnen](media/report-a-problem.png)
3. Versehen Sie Ihren Problembericht mit einem Titel, und geben Sie relevante Details an. Klicken Sie auf **Weiter**, um zum Abschnitt **Anlagen** zu wechseln. Fügen Sie die generierte Protokolldatei an (in der Regel befindet sich die Datei unter `%TEMP%\vslogs.zip`).
4. Klicken Sie auf **Weiter**, um Ihren Problembericht zu überprüfen, und dann auf **Senden**.

### <a name="step-5---run-installcleanupexe-to-remove-installation-files"></a>Schritt 5: Ausführen von „InstallCleanup.exe“, um die Installationsdateien zu entfernen

Als letzten Ausweg können Sie [Visual Studio entfernen](remove-visual-studio.md), um alle Installationsdateien und Produktinformationen zu entfernen.

1. Folgen Sie den Anweisungen unter [Entfernen von Visual Studio](remove-visual-studio.md).
2. Führen Sie den in [Schritt 3: Löschen des Visual Studio-Installer-Verzeichnisses, um Probleme mit Upgrades zu beheben](#step-3---delete-the-visual-studio-installer-directory-to-fix-upgrade-problems) beschriebenen Bootstrapper erneut aus.
3. Versuchen Sie, Visual Studio erneut zu installieren oder zu aktualisieren.

### <a name="step-6---contact-us-optional"></a>Schritt 6: Wenden Sie sich an uns (optional)

Wenn keiner der anderen Schritte Ihnen bei der erfolgreichen Installation hilft, können Sie uns per Livechat kontaktieren, um Hilfe bei der Installation zu erhalten (nur in englischer Sprache). Einzelheiten finden Sie auf der [Visual Studio-Supportseite](https://www.visualstudio.com/vs/support/#talktous).

## <a name="how-to-troubleshoot-an-offline-installer"></a>Gewusst wie: Problembehandlung bei einem Offlineinstallationsprogramm

Es folgt eine Tabelle mit bekannten Problemen und einigen Problemumgehungen, die bei Installation mithilfe eines lokalen Layouts helfen können.

| Problem       | Element                   | Lösung |
| ----------- | ---------------------- | -------- |
| Benutzer haben keinen Zugriff auf Dateien. | Berechtigungen (ACLs) | Stellen Sie sicher, dass Sie die Berechtigungen (ACLs) so anpassen, dass anderen Benutzern Lesezugriff erteilt wird, *bevor* Sie die Offlineinstallation freigeben. |
| Neue Arbeitslasten, Komponenten oder Sprachen werden nicht installiert.  | `--layout`  | Stellen Sie sicher, dass Sie über Internetzugriff verfügen, wenn Sie eine Installation aus einem partiellen Layout heraus ausführen und Arbeitsauslastungen, Komponenten oder Sprachen auswählen, die nicht zuvor in diesem partiellen Layout heruntergeladen wurden. |

## <a name="how-to-get-the-visual-studio-installation-logs"></a>Gewusst wie: Abrufen der Visual Studio-Installationsprotokolle

Setupprotokolle sind zum Beheben der meisten Installationsprobleme nicht erforderlich. Wenn Sie ein Problem mit [Melden eines Problems mit Visual Studio 2017](../ide/how-to-report-a-problem-with-visual-studio-2017.md) im Visual Studio-Installer melden, werden diese Protokolle automatisch in Ihren Bericht einbezogen.

Wenn Sie sich an den Microsoft-Support wenden, müssen Sie möglicherweise diese Setupprotokolle mit dem [Protokollerfassungstool für Microsoft Visual Studio und .NET Framework](https://aka.ms/vscollect) bereitstellen. Das Protokollerfassungstool erfasst Setupprotokolle aller von Visual Studio 2017 installierten Komponenten einschließlich .NET Framework, Windows SDK und SQL Server. Es erfasst auch Computerinformationen, einen Windows Installer-Bestand und Windows-Ereignisprotokollinformationen für Visual Studio-Installer, Windows Installer und Systemwiederherstellung.

So erfassen Sie die Protokolle:

1. [Laden Sie das Tool herunter](https://aka.ms/vscollect).
2. Öffnen Sie eine Eingabeaufforderung als Administrator.
3. Führen Sie `Collect.exe` aus dem Verzeichnis aus, in dem Sie das Tool gespeichert haben.
4. Suchen Sie die sich daraus ergebende `vslogs.zip`-Datei in Ihrem `%TEMP%`-Verzeichnis, z.B. `C:\Users\YourName\AppData\Local\Temp\vslogs.zip`.

> [!NOTE]
> Das Tool muss unter dem gleichen Benutzerkonto ausgeführt werden, unter dem die fehlgeschlagene Installation ausgeführt wurde. Wenn Sie das Tool in einem anderen Benutzerkonto ausführen, legen Sie die Option `–user:<name>` fest, um das Benutzerkonto anzugeben, unter dem die fehlgeschlagene Installation ausgeführt wurde. Führen Sie `Collect.exe -?` in einer Eingabeaufforderung als Administrator für zusätzliche Optionen und Nutzungsinformationen aus.

## <a name="more-support-options"></a>Weitere Supportoptionen

Wenn keiner der anderen Schritte Ihnen bei der erfolgreichen Installation hilft, können Sie uns per Livechat kontaktieren, um Hilfe bei der Installation zu erhalten (nur in englischer Sprache). Einzelheiten finden Sie auf der [Visual Studio-Supportseite](https://www.visualstudio.com/vs/support/#talktous).

Hier sind einige weitere Optionen:

* Sie können uns über Produktprobleme mit dem Tool [Problem melden](../ide/how-to-report-a-problem-with-visual-studio-2017.md) informieren, das sowohl im Visual Studio-Installer als auch in der Visual Studio-IDE angezeigt wird.
* Sie können uns einen Produktvorschlag unter [UserVoice](https://visualstudio.uservoice.com/forums/121579) mitteilen.
* Sie können Probleme mit Produkten und Antworten in der [Visual Studio-Entwicklercommunity](https://developercommunity.visualstudio.com/) finden.
* Sie können auch über die [Visual Studio-Unterhaltung in der Gitter-Community](https://gitter.im/Microsoft/VisualStudio) Kontakt zu uns oder zu anderen Visual Studio-Entwicklern aufnehmen. (Diese Option erfordert ein [GitHub](https://github.com/)-Konto.)

## <a name="see-also"></a>Siehe auch

* [Administratorhandbuch für Visual Studio](visual-studio-administrator-guide.md)
* [Tools zum Erkennen und Verwalten von Visual Studio-Instanzen](tools-for-managing-visual-studio-instances.md)
* [Entfernen von Visual Studio 2017](remove-visual-studio.md)

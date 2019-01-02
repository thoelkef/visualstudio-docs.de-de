---
title: Erstellen einer netzwerkbasierten Installation
description: Erfahren Sie, wie ein Netzwerkinstallationspunkts für die Bereitstellung von Visual Studio in einem Unternehmen erstellt wird.
ms.date: 10/17/2017
ms.technology: vs-acquisition
ms.custom: seodec18
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 4CABFD20-962E-482C-8A76-E4012052F701
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cb259e1b6b90b93d01cdabd5622e0397d037c250
ms.sourcegitcommit: 0cdd8e8a53fb4fd5e869f07c35204419fa12783d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2018
ms.locfileid: "53159450"
---
# <a name="create-a-network-installation-of-visual-studio-2017"></a>Erstellen einer Netzwerkinstallation von Visual Studio 2017

Normalerweise erstellen Unternehmensadministratoren für die Bereitstellung auf Clientarbeitsstationen einen Netzwerkinstallationspfad. Wir haben Visual Studio 2017 so entworfen, dass die Dateien für die Erstinstallation zusammen mit allen Produktupdates in einem einzelnen Ordner zwischengespeichert werden. (Dieser Prozess wird auch als _Erstellen eines Layouts_ bezeichnet.) Dadurch können Clientarbeitsstationen dieselbe Netzwerkadresse verwenden, um ihre Installation zu verwalten, selbst wenn sie noch nicht auf das neueste Wartungsupdate aktualisiert haben.

 > [!NOTE]
 > Wenn Sie mehrere Editionen von Visual Studio in Ihrem Unternehmen nutzen (z.B. Visual Studio Professional und Visual Studio Enterprise), benötigen Sie für jede Edition eine eigene Netzwerkinstallationsfreigabe.

## <a name="download-the-visual-studio-bootstrapper"></a>Herunterladen des Visual Studio-Bootstrappers

**Laden** Sie die gewünschte Edition von Visual Studio herunter. Achten Sie darauf, auf **Speichern** zu klicken, und dann auf **Ordner öffnen**.

Ihre ausführbare Setupdatei &mdash; oder genauer gesagt die Bootstrapperdatei &mdash; entspricht einer der folgenden.

|Edition | Herunterladen|
|-------------|-----------------------|
|Visual Studio Enterprise | [**vs_enterprise.exe**](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=enterprise&rel=15?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=network+install&utm_content=download+vs2017) |
|Visual Studio Professional | [**vs_professional.exe**](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=professional&rel=15?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=network+install&utm_content=download+vs2017) |
|Visual Studio-Community | [**vs_community.exe**](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=community&rel=15?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=network+install&utm_content=download+vs2017) |

Andere unterstützte Bootstrapper sind u.a. [vs_buildtools.exe](https://aka.ms/vs/15/release/vs_buildtools.exe), [vs_feedbackclient.exe](https://aka.ms/vs/15/release/vs_feedbackclient.exe), [vs_teamexplorer.exe](https://aka.ms/vs/15/release/vs_teamexplorer.exe), [vs_testagent.exe](https://aka.ms/vs/15/release/vs_testagent.exe), [vs_testcontroller.exe](https://aka.ms/vs/15/release/vs_testcontroller.exe) und [vs_testprofessional.exe](https://aka.ms/vs/15/release/vs_testprofessional.exe).

## <a name="create-an-offline-installation-folder"></a>Erstellen eines Offlineinstallationsordners

Zum Ausführen dieses Schritts muss Ihr Computer mit dem Internet verbunden sein. Um eine Offlineinstallation mit allen Sprachen und allen Funktionen zu erstellen, verwenden Sie einen der Befehle in den folgenden Beispielen.

   > [!IMPORTANT]
   > Ein vollständiges Visual Studio 2017-Layout erfordert mindestens 35 GB Speicherplatz, und der Download kann einige Zeit in Anspruch nehmen.  Im Abschnitt [Customizing the network layout](#customizing-the-network-layout) (Anpassen des Netzwerklayouts) finden Sie weitere Informationen zum Erstellen eines Layouts, das nur die Komponenten enthält, die Sie installieren möchten.
   >
   > [!TIP]
   > Stellen Sie sicher, dass Sie den Befehl über das Download-Verzeichnis ausführen. Dies ist in der Regel `C:\Users\<username>\Downloads` auf einem Computer, auf dem Windows 10 installiert ist.

- Führen Sie für Visual Studio Enterprise aus:

  ```vs_enterprise.exe --layout c:\vs2017offline```

- Führen Sie für Visual Studio Professional aus:

  ```vs_professional.exe --layout c:\vs2017offline```

- Führen Sie für Visual Studio-Community aus:

  ```vs_community.exe --layout c:\vs2017offline```

## <a name="modify-the-responsejson-file"></a>Ändern der Datei „response.json“

Sie können die Datei „response.json“ zum Festlegen von Standardwerten ändern, die verwendet werden, wenn Setup ausgeführt wird.  Sie können z. B. die Datei `response.json` so konfigurieren, dass eine bestimmte Gruppe von Workloads automatisch ausgewählt wird.
Einzelheiten finden Sie unter [Automatisieren der Visual Studio-Installation mit einer Antwortdatei](automated-installation-with-response-file.md).

## <a name="copy-the-layout-to-a-network-share"></a>Kopieren des Layouts in eine Netzwerkfreigabe

Hosten Sie das Layout in einer Netzwerkfreigabe, damit es auf anderen Computern ausgeführt werden kann.
* Beispiel:<br>
```xcopy /e c:\vs2017offline \\server\products\VS2017```

## <a name="customizing-the-network-layout"></a>Anpassen des Netzwerklayouts

Es gibt mehrere Optionen zum Anpassen Ihres Netzwerklayouts. Sie können ein Teillayout erstellen, das nur eine bestimmte Gruppe von [Gebietsschemas](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales), [Workloads und Komponenten mit ihren empfohlenen oder optionalen Abhängigkeiten](workload-and-component-ids.md) enthält. Dies ist möglicherweise hilfreich, wenn Sie wissen, dass Sie nur eine Teilmenge der Workloads auf Clientarbeitsstationen bereitstellen. Es folgen übliche Befehlszeilenparameter zum Anpassen des Layouts:

* ```--add``` zum Angeben von [Workload- oder Komponenten-IDs](workload-and-component-ids.md).  Wenn `--add` verwendet wird, werden nur die Workloads und Komponenten heruntergeladen, die mit `--add` angegeben sind.  Wenn `--add` nicht verwendet wird, werden alle Workloads und Komponenten heruntergeladen.
* ```--includeRecommended``` zum Einschließen aller empfohlenen Komponenten für die angegebenen Workload-IDs.
* ```--includeOptional``` zum Einschließen aller empfohlenen und optionalen Komponenten für die angegebenen Workload-IDs.
* ```--lang``` zum Angeben von [Gebietsschemas](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales).

Es folgen einige Beispiele, wie ein Teillayout benutzerdefiniert erstellt werden kann.

* Führen Sie zum Herunterladen aller Arbeitsauslastungen und Komponenten für nur eine Sprache Folgendes aus: <br>```vs_enterprise.exe --layout C:\vs2017offline --lang en-US```
* Führen Sie zum Herunterladen aller Arbeitsauslastungen und Komponenten für mehrere Sprachen Folgendes aus: <br>```vs_enterprise.exe --layout C:\vs2017offline --lang en-US de-DE ja-JP```
* Führen Sie zum Herunterladen einer Arbeitsauslastung für alle Sprachen Folgendes aus: <br> ```vs_enterprise.exe --layout C:\vs2017offline --add Microsoft.VisualStudio.Workload.Azure --includeRecommended```
* Führen Sie zum Herunterladen von zwei Arbeitsauslastungen und einer optionalen Komponenten für drei Sprachen Folgendes aus: <br>```vs_enterprise.exe --layout C:\vs2017offline --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeRecommended --lang en-US de-DE ja-JP ```
* Führen Sie Folgendes aus, um zwei Workloads und alle ihre empfohlenen Komponenten herunterzuladen: <br>```vs_enterprise.exe --layout C:\vs2017offline --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeRecommended ```
* Führen Sie Folgendes aus, um zwei Workloads und alle ihre empfohlenen und optionalen Komponenten herunterzuladen: <br>```vs_enterprise.exe --layout C:\vs2017offline --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeOptional ```

### <a name="new-in-153"></a>Neu in 15.3

Wenn Sie einen Layoutbefehl ausführen, werden die Optionen gespeichert, die Sie angeben (z.B. die Workoads und Sprachen). Nachfolgende Layoutbefehle enthalten alle vorherigen Optionen.  Hier ist ein Beispiel für ein Layout mit nur einer Workload für Englisch:

```vs_enterprise.exe --layout c:\VS2017Layout --add Microsoft.VisualStudio.Workload.ManagedDesktop --lang en-US```

Wenn Sie das Layout auf eine neuere Version aktualisieren möchten, müssen Sie keine zusätzlichen Befehlszeilenparameter angeben. Die vorherigen Einstellungen werden gespeichert und durch nachfolgende Layoutbefehle in diesem Layoutordner verwendet.  Der folgende Befehl aktualisiert das vorhandene partielle Layout.

```vs_enterprise.exe --layout c:\VS2017Layout```

Wenn Sie eine zusätzliche Workload hinzufügen möchten, finden Sie hier ein Beispiel. In diesem Fall fügen wir die Azure-Workload und die lokalisierten Sprache hinzu.  Nun sind sowohl der verwaltete Desktop und Azure in diesem Layout enthalten.  Die Sprachressourcen für Englisch und Deutsch sind für all diese Workloads enthalten. Das Layout wird auf die neueste Version aktualisiert.

```vs_enterprise.exe --layout c:\VS2017Layout --add Microsoft.VisualStudio.Workload.Azure --lang de-DE```

Wenn Sie ein vorhandenes Layout auf ein vollständiges Layout aktualisieren möchten, verwenden Sie die Option „--all“, wie im folgenden Beispiel dargestellt.

```vs_enterprise.exe --layout c:\VS2017Layout --all```

## <a name="deploying-from-a-network-installation"></a>Bereitstellen über eine Netzwerkinstallation

Administratoren können Visual Studio auf Clientarbeitsstationen als Teil eines Installationsskripts bereitstellen. Oder Benutzer mit Administratorrechten können das Setup direkt über die Freigabe ausführen, um Visual Studio auf ihrem Computer zu installieren.

- Benutzer müssen für die Installation Folgendes ausführen: <br>```\\server\products\VS2017\vs_enterprise.exe```
- Administratoren können eine Installation im unbeaufsichtigten Modus ausführen, indem Folgendes aufgerufen wird: <br>```\\server\products\VS2017\vs_enterprise.exe --quiet --wait --norestart```

> [!TIP]
> Bei Ausführung als Teil einer Batchdatei wird mit der Option `--wait` sichergestellt, dass der `vs_enterprise.exe`-Prozess wartet, bis die Installation abgeschlossen ist, ehe ein Exitcode zurückgegeben wird. Dies ist hilfreich, wenn ein Unternehmensadministrator weitere Aktionen für vollständige Installation durchführen möchte (z.B. um [einen Product Key auf eine erfolgreiche Installation anzuwenden](automatically-apply-product-keys-when-deploying-visual-studio.md)), aber auf die Beendigung der Installation warten muss, um den Rückgabecode dieser Installation zu verarbeiten.  Wenn Sie `--wait` nicht verwenden, wird der Prozess `vs_enterprise.exe` beendet, bevor die Installation abgeschlossen ist, und gibt ungenauen Exitcode zurück, der den Status des Installationsvorgangs nicht darstellt.

Bei der Installation eines Layout werden die installierten Inhalte aus dem Layout abgerufen. Wenn Sie allerdings eine Komponente auswählen, die im Layout fehlt, wird diese aus dem Internet abgerufen.  Falls Sie verhindern möchten, dass das Visual Studio-Setup alle Inhalte, die in Ihrem Layout fehlen, herunterlädt, verwenden Sie die Option `--noWeb`.  Wenn `--noWeb` verwendet wird und das Layout nicht über alle Inhalte verfügt, die installiert werden sollen, tritt beim Setup ein Fehler auf.

### <a name="error-codes"></a>Fehlercodes

Wenn Sie den Parameter `--wait` nicht verwenden, wird je nach Ergebnis des Vorgangs die Umgebungsvariable `%ERRORLEVEL%` auf einen der folgenden Werte festgelegt:

  | **Wert** | **Ergebnis** |
  | --------- | ---------- |
  | 0 | Der Vorgang wurde erfolgreich abgeschlossen. |
  | 3010 | Der Vorgang wurde erfolgreich abgeschlossen, für die Installation ist jedoch ein Neustart erforderlich, bevor sie verwendet werden kann. |
  | Andere | Es ist ein Fehler aufgetreten – Überprüfen Sie die Protokolle für weitere Informationen |

## <a name="updating-a-network-install-layout"></a>Aktualisieren des Layouts einer Netzwerkinstallation

Wenn Produktupdates verfügbar sind, empfiehlt es sich, [das Layout der Netzwerkinstallation zu aktualisieren](update-a-network-installation-of-visual-studio.md), um aktualisierte Pakete einzubeziehen.

## <a name="how-to-create-a-layout-for-a-previous-visual-studio-2017-release"></a>Gewusst wie: Erstellen eines Layouts für eine frühere Version von Visual Studio 2017

> [!NOTE]
> Die unter [visualstudio.microsoft.com](http://visualstudio.microsoft.com) verfügbaren Visual Studio 2017-Bootstrapper werden heruntergeladen und installieren bei ihrer Ausführung die neueste verfügbare Version von Visual Studio 2017. Wenn Sie einen Visual Studio-Bootstrapper heute herunterladen und erst in sechs Monaten ausführen, wird die Visual Studio 2017-Version installiert, die zu diesem späteren Zeitpunkt verfügbar ist. Wenn Sie ein Layout erstellen, wird bei Installation von Visual Studio über das Layout die Version von Visual Studio installiert, die im Layout vorhanden ist. Obwohl online ggf. eine neuere Version vorhanden ist, erhalten Sie die Version von Visual Studio im Layout.

Wenn Sie ein Layout für eine ältere Version von Visual Studio 2017 erstellen müssen, wechseln Sie zu https://my.visualstudio.com, um „korrigierte“ Versionen der Visual Studio-2017 Bootstrappers herunterzuladen.

### <a name="how-to-get-support-for-your-offline-installer"></a>Gewusst wie: Anfordern von Support für Ihr Offlineinstallationsprogramm

Wenn ein Problem mit der Offlineinstallation auftritt, möchten wir dies erfahren. Die beste Möglichkeit, uns zu informieren, ist die Verwendung des [Problem melden](../ide/how-to-report-a-problem-with-visual-studio-2017.md)-Tools. Wenn Sie dieses Tool verwenden, können Sie uns die Telemetriedaten und Protokolle senden, die wir benötigen, um uns Diagnose und Behebung des Problems zu erleichtern.

Für installationsbezogene Probleme wird außerdem ein [**Livechat**](https://visualstudio.microsoft.com/vs/support/#talktous) (nur auf Englisch) als Supportoption angeboten.

Wir bieten auch noch weitere Supportoptionen. Eine Liste finden Sie auf unserer Seite [Melden eines Problems mit Visual Studio 2017 RC](../ide/how-to-report-a-problem-with-visual-studio-2017.md).

## <a name="see-also"></a>Siehe auch

* [Installieren von Visual Studio](install-visual-studio.md)
* [Administratorhandbuch für Visual Studio 2017 RC](visual-studio-administrator-guide.md)
* [Verwenden von Befehlszeilenparametern zum Installieren von Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Arbeitsauslastung und Komponenten-IDs von Visual Studio](workload-and-component-ids.md)

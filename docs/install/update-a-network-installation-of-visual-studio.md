---
title: Aktualisieren einer netzwerkbasierten Installation
description: Erfahren Sie, wie Sie eine netzwerkbasierte Installation von Visual Studio mit dem Befehl „--layout“ aktualisieren.
ms.date: 08/14/2017
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 1AF69C0E-0AC9-451B-845D-AE4EDBCEA65C
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9159651ea1f7c8890cdf8832a8898743e91bb222
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55937538"
---
# <a name="update-a-network-based-installation-of-visual-studio-2017"></a>Aktualisieren einer netzwerkbasierten Installation von Visual Studio 2017

Es ist möglich, ein Layout für die Netzwerkinstallation von Visual Studio mit den neuesten Produktupdates zu aktualisieren, sodass es sowohl als Installationspfad für das neueste Update von Visual Studio auch zum Warten von Installationen verwendet werden kann, die bereits auf Clientarbeitsstationen bereitgestellt wurden.

## <a name="how-to-update-a-network-layout"></a>Gewusst wie: Aktualisieren eines Netzwerklayouts

Um die Netzwerkinstallationsfreigabe so zu aktualisieren, dass sie die neuesten Updates aufweist, führen Sie den Befehl „--layout“ aus, um aktualisierte Pakete schrittweise herunterzuladen.

Wenn Sie beim Erstellen des Netzwerklayouts ein partielles Layout ausgewählt haben, werden diese Einstellungen gespeichert.  Alle zukünftigen Layoutbefehle verwenden die vorherigen Optionen und alle neuen, die Sie angeben.  (Dies ist neu in Version 15.3.)  Wenn Sie ein Layout einer älteren Version verwenden, sollten Sie dieselben Befehlszeilenparameter verwenden, die Sie beim ersten Erstellen des Layouts für die Netzwerkinstallation verwendet haben (d.h. dieselben Workloads und Sprachen), um den Inhalt zu aktualisieren.

Wenn Sie ein Layout in einer Dateifreigabe hosten, sollten Sie eine private Kopie des Layouts aktualisieren (z.B. c:\vs2017offline) und diese, nachdem alle aktualisierten Inhalte heruntergeladen wurden, in Ihre Dateifreigabe kopieren (z.B. \\server\products\VS2017). Wenn Sie dies nicht tun, ist es wahrscheinlicher, dass Benutzer, die das Setup ausführen, während Sie das Layout aktualisieren, nicht alle Inhalte aus dem Layout erhalten, da es noch nicht vollständig aktualisiert wurde.

Sehen wir uns Schritt für Schritt das Erstellen und Aktualisieren eines Layouts an:

* Hier ist erst einmal ein Beispiel für die Erstellung eines Layouts mit nur einer Workload für Englisch:

  ```cmd
  vs_enterprise.exe --layout c:\VS2017Layout --add Microsoft.VisualStudio.Workload.ManagedDesktop --lang en-US
  ```

* So aktualisieren Sie dasselbe Layout auf eine neuere Version. Sie müssen dazu keine zusätzlichen Befehlszeilenparameter angeben. Die vorherigen Einstellungen wurden gespeichert und werden durch nachfolgende Layoutbefehle in diesem Layoutordner verwendet.

  ```cmd
  vs_enterprise.exe --layout c:\VS2017Layout
  ```

* So ändern Sie Ihr Layout unbeaufsichtigt in eine neuere Version. Der Layoutvorgang führt den Setupprozess in einem neuen Konsolenfenster aus. Das Fenster bleibt geöffnet, sodass sich die Benutzer das endgültige Ergebnis und ggf. eine Zusammenfassung der aufgetretenen Fehler ansehen können. Wenn Sie einen Layoutvorgang unbeaufsichtigt durchführen (wenn Sie z.B. über ein Skript verfügen, das regelmäßig ausgeführt wird, um ihr Layout auf die aktuelle Version zu aktualisieren), verwenden Sie den Parameter `--passive`, und der Vorgang schließt das Fenster automatisch.

  ```cmd
  vs_enterprise.exe --layout c:\VS2017Layout --passive
  ```

* So fügen Sie eine zusätzliche Workload und lokalisierte Sprachen hinzu.  (Mit diesem Befehl wird die Azure-Workload hinzugefügt.)  Nun sind sowohl der verwaltete Desktop und Azure in diesem Layout enthalten.  Die Sprachressourcen für Englisch und Deutsch sind für all diese Workloads enthalten.  Außerdem wird das Layout auf die neueste Version aktualisiert.

  ```cmd
  vs_enterprise.exe --layout c:\VS2017Layout --add Microsoft.VisualStudio.Workload.Azure --lang de-DE
  ```

* Und so wird eine zusätzliche Workload und die lokalisierte Sprache hinzugefügt, ohne die Version zu aktualisieren. (Mit diesem Befehl wird die ASP.NET & Web-Workload hinzugefügt.)  Nun sind der verwaltete Desktop, Azure und die ASP.NET & Web-Workloads in diesem Layout enthalten.  Die Sprachressourcen für Englisch, Deutsch und Französisch sind auch für all diese Workloads enthalten.  Das Layout wurde bei der Ausführung dieses Befehls jedoch nicht auf die neueste verfügbare Version aktualisiert.  Es bleibt weiterhin in der vorhandenen Version.

  ```cmd
  vs_enterprise.exe --layout c:\VS2017Layout --add Microsoft.VisualStudio.Workload.NetWeb --lang fr-FR --keepLayoutVersion
  ```

## <a name="how-to-deploy-an-update-to-client-machines"></a>Gewusst wie: Bereitstellen eines Updates auf Clientcomputern

Je nach Konfiguration Ihrer Netzwerkumgebung kann ein Update entweder von einem Unternehmensadministrator bereitgestellt oder auf einem Clientcomputer ausgelöst werden.

* Benutzer können eine Instanz von Visual Studio aktualisieren, die über einen Offlineinstallationsordner installiert wurde:
  * Führen Sie den Visual Studio-Installer aus.
  * Klicken Sie auf **Aktualisieren**.

* Administratoren können Clientbereitstellungen von Visual Studio ohne Benutzereingriff mit zwei separaten Befehlen aktualisieren:
  * Aktualisieren Sie zunächst den Visual Studio-Installer: <br>```vs_enterprise.exe --quiet --update```
  * Aktualisieren Sie anschließend die Visual Studio-Anwendung selbst: <br>```vs_enterprise.exe update --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" --quiet --wait --norestart```

> [!NOTE]
> Verwenden Sie den Befehl [vswhere.exe](tools-for-managing-visual-studio-instances.md), um den Installationspfad einer vorhandenen Instanz von Visual Studio auf einem Clientcomputer zu bestimmen.
>
> [!TIP]
> Weitere Informationen dazu, wie Sie steuern, wann Updatebenachrichtigungen Benutzern angezeigt werden, finden Sie unter [Steuern von Updates für netzwerkbasierte Visual Studio-Bereitstellungen](controlling-updates-to-visual-studio-deployments.md).

## <a name="how-to-verify-a-layout"></a>Überprüfen eines Layouts

Verwenden Sie `--verify`, um für den angegebenen Offlinecache eine Überprüfung auszuführen. Dabei wird überprüft, ob Paketdateien fehlen oder ungültig sind. Am Ende der Überprüfung wird die Liste der fehlenden und ungültigen Dateien ausgegeben.

```cmd
vs_enterprise.exe --layout <layoutDir> --verify
```

Die Datei „vs_enterprise.exe“ kann innerhalb von „layoutDir“ aufgerufen werden.

> [!NOTE]
> Einige wichtige Metadatendateien, die für die Option `--verify` erforderlich sind, müssen im Layoutofflinecache vorhanden sein. Wenn diese Metadatendateien fehlen, kann "--verify" nicht ausgeführt werden, und das Setup gibt einen Fehler aus. Wenn dieser Fehler bei Ihnen auftritt, erstellen Sie ein neues Offlinelayout in einem anderen Ordner (oder im selben Offlinecacheordner). Führen Sie dazu den gleichen Layoutbefehl aus, mit dem Sie das anfängliche Offlinelayout erstellt haben. Beispielsweise `Vs_enterprise.exe --layout <layoutDir>`.

Microsoft liefert in regelmäßigen Abständen Updates für Visual Studio. Ihr neues Layout hat möglicherweise nicht die gleiche Version wie das anfängliche Layout.

## <a name="how-to-fix-a-layout"></a>Beheben von Problemen mit Layouts

Verwenden Sie `--fix`, um die gleiche Überprüfung wie mit `--verify` durchzuführen, und versuchen Sie außerdem, die identifizierten Probleme zu beheben. Der `--fix`-Prozess benötigt eine Internetverbindung, also stellen Sie sicher, dass Ihr Computer mit dem Internet verbunden ist, bevor Sie `--fix` aufrufen.

```cmd
vs_enterprise.exe --layout <layoutDir> --fix
```

Die Datei „vs_enterprise.exe“ kann innerhalb von „layoutDir“ aufgerufen werden.

## <a name="how-to-remove-older-versions-from-a-layout"></a>Entfernen älterer Versionen aus einem Layout

Nach dem Ausführen von Layoutupdates für einen Offlinecache enthält der Layoutcacheordner möglicherweise einige veraltete Pakete, die für die neueste Visual Studio-Installation nicht mehr gebraucht werden. Sie können die Option `--clean` verwenden, um veraltete Pakete aus einem Offlinecacheordner zu entfernen.

Dazu benötigen Sie die Dateipfade zu den Katalogmanifesten, die diese veralteten Pakete enthalten. Die Katalogmanifeste finden Sie in einem Ordner „Archiv“ im Offlinelayoutcache. Sie werden gespeichert, wenn Sie ein Layout aktualisieren. Im Ordner „Archiv“ befindet sich mindestens ein Ordner namens „GUID“, der jeweils ein veraltetes Katalogmanifest enthält. Die Anzahl der GUID-Ordner sollte der Anzahl der Updates entsprechen, die für Ihren Offlinecache ausgeführt wurden.

Einige Dateien werden in jedem GUID-Ordner gespeichert. Die beiden interessantesten Dateien sind „catalog.json“ und „version.txt“. Die Datei „catalog.json“ ist das veraltete Katalogmanifest, das Sie an die Option `--clean` übergeben müssen. Die andere Datei, „version.txt“, enthält die Version des veralteten Katalogmanifests. Auf Grundlage der Versionsnummer können Sie entscheiden, ob veraltete Pakete aus diesem Katalogmanifest entfernt werden sollen. Sie können diesen Vorgang beim Durchgehen der anderen GUID-Ordner wiederholen. Nachdem Sie entschieden haben, welche Kataloge Sie bereinigen möchten, führen Sie den Befehl `--clean` aus, indem Sie die Dateipfade für diese Kataloge angeben.

Hier sind einige Beispiele für die Verwendung der Option „--clean“:

```cmd
vs_enterprise.exe --layout <layoutDir> --clean <file-path-of-catalog1> <file-path-of-catalog2> …
```

```cmd
vs_enterprise.exe --layout <layoutDir> --clean <file-path-of-catalog1> --clean <file-path-of-catalog2> …
```

Sie können „vs_enterprise.exe“ auch innerhalb von &lt;layoutDir&gt; aufrufen. Im Folgenden ein Beispiel:

```cmd
c:\VS2017Layout\vs_enterprise.exe --layout c:\VS2017Layout --clean c:\VS2017Layout\Archive\1cd70189-fc55-4583-8ad8-a2711e928325\Catalog.json --clean c:\VS2017Layout\Archive\d420889f-6aad-4ba4-99e4-ed7833795a10\Catalog.json
```

Wenn Sie diesen Befehl ausführen, analysiert das Setup Ihren Offlinecacheordner, um die Liste der Dateien zu suchen, die entfernt werden. Sie haben dann die Gelegenheit, die Dateien, die gelöscht werden sollen, zu überprüfen und den Löschvorgang zu bestätigen.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Siehe auch

* [Installieren von Visual Studio](install-visual-studio.md)
* [Administratorhandbuch für Visual Studio 2017 RC](visual-studio-administrator-guide.md)
* [Verwenden von Befehlszeilenparametern zum Installieren von Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Tools zum Erkennen und Verwalten von Visual Studio-Instanzen](tools-for-managing-visual-studio-instances.md)
* [Steuern von Updates für netzwerkbasierte Visual Studio-Bereitstellungen](controlling-updates-to-visual-studio-deployments.md)

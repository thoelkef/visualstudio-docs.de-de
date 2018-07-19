---
title: Installieren von Visual Studio in Umgebungen mit niedriger Bandbreite oder unzuverlässigem Netzwerk | Microsoft-Dokumentation
description: Informationen zur Verwendung des Visual Studio-Installers, wenn Ihr Netzwerk unzuverlässig ist oder Sie über eine niedrige Bandbreite verfügen, und zur Verwendung der Befehlszeile zum Herunterladen von Installationsdateien.
ms.date: 01/17/2018
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- installing Visual Studio
- no internet connection
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1b60df36240b332e74e63aaef7fab75ff19c7d77
ms.sourcegitcommit: 4667e6ad223642bc4ac525f57281482c9894daf4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/20/2018
ms.locfileid: "36297625"
---
# <a name="install-visual-studio-2017-on-low-bandwidth-or-unreliable-network-environments"></a>Installieren von Visual Studio 2017 in Umgebungen mit niedriger Bandbreite oder unzuverlässigem Netzwerk

Sie sollten den Visual Studio-Webinstaller ausprobieren. Er ist in den meisten Fällen die passende Lösung.

 > [!div class="button"]
 > [Visual Studio 2017 herunterladen](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)
<br/>

Wenn Ihre Internetverbindung jedoch unterbrochen wurde oder unzuverlässig ist, können Sie über die Befehlszeile einen lokalen Cache der Dateien erstellen, die Sie für eine Offlineinstallation benötigen. Gehen Sie folgendermaßen vor:

> [!NOTE]
> Wenn Sie Administrator in einem Unternehmen sind und Visual Studio 2017 in einem Netzwerk von Clientarbeitsstationen, die mit einer Firewall geschützt sind, bereitstellen möchten, finden Sie weitere Informationen unter [Erstellen einer Netzwerkinstallation von Visual Studio 2017](../install/create-a-network-installation-of-visual-studio.md) und [Installieren der für eine Offlineinstallation von Visual Studio erforderlichen Zertifikate](../install/install-certificates-for-visual-studio-offline.md).

## <a name="step-1---download-the-visual-studio-bootstrapper"></a>Schritt 1: Herunterladen des Visual Studio-Bootstrappers

Beginnen Sie mit dem Herunterladen des Visual Studio-Bootstrappers für die ausgewählte Edition von Visual Studio.

Ihre Setupdatei, &mdash;oder genauer gesagt eine Bootstrapperdatei &mdash;, entspricht einer der folgenden.

| Edition                    | Datei                                                                    |
|----------------------------|-------------------------------------------------------------------------|
| Visual Studio-Community    | [vs_community.exe](https://aka.ms/vs/15/release/vs_community.exe)       |
| Visual Studio Professional | [vs_professional.exe](https://aka.ms/vs/15/release/vs_professional.exe) |
| Visual Studio Enterprise   | [vs_enterprise.exe](https://aka.ms/vs/15/release/vs_enterprise.exe)     |

## <a name="step-2---create-a-local-install-cache"></a>Schritt 2: Erstellen eines lokalen Installationscaches

Zum Ausführen dieses Schritts muss Ihr Computer mit dem Internet verbunden sein. Zum Erstellen eines lokalen Layouts öffnen Sie eine Eingabeaufforderung, und rufen einen der Befehle in den folgenden Beispielen auf. Bei den hier aufgeführten Beispielen wird davon ausgegangen, dass Sie die Community-Edition von Visual Studio verwenden. Passen Sie den Befehl nach Bedarf für Ihre Edition an.

- Führen Sie für die .NET-Web- und .NET-Desktopentwicklung Folgendes aus:

   ```vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US```

- Führen Sie für die .NET-Desktop- und Office-Entwicklung Folgendes aus:

   ```vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.Office --includeOptional --lang en-US```

- Führen Sie für die C++-Desktopentwicklung Folgendes aus:

   ```vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.NativeDesktop --includeRecommended --lang en-US```

- Führen Sie zum Erstellen eines vollständigen lokalen Layouts mit allen Funktionen Folgendes aus. Hinweis: Das Erstellen nimmt wegen der _umfangreichen_ Funktionen einige Zeit in Anspruch.

   ```vs_community.exe --layout c:\vs2017layout --lang en-US```

Wenn Sie eine andere Sprache als Englisch installieren möchten, ändern Sie `en-US` in ein Gebietsschema in der Liste am unteren Rand dieser Seite. Verwenden Sie diese [Liste verfügbarer Komponenten und Workloads](workload-and-component-ids.md), um bei Bedarf Ihren Installationscache weiter anzupassen.

> [!IMPORTANT]
> Ein vollständiges Visual Studio 2017-Layout erfordert mindestens 35 GB Speicherplatz, und der Download kann einige Zeit in Anspruch nehmen. Weitere Informationen zur Erstellung eines Layouts, das nur die gewünschten Komponenten enthält, finden Sie unter [Verwenden von Befehlszeilenparametern zum Installieren von Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md).

## <a name="step-3---install-visual-studio-from-the-local-cache"></a>Schritt 3: Installieren von Visual Studio über den lokalen Cache

> [!TIP]
> Wenn eine Installation aus einem lokalen Installationscache erfolgt, werden beim Setup die lokalen Versionen dieser Dateien verwendet. Wenn Sie während der Installation jedoch Dateien verwenden, die sich nicht im Cache befinden, wird versucht, sie aus dem Internet herunterzuladen.

Um sicherzustellen, dass Sie nur die Dateien installieren, die Sie heruntergeladen haben, verwenden Sie dieselben Befehlszeilenoptionen, die Sie zum Erstellen des Layoutcaches verwendet haben. Wenn Sie z. B. einen Layoutcache mit dem folgenden Befehl erstellt haben:

```vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US```

Mit dem folgenden Befehl führen Sie die Installation aus:

```c:\vs2017layout\vs_community.exe --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional```

> [!NOTE]
> Wenn eine Fehlermeldung mit dem Hinweis zurückgegeben wird, dass eine Signatur ungültig ist, müssen Sie die aktualisierten Zertifikate installieren. Öffnen Sie den Ordner „Zertifikate“ in Ihrem Offlinecache. Doppelklicken Sie auf jede der Zertifikatdateien, und schließen Sie dann den Zertifikat-Manager-Assistenten ab. Wenn Sie nach einem Kennwort gefragt werden, lassen Sie es leer.

## <a name="list-of-language-locales"></a>Liste der Gebietsschemas

| **Gebietsschema** | **Sprache** |
| ----------------------- | --------------- |
| cs-CZ | Tschechisch |
| de-DE | Deutsch |
| en-US | Englisch |
| es-ES | Spanisch |
| fr-FR | Französisch |
| it-IT | Italienisch |
| ja-JP | Japanisch |
| ko-KR | Koreanisch |
| pl-PL | Polnisch |
| pt-BR | Portugiesisch (Brasilien) |
| ru-RU | Russisch |
| tr-TR | Türkisch |
| zh-CN | Chinesisch (vereinfacht) |
| zh-TW | Chinesisch (traditionell) |

## <a name="get-support"></a>Support aufrufen

Manchmal kann etwas schiefgehen. Wenn bei der Installation von Visual Studio ein Fehler auftritt, lesen Sie den Artikel [Problembehandlung bei Visual Studio 2017-Installations- und -Upgradefehlern](troubleshooting-installation-issues.md). Wenn keiner der Schritte zur Problembehandlung hilfreich ist, können Sie uns per Livechat kontaktieren, um Hilfe bei der Installation zu erhalten (nur in englischer Sprache). Einzelheiten finden Sie auf der [Visual Studio-Supportseite](https://visualstudio.microsoft.com/vs/support/#talktous).

Hier sind einige weitere Supportoptionen:

* Sie können uns über Produktprobleme mit dem Tool [Problem melden](../ide/how-to-report-a-problem-with-visual-studio-2017.md) informieren, das sowohl im Visual Studio-Installer als auch in der Visual Studio-IDE angezeigt wird.
* Sie können uns einen Produktvorschlag unter [UserVoice](https://visualstudio.uservoice.com/forums/121579) mitteilen.
* Sie können Probleme mit Produkten und Antworten in der [Visual Studio-Entwicklercommunity](https://developercommunity.visualstudio.com/) finden.
* Sie können auch über die [Visual Studio-Unterhaltung in der Gitter-Community](https://gitter.im/Microsoft/VisualStudio) Kontakt zu uns oder zu anderen Visual Studio-Entwicklern aufnehmen. (Diese Option erfordert ein [GitHub](https://github.com/)-Konto.)

## <a name="see-also"></a>Siehe auch

* [Installieren von Visual Studio](install-visual-studio.md)
* [Administratorhandbuch für Visual Studio 2017 RC](visual-studio-administrator-guide.md)
* [Verwenden von Befehlszeilenparametern zum Installieren von Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Arbeitsauslastungs- und Komponenten-IDs von Visual Studio 2017](workload-and-component-ids.md)

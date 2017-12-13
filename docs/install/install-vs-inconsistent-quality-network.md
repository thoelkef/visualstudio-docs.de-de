---
title: "Installieren von Visual Studio in Umgebungen mit niedriger Bandbreite oder unzuverlässigem Netzwerk | Microsoft-Dokumentation"
description: "Beschreibt die Funktionsweise des Visual Studio-Installationsprogramms in Umgebungen mit unzuverlässigem Netzwerk und erläutert das Herunterladen von Installationsdateien vor dem Starten der Installation."
ms.date: 08/30/2017
ms.reviewer: tims
ms.suite: 
ms.technology: vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 44DB1998-68CD-4560-870A-EE5B993DCF6E
author: timsneath
ms.author: tims
manager: ghogen
ms.openlocfilehash: 57665c39c875b57a1e90c4f57de68f069823cc86
ms.sourcegitcommit: 26419ab0cccdc30d279c32d6a841758cfa903806
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/11/2017
---
# <a name="install-visual-studio-2017-on-low-bandwidth-or-unreliable-network-environments"></a>Installieren von Visual Studio 2017 in Umgebungen mit niedriger Bandbreite oder unzuverlässigem Netzwerk

Sie sollten den Visual Studio-Webinstaller ausprobieren. Er ist in den meisten Fällen die passende Lösung.

 > [!div class="button"]
 > [Herunterladen von Visual Studio 2017](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocsOL)
<br/>

Wenn Ihre Internetverbindung jedoch unterbrochen wurde oder unzuverlässig ist, können Sie über die Befehlszeile einen lokalen Cache der Dateien erstellen, die Sie für eine Offlineinstallation benötigen. Gehen Sie folgendermaßen vor:

> [!NOTE]
> Wenn Sie Administrator in einem Unternehmen sind und Visual Studio 2017 in einem Netzwerk von Clientarbeitsstationen, die mit einer Firewall geschützt sind, bereitstellen möchten, finden Sie weitere Informationen unter [Erstellen einer Netzwerkinstallation von Visual Studio 2017](../install/create-a-network-installation-of-visual-studio.md) und [Besonderheiten bei der Installation von Visual Studio in einer Offlineumgebung](../install/install-visual-studio-in-offline-environment.md).

## <a name="step-1---download-the-visual-studio-bootstrapper"></a>Schritt 1: Herunterladen des Visual Studio-Bootstrappers

Beginnen Sie mit dem Herunterladen des Visual Studio-Bootstrappers für die ausgewählte Edition von Visual Studio.

Ihre Setupdatei, &mdash;oder genauer gesagt eine Bootstrapperdatei &mdash;, entspricht einer der folgenden.

| Edition                    | Datei                                                                    |
|----------------------------|-------------------------------------------------------------------------|
| Visual Studio-Community    | [vs_community.exe](https://aka.ms/vs/15/release/vs_community.exe)       |
| Visual Studio Professional | [vs_professional.exe](https://aka.ms/vs/15/release/vs_professional.exe) |
| Visual Studio Enterprise   | [vs_enterprise.exe](https://aka.ms/vs/15/release/vs_enterprise.exe)     |

## <a name="step-2---create-a-local-install-cache"></a>Schritt 2: Erstellen eines lokalen Installationscaches

Zum Ausführen dieses Beispiels muss Ihr Computer eine Internetverbindung haben. Öffnen Sie zum Erstellen eines lokalen Layouts eine Eingabeaufforderung, und geben Sie einen der folgenden Befehle ein. In diesen Beispielen wird vorausgesetzt, dass Sie die Community-Version von Visual Studio verwenden. Passen Sie den Befehl also Ihrer Edition entsprechend an.

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
Manchmal kann etwas schiefgehen. Wenn die Installation von Visual Studio fehlschlägt, lesen Sie den Artikel [Problembehandlung bei der Visual Studio 2017-Installation und Upgradefehlern](troubleshooting-installation-issues.md), um Hilfe bei der Problemlösung zu erhalten. Sie können uns außerdem über das Tool [Ein Problem melden](../ide/how-to-report-a-problem-with-visual-studio-2017.md) in der Visual Studio-IDE oder über [UserVoice](https://visualstudio.uservoice.com/forums/121579) Probleme und Vorschläge mitteilen. Sie können Probleme mit Produkten im Portal [Visual Studio Developer Community](https://developercommunity.visualstudio.com/) im Blick behalten, Fragen stellen und Antworten finden. Über die [Visual Studio-Unterhaltung in der Gitter-Community](https://gitter.im/Microsoft/VisualStudio) können Sie Kontakt zu uns oder anderen Visual Studio-Entwicklern aufnehmen ([GitHub](https://github.com/)-Konto erforderlich).

## <a name="see-also"></a>Siehe auch
* [Installieren von Visual Studio](install-visual-studio.md)
* [Administratorhandbuch für Visual Studio 2017 RC](visual-studio-administrator-guide.md)
* [Verwenden von Befehlszeilenparametern zum Installieren von Visual Studio](use-command-line-parameters-to-install-visual-studio.md)

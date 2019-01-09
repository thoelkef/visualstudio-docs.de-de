---
title: Private Daten in Problemberichten
ms.date: 06/21/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- developer community privacy
- privacy, developer community
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c98747a4ad1d37d7a8b0d8cc51b4e1ddbd851663
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53895765"
---
# <a name="developer-community-data-privacy"></a>Datenschutz in der Developer Community

Standardmäßig sind sämtliche Informationen in Problemberichten der [Entwicklercommunity](https://developercommunity.visualstudio.com/), Kommentare und Antworten inbegriffen, öffentlich sichtbar. Dies ist ein Vorteil, da die gesamte Community Einblicke in die Probleme, Lösungen und Problemumgehungen anderer Benutzer hat. Wenn Sie um den Datenschutz Ihrer Daten oder Ihrer Identität besorgt sind, gibt es jedoch auch andere Optionen.

## <a name="identity-privacy"></a>Identitätsschutz

Wenn Sie Ihre Identität nicht offenlegen möchten, [erstellen Sie ein neues Microsoft-Konto](https://signup.live.com/), das keine personenbezogenen Informationen enthält. Verwenden Sie dieses Konto, um Ihren Bericht zu erstellen.

## <a name="data-privacy"></a>Datenschutz

Wenn Sie um den Datenschutz besorgt sind, fügen Sie keine Informationen, die privat bleiben sollen, in den Titel oder den Inhalt des ursprünglichen Berichts ein, denn dieser ist immer öffentlich. Erstellen Sie stattdessen den Bericht, und achten Sie anschließend darauf, dass Sie die Details privat in einem separaten Kommentar senden. Sobald der Problembericht erstellt wurde, können Sie angeben, wer Ihre Antworten und Anlagen anzeigen darf:

1. Klicken Sie im erstellten Bericht auf **Kommentar hinzufügen**, um eine private Beschreibung des Problems zu erstellen.

2. Verwenden Sie im Antwort-Editor das Steuerelement unter den Schaltflächen **Senden** und **Abbrechen**, um die Zielgruppe für Ihre Antwort anzugeben. Wählen Sie **Viewable by moderators and the original poster** (Sichtbar für Moderatoren und den Verfasser) aus, um die Sichtbarkeit auf Microsoft-Mitarbeiter und sich selbst zu beschränken.

   ![Datenschutz-Steuerelement in der Entwicklercommunity](media/developer-community-privacy-control.png)

   Nur die von Ihnen angegebenen Personen können die Kommentare sowie darin enthaltene Bilder, Links und Code anzeigen. Sämtliche Antworten unter dem Kommentar weisen die gleiche Sichtbarkeit wie der ursprüngliche Kommentar auf. Dies gilt auch dann, wenn das Datenschutz-Steuerelement den Status der eingeschränkten Sichtbarkeit nicht korrekt anzeigt.

3. Fügen Sie die Beschreibung und weitere erforderliche Informationen, Bilder und Dateianlagen für die Reproduktion hinzu. Klicken Sie auf die Schaltfläche **Senden**, um diese Informationen privat zu senden.

   > [!NOTE]
   > Es gibt einen Grenzwert von maximal 10 Dateien und maximal 2 GB in angehängten Dateien. Wenn Sie eine größere Datei hochladen müssen, können Sie einen neuen Problembericht senden oder in einem privaten Kommentar bei einem Microsoft-Mitarbeiter eine Upload-URL anfordern.

Wenn Sie Ihre Privatsphäre schützen und vertrauliche Daten nicht veröffentlichen möchten, sollte die gesamte Interaktion mit Microsoft unter einem Kommentar mit eingeschränkter Sichtbarkeit stattfinden. Antworten auf andere Kommentare können dazu führen, dass Sie versehentlich vertrauliche Informationen offenlegen.

## <a name="data-we-collect"></a>Erfasste Daten

Wenn der Visual Studio-Installer den Vorgang **Problem melden** einleitet, wird das aktuelle Setupprotokoll erfasst.

Wenn Visual Studio den Vorgang **Problem melden** einleitet, wird mindestens einer der folgenden Datentypen erfasst:

- Watson- und .NET-Einträge aus dem Ereignisprotokoll

- Visual Studio-Aktivitätsprotokolldatei im Arbeitsspeicher

- PerfWatson-Dateien, wenn die Watson-Sammlung aktiviert ist, aus dem Ordner *VSFeedbackPerfWatsonData*

- LiveShare-Protokolldateien, sofern vorhanden, aus dem Ordner *VSFeedbackVSRTCLogs*

- Xamarin-Protokolldateien, sofern vorhanden, aus *%LOCALAPPDATA%\Xamarin\Logs*

- NuGet-Protokolldateien, sofern vorhanden, aus *%TEMP%\NuGetScratch\nuget-dg\nugetSpec.dg*

- Webdebugger-Protokolldateien, sofern vorhanden:

   - *%TEMP%\vscode-chrome-debug.txt*

   - *%TEMP%\vscode-node-debug2.txt*

   - *%TEMP%\vscode-edge-debug.txt*

- Ein Screenshot, sofern dieser einbezogen werden soll

- Aufzeichnungsdaten, sofern eine Aufzeichnung einbezogen werden soll. Diese umfassen:

   - Schritte zum Reproduzieren des Problems

   - ETL-Ablaufverfolgungsdatei

   - Dumpdatei

    > [!NOTE]
    > Sie können vor dem Senden des Berichts sämtliche Aufzeichnungsdaten löschen, die nicht gesendet werden sollen.

## <a name="see-also"></a>Siehe auch

- [Melden eines Problems mit Visual Studio](how-to-report-a-problem-with-visual-studio-2017.md)
- [Datenschutz in C++-Problemberichten](/cpp/how-to-report-a-problem-with-the-visual-cpp-toolset#reports-and-privacy)
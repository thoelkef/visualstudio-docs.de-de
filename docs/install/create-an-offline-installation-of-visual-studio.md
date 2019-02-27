---
title: Erstellen einer Offlineinstallation
description: Erfahren Sie, wie Sie Visual Studio offline installieren können, wenn Sie über eine unzuverlässige Internetverbindung oder eine geringe Bandbreite verfügen.
ms.date: 02/23/2019
ms.custom: seodec18
ms.topic: conceptual
f1_keywords:
- offline installation [Visual Studio]
- offline install [Visual Studio]
- layout [Visual Studio]
ms.assetid: f8625d5e-f6ea-4db0-83c0-619b77fab3cf
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b33e08e8aa639540461216b057ae80d1eb7701f6
ms.sourcegitcommit: 1c8e07b98fc0a44b5ab90bcef77d9fac7b3eb452
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/25/2019
ms.locfileid: "56796542"
---
# <a name="create-an-offline-installation-of-visual-studio-2017"></a>Erstellen einer Offlineinstallation von Visual Studio 2017

Visual Studio 2017 wurde so gestaltet, dass es unter verschiedensten Netzwerk- und Computerbedingungen gut funktioniert. Obwohl empfohlen wird, den [Visual Studio-Webinstaller](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) zu verwenden – bei dem es sich um eine kleine Datei handelt und durch den Sie mit den neuesten Fehlerbehebungen und Features auf dem Laufenden bleiben können – ist es Ihnen unter Umständen nicht möglich, diesen zu nutzen.

Gründe hierfür können eine unzuverlässige Internetverbindung oder eine Verbindung mit geringer Bandbreite sein. Falls dies der Fall sein sollte, haben Sie die folgenden Möglichkeiten: Sie können die neue Funktion „Download all, then install“ (Alles herunterladen, dann installieren) verwenden, um die Dateien vor der Installation herunterzuladen, oder Sie können über die Befehlszeile einen lokalen Cache für die Dateien erstellen.

> [!NOTE]
> Wenn Sie Administrator in einem Unternehmen sind und Visual Studio 2017 in einem Netzwerk von Clientarbeitsstationen, die mit einer Firewall geschützt sind, bereitstellen möchten, finden Sie weitere Informationen unter [Erstellen einer Netzwerkinstallation von Visual Studio 2017](../install/create-a-network-installation-of-visual-studio.md) und [Installieren der für eine Offlineinstallation von Visual Studio erforderlichen Zertifikate](../install/install-certificates-for-visual-studio-offline.md).

## <a name="use-the-download-all-then-install-feature"></a>Verwenden der Funktion „Download all, then install“ (Alles herunterladen, dann installieren)

[**Neues in 15.8:**](/visualstudio/releasenotes/vs2017-relnotes-v15.8#install) Nachdem Sie den Webinstaller heruntergeladen haben, wählen Sie im Visual Studio-Installer die neue Option **Download all, then install** (Alles herunterladen, dann installieren) aus. Anschließend fahren Sie mit der Installation fort.

   ![Die Option „Download all, then install“ (Alles herunterladen, dann installieren)](media/download-all-then-install.png)

Das „Alles herunterladen, dann installieren“-Feature wurde so gestaltet, dass Sie Visual Studio als einzelne Installation für denselben Computer herunterladen können, auf den Sie es heruntergeladen haben. Auf diese Weise können Sie sich vor der Installation von Visual Studio problemlos vom Internet trennen.

> [!IMPORTANT]
> Verwenden Sie das „Alles herunterladen, dann installieren“-Feature nicht zum Erstellen eines Offlinecaches, den Sie auf einen anderen Computer übertragen möchten. Hierfür ist es nicht vorgesehen. <br><br>Wenn Sie einen Offlinecache erstellen möchten, um Visual Studio auf einem anderen Computer zu installieren, finden Sie im Abschnitt [Verwenden der Befehlszeile zum Erstellen eines lokalen Caches](#use-the-command-line-to-create-a-local-cache) dieser Seite Informationen zum Erstellen eines lokalen Caches, oder auf der Seite [Erstellen einer Netzwerkinstallation von Visual Studio 2017](../install/create-a-network-installation-of-visual-studio.md) Informationen zum Erstellen eines Netzwerkcaches.

## <a name="use-the-command-line-to-create-a-local-cache"></a>Verwenden der Befehlszeile zum Erstellen eines lokalen Caches

Nachdem Sie einen kleinen Bootstrapper heruntergeladen haben, erstellen Sie über die Befehlszeile einen lokalen Cache. Dann installieren Sie Visual Studio über den lokalen Cache. (Dieser Vorgang ersetzt die ISO-Dateien, die in vorherigen Versionen genutzt wurden.)

Gehen Sie folgendermaßen vor:

### <a name="step-1---download-the-visual-studio-bootstrapper"></a>Schritt 1: Herunterladen des Visual Studio-Bootstrappers

Zum Ausführen dieses Schritts muss Ihr Computer mit dem Internet verbunden sein.

Beginnen Sie mit dem Herunterladen des Visual Studio-Bootstrappers für die ausgewählte Edition von Visual Studio. Ihre Setupdatei, d.h. Ihre Bootstrapperdatei, entspricht oder ähnelt einer der folgenden.

| Edition                    | Datei                                                                    |
|----------------------------|-------------------------------------------------------------------------|
| Visual Studio-Community    | [vs_community.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=community&rel=15&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2017)       |
| Visual Studio Professional | [vs_professional.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=professional&rel=15&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2017) |
| Visual Studio Enterprise   | [vs_enterprise.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=enterprise&rel=15&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2017)     |

### <a name="step-2---create-a-local-install-cache"></a>Schritt 2: Erstellen eines lokalen Installationscaches

Zum Ausführen dieses Schritts muss Ihr Computer mit dem Internet verbunden sein.

> [!IMPORTANT]
> Wenn Sie Visual Studio Community 2017 installieren, müssen Sie die Anwendung innerhalb von 30 Tagen nach der Installation aktivieren. Dazu ist eine Internetverbindung erforderlich.

Öffnen Sie eine Eingabeaufforderung, und rufen Sie einen der Befehle in den folgenden Beispielen auf. Bei den hier aufgeführten Beispielen wird davon ausgegangen, dass Sie die Community-Edition von Visual Studio verwenden. Passen Sie den Befehl nach Bedarf für Ihre Edition an.

> [!TIP]
> Um Fehler zu vermeiden, darf Ihr vollständiger Installationspfad nicht mehr 80 Zeichen enthalten.

- Führen Sie für die .NET-Web- und .NET-Desktopentwicklung Folgendes aus:

   ```cmd
    vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US
    ```

- Führen Sie für die .NET-Desktop- und Office-Entwicklung Folgendes aus:

   ```cmd
    vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.Office --includeOptional --lang en-US
    ```

- Führen Sie für die C++-Desktopentwicklung Folgendes aus:

   ```cmd
    vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.NativeDesktop --includeRecommended --lang en-US
    ```

- Führen Sie zum Erstellen eines vollständigen lokalen Layouts mit allen Funktionen Folgendes aus. Hinweis: Das Erstellen nimmt wegen der _umfangreichen_ Funktionen einige Zeit in Anspruch.

   ```cmd
    vs_community.exe --layout c:\vs2017layout --lang en-US
    ```

  > [!NOTE]
  > Ein vollständiges Visual Studio 2017-Layout erfordert mindestens 35 GB Speicherplatz. Weitere Informationen zur Erstellung eines Layouts, das nur die gewünschten Komponenten enthält, finden Sie unter [Verwenden von Befehlszeilenparametern zum Installieren von Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md).

Wenn Sie eine andere Sprache als Englisch installieren möchten, ändern Sie `en-US` in das gewünschte Gebietsschema aus der [Liste der Gebietsschemas](#list-of-language-locales). Verwenden Sie dann die [Liste verfügbarer Komponenten und Workloads](workload-and-component-ids.md), um Ihren Installationscache weiter anzupassen.

### <a name="step-3---install-visual-studio-from-the-local-cache"></a>Schritt 3: Installieren von Visual Studio über den lokalen Cache

> [!TIP]
> Wenn eine Installation aus einem lokalen Installationscache erfolgt, werden beim Setup die lokalen Versionen dieser Dateien verwendet. Wenn Sie während der Installation jedoch Komponenten verwenden, die sich nicht im Cache befinden, wird versucht, sie aus dem Internet herunterzuladen.

Um sicherzustellen, dass Sie nur die Dateien installieren, die Sie zuvor heruntergeladen haben, verwenden Sie dieselben Befehlszeilenoptionen, die Sie zum Erstellen des Layoutcaches verwendet haben. Wenn Sie z. B. einen Layoutcache mit dem folgenden Befehl erstellt haben:

```cmd
vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US
```

Anschließend führen Sie mit dem folgenden Befehl die Installation aus:

```cmd
c:\vs2017layout\vs_community.exe --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional
```

> [!NOTE]
> Wenn eine Fehlermeldung mit dem Hinweis zurückgegeben wird, dass eine Signatur ungültig ist, müssen Sie die aktualisierten Zertifikate installieren. Öffnen Sie den Ordner „Zertifikate“ in Ihrem Offlinecache. Doppelklicken Sie auf jede der Zertifikatdateien, und schließen Sie dann den Zertifikat-Manager-Assistenten ab. Wenn Sie nach einem Kennwort gefragt werden, lassen Sie es leer.

### <a name="list-of-language-locales"></a>Liste der Gebietsschemas

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

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Siehe auch

- [Erstellen einer Netzwerkinstallation von Visual Studio 2017](../install/create-a-network-installation-of-visual-studio.md)
- [Installieren der für eine Offlineinstallation von Visual Studio erforderlichen Zertifikate](../install/install-certificates-for-visual-studio-offline.md)
- [Verwenden von Befehlszeilenparametern zum Installieren von Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
- [Arbeitsauslastungs- und Komponenten-IDs von Visual Studio 2017](workload-and-component-ids.md)

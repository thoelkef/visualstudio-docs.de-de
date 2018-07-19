---
title: Erstellen einer Offlineinstallation von Visual Studio
description: Hier erfahren Sie, wie Sie Visual Studio offline installieren können.
ms.custom: ''
ms.date: 01/17/2018
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- offline installation [Visual Studio]
- offline install [Visual Studio]
- layout [Visual Studio]
ms.assetid: f8625d5e-f6ea-4db0-83c0-619b77fab3cf
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1ef917b4e8aa5cde8d95c036523bb525799cc19e
ms.sourcegitcommit: 4667e6ad223642bc4ac525f57281482c9894daf4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/20/2018
ms.locfileid: "36279962"
---
# <a name="create-an-offline-installation-of-visual-studio-2017"></a>Erstellen einer Offlineinstallation von Visual Studio 2017

Das Visual Studio 2017-Installationsprogramm wurde so gestaltet, dass es unter verschiedensten Netzwerk- und Computerbedingungen gut funktioniert.

- Durch das neue workloadbasierte Modell müssen Sie weit weniger Inhalt herunterladen als bei früheren Versionen von Visual Studio. Für die kleinste Installation müssen Sie z.B. nur 300 MB herunterladen.
- Im Vergleich zu einer generischen ISO- oder ZIP-Datei müssen Sie nur die Pakete herunterladen, die Sie auf Ihrem Computer benötigen. Es werden z.B. keine 64-Bit-Dateien heruntergeladen, wenn Sie diese nicht benötigen.
- Währen des Installationsvorgangs probieren wir drei Downloadtechnologien (WebClient, BITS und WinInet) aus, um Störungen durch Antiviren- und Proxysoftware zu minimieren.
- Die Dateien, die Sie für die Installation von Visual Studio benötigen, werden an ein globales Übermittlungsnetzwerk verteilt, sodass Sie sie von einem lokalen Server abrufen können.

Probieren Sie den [Visual Studio-Webinstaller](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) aus, und überzeugen Sie sich selbst.

 > [!div class="button"]
 > [Visual Studio 2017 herunterladen](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)

Wenn Sie eine Offlineinstallation durchführen möchten, weil Sie nicht mit dem Internet verbunden sind oder die Verbindung unzuverlässig ist, finden Sie weitere Informationen unter [Installieren von Visual Studio 2017 in Umgebungen mit niedriger Bandbreite oder unzuverlässigem Netzwerk](../install/install-vs-inconsistent-quality-network.md). Sie können über die Befehlszeile einen lokalen Cache der Dateien erstellen, die Sie für eine Offlineinstallation benötigen. Dieser Vorgang ersetzt die ISO-Dateien, die Sie in vorherigen Versionen herunterladen mussten.

> [!NOTE]
> Wenn Sie Administrator in einem Unternehmen sind und Visual Studio 2017 in einem Netzwerk von Clientarbeitsstationen, die mit einer Firewall geschützt sind, bereitstellen möchten, finden Sie weitere Informationen unter [Erstellen einer Netzwerkinstallation von Visual Studio 2017](../install/create-a-network-installation-of-visual-studio.md) und [Installieren der für eine Offlineinstallation von Visual Studio erforderlichen Zertifikate](../install/install-certificates-for-visual-studio-offline.md).

## <a name="get-support"></a>Support aufrufen

Manchmal kann etwas schiefgehen. Wenn bei der Installation von Visual Studio ein Fehler auftritt, lesen Sie den Artikel [Problembehandlung bei Visual Studio 2017-Installations- und -Upgradefehlern](troubleshooting-installation-issues.md). Wenn keiner der Schritte zur Problembehandlung hilfreich ist, können Sie uns per Livechat kontaktieren, um Hilfe bei der Installation zu erhalten (nur in englischer Sprache). Einzelheiten finden Sie auf der [Visual Studio-Supportseite](https://visualstudio.microsoft.com/vs/support/#talktous).

Hier sind einige weitere Supportoptionen:

* Sie können uns über Produktprobleme mit dem Tool [Problem melden](../ide/how-to-report-a-problem-with-visual-studio-2017.md) informieren, das sowohl im Visual Studio-Installer als auch in der Visual Studio-IDE angezeigt wird.
* Sie können uns einen Produktvorschlag unter [UserVoice](https://visualstudio.uservoice.com/forums/121579) mitteilen.
* Sie können Probleme mit Produkten und Antworten in der [Visual Studio-Entwicklercommunity](https://developercommunity.visualstudio.com/) finden.
* Sie können auch über die [Visual Studio-Unterhaltung in der Gitter-Community](https://gitter.im/Microsoft/VisualStudio) Kontakt zu uns oder zu anderen Visual Studio-Entwicklern aufnehmen. (Diese Option erfordert ein [GitHub](https://github.com/)-Konto.)

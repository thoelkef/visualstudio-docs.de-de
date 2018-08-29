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
ms.openlocfilehash: d19eabe10234ca2a1670ae04f99a45a85a6cac14
ms.sourcegitcommit: 6b092e7d466377f06913d49d183dbbdca16730f0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/28/2018
ms.locfileid: "43138876"
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

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

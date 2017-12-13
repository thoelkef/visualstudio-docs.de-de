---
title: "Visual Studio-Tools für Unity – Exemplarische Vorgehensweise (Azure) Microsoft-Dokumentation"
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7921D4C7-5526-42F5-8E03-82D3E33A893F
author: dantogno
ms.author: v-davian
manager: crdun
ms.openlocfilehash: a7e12508537a3bcda1df7997ba9e390b75b9beaf
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2017
---
# <a name="using-azure-easy-tables-with-unity-walkthrough"></a>Exemplarische Vorgehensweise zur Verwendung von Azure-Easy-Tabellen mit Unity

![Screenshot eines Spielbeispiels](media/vstu_azure-test-sample-game-image2.png)

## <a name="introduction"></a>Einführung

Azure bietet eine skalierbare Lösung zum Speichern von Telemetriedaten und anderen Spieledaten in der Cloud. Mit der Veröffentlichung von Unity 2017 wird die Azure-Integration durch die Unterstützung von Unity für .NET 4.6 so einfach wie nie, da die Verwendung des Azure Mobile Client SDK zugelassen wird.

Diese Schritte führen Sie durch die Einrichtung eines Unity-Projekts, das Azure für die Speicherung von Telemetrie- und Bestenlistendaten in der Cloud nutzt.

> [!NOTE]
> Dieses Projekt erfordert die „experimentelle“ .NET 4.6-Mono-Skriptruntime in Unity 2017. [Unity hat angekündigt, dass diese bald Standard sein wird](https://forum.unity3d.com/threads/future-plans-for-the-mono-runtime-upgrade.464327/). Aktuell wird die Runtime jedoch als „experimentell“ bezeichnet, und es können Fehler auftreten.

> Diese exemplarische Vorgehensweise dokumentiert ein Beispiel für die Herstellung einer Verbindung zu einem Back-End einer mobilen Azure-App von einem Unity-PC-Build aus. Zum Zeitpunkt der Erstellung dieses Dokuments gibt es bekannte Probleme, die dazu führen, dass dieses Projekt nicht auf Mac- und Android-Plattformen ausgeführt werden kann. Dies sind bekannte Probleme, die behoben werden, jedoch ist es nicht ersichtlich, wie lange dies dauern wird. Weitere Informationen finden Sie im [Forum für experimentelle Skripts](https://forum.unity3d.com/forums/experimental-scripting-previews.107/) für Unity.

## <a name="download-the-completed-project"></a>Herunterladen des abgeschlossenen Projekts

Das abgeschlossene Projekt ist auf GitHub verfügbar. In der exemplarischen Vorgehensweise wird jedoch davon ausgegangen, dass Sie mit einem leeren neuen Projekt beginnen. Es werden wenn nötig Links zum Download von Objekten bereitgestellt.

## <a name="walkthrough-steps"></a>Schritte für die exemplarische Vorgehensweise

1. [Konfigurieren einfacher Tabellen in Azure](visual-studio-tools-for-unity-azure-configure.md)
2. [Erstellen einfacher Tabellen](visual-studio-tools-for-unity-azure-setup.md)
3. [Vorbereiten der Entwicklungsumgebung](visual-studio-tools-for-unity-azure-prepare.md)
4. [Erstellen von Datenmodellklassen](visual-studio-tools-for-unity-azure-data.md)
5. [Implementieren des Azure MobileServiceClient](visual-studio-tools-for-unity-azure-mobile-client.md)
6. [Aktualisieren des Unity Mono-Sicherheitszertifikatspeichers](visual-studio-tools-for-unity-azure-security.md)
7. [Testen der Clientverbindung](visual-studio-tools-for-unity-azure-connection.md)
7. [Importieren von Beispielspielressourcen](visual-studio-tools-for-unity-azure-game-assets.md)
8. [Testen des Beispielspiels](visual-studio-tools-for-unity-azure-game.md)
9. [Erläuterung von RaceScene](visual-studio-tools-for-unity-azure-racescene.md)
10. [Erläuterung von HeatmapScene](visual-studio-tools-for-unity-azure-heatmapscene.md)
11. [Erläuterung zu LeaderboardScene](visual-studio-tools-for-unity-azure-leaderboardscene.md)


## <a name="next-step"></a>Nächster Schritt
* [Konfigurieren einfacher Tabellen in Azure](visual-studio-tools-for-unity-azure-configure.md)

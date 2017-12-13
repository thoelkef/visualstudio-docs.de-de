---
title: "Visual Studio-Tools für Unity: Spielobjekt – Exemplarische Vorgehensweise (Azure) | Microsoft-Dokumentation"
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: C06FAB2E-F592-4EFF-B96A-58858C92DCEB
author: dantogno
ms.author: v-davian
manager: crdun
ms.openlocfilehash: 3b1ad3d7dc6af48986e8b10278a8b8135843239d
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2017
---
# <a name="import-sample-game-assets"></a>Importieren von Beispielspielobjekten

Die Hauptfunktion wurde getestet und ist funktionstüchtig: Jetzt können Sie Beispielspielobjekte importieren.

## <a name="import-package"></a>Importieren eines Pakets

1. Laden Sie das [Paket mit Beispielspielobjekten](https://github.com/dantogno/UnityAzureSample/blob/master/Azure%20Easy%20tables%20sample%20game%20assets.unitypackage) herunter.

2. Achten Sie darauf, dass Ihr Unity-Projekt geöffnet ist, und navigieren Sie dann zum Speicherort des Downloads, und doppelklicken Sie auf die Datei. Dann wird das Dialogfeld „Importieren“ in Unity geöffnet.

3. Klicken Sie auf **All** (Alle) und anschließend auf **Import** (Importieren). Warten Sie, bis der Vorgang abgeschlossen ist (dies erkennen Sie an der Statusanzeige).

  ![Importieren eines Pakets](media/vstu_azure-import-sample-assets-image1.png)

## <a name="add-scenes-to-build-settings"></a>Hinzufügen von Szenen in den Buildeinstellungen

Sobald der Import der Dateien abgeschlossen ist, müssen die erforderlichen Szenendateien zu den Buildeinstellungen des Unity-Projekts hinzugefügt werden.

1. Navigieren Sie im Unity-Projektfenster zum Verzeichnis **Assets/Azure Easy Tables sample game assets/Scenes**.

2. Klicken Sie im Unity-Menü auf **Datei > Buildeinstellungen**. Dann wird das Dialogfeld „Buildeinstellungen“ geöffnet.

3. Ziehen Sie die Dateien **HeatmapScene**, **LeaderboardScene**, **MenuScene** und **RaceScene** aus dem Projektfenster in den Bereich **Scenes In Build** (Szenen im Build) im Dialogfeld „Buildeinstellungen“.

  ![Importieren eines Pakets](media/vstu_azure-import-sample-assets-image2.png)

4. Klicken Sie im Unity-Menü auf **Datei > Projekt speichern**, um die Buildeinstellungen zu speichern.

## <a name="next-step"></a>Nächster Schritt

* [Testen des Beispielspiels](visual-studio-tools-for-unity-azure-game.md)
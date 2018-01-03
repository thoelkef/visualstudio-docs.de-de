---
title: "Visual Studio-Tools für Unity: Spiel – Exemplarische Vorgehensweise (Azure) | Microsoft-Dokumentation"
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: DA86FC7F-E456-4DFC-84BF-D780421508B9
author: dantogno
ms.author: v-davian
manager: crdun
ms.workload:
- azure
- unity
ms.openlocfilehash: 7d0a7da4093b8f90ab76dee55f1ec9ad6dc21679
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="test-the-sample-game"></a>Testen des Beispielspiels

Das Beispielspiel ist ein einfaches Rennspiel, das Daten über das Spielerverhalten aufzeichnet und diese in „Einfache Tabellen“ von Azure speichert. Das Beispielspiel enthält außerdem Szenen, die die Daten aus Azure lesen und für den Spieler darstellen.

In diesem Abschnitt wird erläutert, wie das Beispielspiel gespielt wird und sichergestellt, dass es korrekt funktioniert. Die nächsten Abschnitte erläutern ausführlicher, wie das Beispielspiel funktioniert.

## <a name="starting-the-game"></a>Starten des Spiels

1. Navigieren Sie im Unity-Projektfenster zum Ordner **Assets/Azure Easy Tables sample game assets/Scenes**.

2. Doppelklicken Sie auf **MenuScene**, um ihn zu öffnen.

3. Klicken Sie im Unity-Spielefenster auf die Dropdownliste **Seitenverhältnis**, und wählen Sie **16:9**.

  ![Festlegen des Seitenverhältnisses](media/vstu_azure-test-sample-game-image1.png)

4. Klicken Sie auf die Schaltfläche **Play** (Spielen), um das Spiel im Unity-Editor auszuführen.


## <a name="complete-a-race"></a>Abschließen eines Rennens

Bevor Sie die Bestenliste oder das Wärmebild anzeigen, empfiehlt es sich, einige Beispieldaten zu erstellen, indem Sie das Rennen mindestens einmal abschließen.

1. Klicken Sie auf **Race!** (Rennen!), wenn das Spiel im Unity-Editor ausgeführt wird. Schaltfläche, um ein neues Rennen zu starten

2. Verwenden Sie **WASD** oder die **Pfeiltasten**, um das Auto zu fahren und eine Runde im Uhrzeigersinn auf der Bahn abzuschließen. Stellen Sie für dieses Beispiel sicher, dass Sie auf dem Weg gegen einige Wände prallen. Die Debugausgabe in der Unity-Konsole sollte angeben, wenn eine Kollision aufgezeichnet wurde.

  >[!NOTE]
  > Wenn Ihr Auto umkippt und Sie nicht mehr fortfahren können, klicken Sie auf **Restart** (Neustart). Die Daten werden nur an Azure gesendet, wenn Sie eine Runde abschließen.

  ![Starten eines Rennens](media/vstu_azure-test-sample-game-image2.png)

3. Nachdem Sie die karierte Ziellinie überquert haben, sollte das Spiel die Meldung **Finished** (Ende) anzeigen. An diesem Punkt werden Kollisionsdaten in Azure hochgeladen.

4. Wenn Sie eine der zehn schnellsten Rundenzeiten erreicht haben, werden Sie dazu aufgefordert, einen Namen für die Bestenliste einzugeben. Geben Sie Ihren Namen ein, und klicken Sie auf **Senden**.

  ![Starten eines Rennens](media/vstu_azure-test-sample-game-image3.png)

## <a name="view-the-heatmap"></a>Anzeigen des Wärmebilds

1. Klicken Sie auf die Schaltfläche **View Crash Heatmap** (Anzeigen des Kollisionswärmebilds) im Rennen oder auf **Crash Heatmap** (Kollisionswärmebild) im Hauptmenü.

2. Die Wärmebildszene lädt Daten aus der CrashInfo-Tabelle in Azure und zeigt eine transparente rote Kugel an den Orten an, an denen die Spieler mit den Wänden der Rennbahn kollidiert sind. Wenn mehrere Kollisionen in einem überlappenden Bereich auftreten, sollten die Kugeln heller angezeigt werden.

  ![Wärmebild](media/vstu_azure-test-sample-game-image4.png)

## <a name="view-the-leaderboard"></a>Anzeigen der Bestenliste

1. Klicken Sie auf die Schaltfläche **Leaderboard** (Bestenliste) im Rennen oder im Hauptmenü.

2. Die Bestenliste lädt Bestzeitdaten aus der HighScoreInfo-Tabelle in Azure und zeigt einen Spielernamen und die Rundenzeit für jeden Eintrag in der Bestenliste an.

  ![Bestenliste](media/vstu_azure-test-sample-game-image5.png)

## <a name="next-step"></a>Nächster Schritt

* [Erläuterung von RaceScene](visual-studio-tools-for-unity-azure-racescene.md)

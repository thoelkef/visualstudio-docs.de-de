---
title: "Visual Studio-Tools für Unity: RaceScene – Exemplarische Vorgehensweise (Azure) | Microsoft-Dokumentation"
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1F9304E8-0F1B-4325-8BED-FE3EB0ADCE8D
author: dantogno
ms.author: v-davian
manager: crdun
ms.openlocfilehash: 304fb69ab6e5da058cd3d2a4d6de202fa042b8f9
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2017
---
# <a name="racescene-explanation"></a>Erläuterung von RaceScene

RaceScene verwendet Unity [Standard Assets](https://www.assetstore.unity3d.com/en/#!/content/32351), um das grundlegende Spiel und die Level des Rennspiels zu erstellen. In diesem Abschnitt werden die relevanten GameObjects und ihre Skripts in der Reihenfolge erläutert, in der sie wie im folgenden Screenshot dargestellt in der RaceScene-Hierarchie aufgelistet sind.

![RaceScene](media/vstu_azure-racescene-explanation-image1.png)

## <a name="multipurposecamerarig"></a>MultipurposeCameraRig

**MultipurposeCameraRig** stammt aus dem **Cameras**-Paket von Standard Assets. Die Inspector-Eigenschaften wurden dafür optimiert, dem Car-Objekt mit einer entsprechenden Geschwindigkeit zu folgen.

## <a name="levelgeometry"></a>LevelGeometry

Das LevelGeometry-Prefab ist ein leeres GameObject, das für die Organisation verwendet wird. Die untergeordneten GameObject-Objekte erstellen den spielbaren Bereich. Die Böden, Wände, Rampen und Hindernisse werden alle aus den Prefabs im **Prototyping**-Paket von Standard Assets erstellt.

**Ein wichtiger Hinweis** besteht darin, dass auf ein Objekt das **Wall**-Tag angewendet sein muss, um es auf Kollisionen zu testen, die in Azure aufgezeichnet werden.

![RaceScene](media/vstu_azure-racescene-explanation-image2.png)

## <a name="car"></a>Car

Das **Car**-Prefab stammt aus dem **Vehicles**-Paket von Standard Assets. Die einzige Änderung besteht darin, dass die **RecordCrashInfo**-Skriptkomponente hinzugefügt wird.

### <a name="recordcrashinfo"></a>RecordCrashInfo

Das Skript überprüft Kollisionen in `OnCollisionEnter` und zeichnet diese in einer Liste auf. `crashRecordingCooldown` und `crashRecordingMinVelocity` schränken ein, was im Spiel als Kollision zählt, um ein relevantes Dataset zu erhalten.

Wenn das `RaceFinished`-Ereignis ausgelöst wird, sendet `UploadNewCrashDataAsync` jeden Kollision in der Liste an die CrashInfo-Easy-Tabelle in Azure.

```Csharp
using System.Collections;
using System.Collections.Generic;
using System.Threading.Tasks;
using UnityEngine;

public class RecordCrashInfo : MonoBehaviour
{
    [Tooltip("Time in seconds after a crash before a new crash can be recorded.")]
    [SerializeField]
    private float crashRecordingCooldown = 1;

    [Tooltip("How fast car must be traveling before crash can be recorded.")]
    [SerializeField]
    private float crashRecordingMinVelocity = 8;

    [SerializeField]
    private Rigidbody carRigidbody;

    [SerializeField]
    private GameObject crashMarkerPrefab;

    [Tooltip("If turned on, crash markers spawn when the player crashes.")]
    [SerializeField]
    private bool spawnDebugMarkers = false;

    private bool isOnCooldown = false;
    private bool meetsMinVelocity = false;
    private bool isRaceFinished = false;

    private List<CrashInfo> newCrashes = new List<CrashInfo>();

    private void LateUpdate()
    {
        // We have to update this in LateUpdate as opposed to checking in OnCollisionEnter.
        // The car's velocity has already decreased from crashing by the time
        // OnCollisionEnter gets called.

        meetsMinVelocity = carRigidbody.velocity.magnitude >= crashRecordingMinVelocity;
    }

    private void OnCollisionEnter(Collision collision)
    {
        if (!isRaceFinished && collision.gameObject.tag == "Wall" && !isOnCooldown && meetsMinVelocity)
        {
            Debug.Log("Collided with wall!");

            newCrashes.Add(new CrashInfo
            {
                X = collision.transform.position.x,
                Y = collision.transform.position.y,
                Z = collision.transform.position.z
            });

            if (spawnDebugMarkers && Debug.isDebugBuild)
                Instantiate(crashMarkerPrefab, collision.transform.position, Quaternion.identity);

            isOnCooldown = true;
            StartCoroutine(Cooldown());
        }  
    }

    private IEnumerator Cooldown()
    {
        yield return new WaitForSeconds(crashRecordingCooldown);

        isOnCooldown = false;
    }

    private void OnRaceFinished()
    {
        Task.Run(UploadNewCrashDataAsync);
    }

    private async Task UploadNewCrashDataAsync()
    {
        var crashTable = AzureMobileServiceClient.Client.GetTable<CrashInfo>();

        try
        {
            Debug.Log("Uploading crash data to Azure...");

            foreach (var item in newCrashes)
            {
                await crashTable.InsertAsync(item);
            }
            Debug.Log("Finished uploading crash data.");
        }
        catch (System.Exception e)
        {
            Debug.Log("Error uploading crash data: " + e.Message);
        }

    }

    private void OnEnable()
    {
        Checkpoint.RaceFinished += OnRaceFinished;
    }

    private void OnDisable()
    {
        Checkpoint.RaceFinished -= OnRaceFinished;
    }

}
```

## <a name="checkpoints"></a>Kontrollpunkte

Die Ebene enthält vier GameObject-Objekte durch die **Checkpoint**-Skriptkomponente. Die Prüfpunkte stellen sicher, dass der Spieler das Rennen nicht beenden kann, indem er die Bahn auf dem falschen Weg befährt. Diese erkennen ebenfalls, wenn der Spieler das Rennen beendet. Hierbei wird das `RaceFinished`-Ereignis aufgerufen.

## <a name="invisible-collision"></a>Unsichtbare Kollision

Primitive Standardcubes werden mit deaktivierten MeshRenderer-Komponenten als unsichtbare Kollisionen verwendet, um den Spieler innerhalb der Grenzen zu halten. Zusätzlich wird das physikalische **Bouncy**-Material angewendet, um sicherzustellen, dass fliegende Autos an den unsichtbaren Wänden wie vorgesehen abprallen und um zu verhindern, dass der Spieler eine unsichtbare Wand trifft, an ihr hinunter rutscht und auf einer sichtbaren Wand landet.

## <a name="recordhighscore"></a>RecordHighScore

Dieses Skript überprüft, ob der Spieler eine neue Bestzeit erreicht hat. Falls ja, wird `enterNamePopup` angezeigt, wodurch der Spieler seinen Namen eingeben und auf **Senden** klicken kann.

Sobald ein Spielername abgesendet wird, wird `UploadNewHighScoreAsync` aufgerufen und die neue Bestzeit wird an die HighScoreInfo-Easy-Tabelle in Azure gesendet.

```csharp
using System.Collections;
using System.Collections.Generic;
using Microsoft.WindowsAzure.MobileServices;
using UnityEngine;
using System.Threading.Tasks;
using System;
using System.Linq;
using UnityEngine.UI;

public class RecordHighScore : MonoBehaviour
{
    [SerializeField]
    private InputField nameInputField;

    [SerializeField]
    private CanvasGroup enterNamePopup;

    private List<HighScoreInfo> highScores;
    private string playerName = string.Empty;

    private async void Start()
    {
        ShowEnterNamePopup(false);
        highScores = await Leaderboard.GetTopHighScoresAsync();
    }

    private void ShowEnterNamePopup(bool shouldShow)
    {
        enterNamePopup.alpha = shouldShow ? 1 : 0;
        enterNamePopup.interactable = shouldShow;
    }

    public void SubmitButtonClicked()
    {
        playerName = nameInputField.text;
    }

    private async void OnAfterMostRecentScoreSet(float newScore)
    {
        bool isNewHighScore = CheckForNewHighScore(newScore);

        if (isNewHighScore)
        {
            Debug.Log("New High Score!");
            await GetPlayerNameAsync();
            await UploadNewHighScoreAsync(newScore);
        }
        else
        {
            Debug.Log("No new high score.");
        }
    }

    private async Task GetPlayerNameAsync()
    {
        // Wait a bit before showing the popup.
        // This just helps the player experience feel
        // less jarring.
        await Task.Delay(2000);
        ShowEnterNamePopup(true);

        // Wait until the player enters a name and clicks submit.
        // OnSubmitButtonClicked will set the playerName.
        while (playerName == string.Empty)
        {
            await Task.Delay(100);
        }

        ShowEnterNamePopup(false);
    }

    private bool CheckForNewHighScore(float newScore)
    {
        Debug.Log("Checking for a new high score...");

        bool isHighScoreListFull = highScores.Count >= Leaderboard.SizeOfHighScoreList;
        var lowerScores = highScores.Where(x => x.Time > newScore);

        return lowerScores.Count() > 0 || !isHighScoreListFull;
    }

    private async Task UploadNewHighScoreAsync(float newScore)
    {
        var newHighScoreInfo = new HighScoreInfo { Name = playerName, Time = newScore };

        try
        {
            Debug.Log("Uploading high score data to Azure...");

            await Leaderboard.HighScoreTable.InsertAsync(newHighScoreInfo);

            Debug.Log("Finished uploading high score data.");
        }
        catch (System.Exception e)
        {
            Debug.Log("Error uploading high score data: " + e.Message);
        }
    }

    private void OnEnable()
    {
        LapTimer.AfterMostRecentScoreSet += OnAfterMostRecentScoreSet;
    }

    private void OnDisable()
    {
        LapTimer.AfterMostRecentScoreSet -= OnAfterMostRecentScoreSet;
    }

}
```

## <a name="next-step"></a>Nächster Schritt

* [Erläuterung von HeatmapScene](visual-studio-tools-for-unity-azure-heatmapscene.md)

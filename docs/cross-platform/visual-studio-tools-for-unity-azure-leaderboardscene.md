---
title: "Visual Studio-Tools für Unity: LeaderboardScene – Exemplarische Vorgehensweise (Azure) | Microsoft-Dokumentation"
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2127DEBA-9470-490B-BDDF-6F77A5ACC329
author: dantogno
ms.author: v-davian
manager: crdun
ms.workload:
- azure
- unity
ms.openlocfilehash: b9d60ffe9dc5f58243328b7aaba3d3aa16cd4beb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="leaderboardscene-explanation"></a>Erläuterung zu LeaderboardScene

LeaderboardScene besteht nur aus Benutzeroberflächen. Klicken Sie in der Szenenhierarchie auf den **Pfeil „Erweiterung“** neben dem Canvas-GameObject, und halten Sie dabei **ALT** gedrückt, um dieses Objekt und die untergeordneten GameObjects zu erweitern. Unter „Canvas“ und „Panel“ befindet sich das Leaderboard-GameObject, dem das Leaderboard-Skript angefügt ist.

![Leaderboard-GameObject](media/vstu_azure-leaderboard-explanation-image1.png)

## <a name="leaderboard-script"></a>Leaderboard-Skript

Die `Leaderboard`-Klasse verwendet eine `async Start`-Funktion, die sogar aufgerufen wird, wenn das Skript deaktiviert ist. Dies ist auch bei einer typischen `Start`-Funktion der Fall.

`DownloadHighScoresAsync` verwendet die Funktionen `OrderBy` und `Take` von <a href="https://msdn.microsoft.com/en-us/library/azure/jj554257(v=azure.10).aspx">`IMobileServiceTable`</a>, um die hohen Werte in der Azure Easy-Tabelle zu sortieren und anhand der `SizeOfHighScoreList`-Konstante die Einträge oben in der Tabelle zu entnehmen, die in der `highScores`-Liste gespeichert werden.

Anschließend wird eine Instanz der Zeile mit den höchsten Werten der vorgefertigten Benutzeroberfläche für jeden Eintrag in der Liste instanziiert.

``` csharp
using Microsoft.WindowsAzure.MobileServices;
using System.Collections.Generic;
using System.Threading.Tasks;
using UnityEngine;
using System;
using UnityEngine.UI;

public class Leaderboard : MonoBehaviour
{
    [SerializeField]
    private GameObject rowPrefab;

    [SerializeField]
    private Text loadingText;

    public const int SizeOfHighScoreList = 10;
    private static int numberOfAttemptsToLoadData = 3;
    private static IMobileServiceTable<HighScoreInfo> highScoreTable_UseProperty;

    public static IMobileServiceTable<HighScoreInfo> HighScoreTable
    {
        get
        {
            if (highScoreTable_UseProperty == null)
            {
                highScoreTable_UseProperty = AzureMobileServiceClient.Client.GetTable<HighScoreInfo>();
            }

            return highScoreTable_UseProperty;
        }
    }

    public static async Task<List<HighScoreInfo>> GetTopHighScoresAsync()
    {
            return await DownloadHighScoresAsync(true);
    }

    private static async Task<List<HighScoreInfo>> DownloadHighScoresAsync(bool onlyTopEntries)
    {
        List<HighScoreInfo> highScoreList;

        Debug.Log("Downloading high score data from Azure...");

        for (int i = 0; i < numberOfAttemptsToLoadData; i++)
        {
            try
            {
                Debug.Log("Connecting... attempt " + (i + 1));

                if (onlyTopEntries)
                {
                    highScoreList = await HighScoreTable
                        .OrderBy(item => item.Time)
                        .Take(SizeOfHighScoreList)
                        .ToListAsync();
                }
                else
                {
                    highScoreList = await HighScoreTable.ToListAsync();
                }

                Debug.Log("Done downloading high score data.");
                return highScoreList;
            }
            catch (Exception e)
            {
                Debug.Log("Error connecting: " + e.Message);
            }

            if (i == numberOfAttemptsToLoadData - 1)
                Debug.Log("Connection failed. Check logs, try again later.");
            else
                await Task.Delay(500);
        }

        // If we can't successfully download a list from the server,
        // just make a new one to fail more gracefully.
        return highScoreList = new List<HighScoreInfo>();
    }

    private async void Start()
    {
        var highScores = await GetTopHighScoresAsync();

        if (highScores.Count == 0)
        {
            ShowEmptyLeaderboardMessage();
        }
        else
        {
            loadingText.gameObject.SetActive(false);

            foreach (var item in highScores)
            {
                var row = Instantiate(rowPrefab, this.transform).GetComponent<LeaderboardRow>();
                row.HighScoreInfo = item;
            }
        }
    }

    private void ShowEmptyLeaderboardMessage()
    {
        loadingText.text = "The leaderboard is empty!";
    }

    public static async Task DeleteAllEntriesAsync()
    {
       Debug.Log("Deleting leaderboard data...");

        var fullHighScoreList = await DownloadHighScoresAsync(false);

        foreach (var item in fullHighScoreList)
        {
            try
            {
                await HighScoreTable.DeleteAsync(item);
            }
            catch (Exception e)
            {
                Debug.Log("Error deleting leaderboard data: " + e.Message);
            }
        }
    }
}
```
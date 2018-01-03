---
title: "Visual Studio-Tools für Unity: HeatmapScene – Exemplarische Vorgehensweise (Azure) | Microsoft-Dokumentation"
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: E11DA08B-7341-4743-A817-0CAD59844305
author: dantogno
ms.author: v-davian
manager: crdun
ms.workload:
- azure
- unity
ms.openlocfilehash: 472b6d5adae5e23007b9c1aa4d9c75118a94e1cc
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="heatmapscene-explanation"></a>Erläuterung zu HeatmapScene

HeatmapScene enthält eine Instanz der vorgefertigten **LevelGeometry**. So werden die Koordinaten von Abstürzen, die von Azure geladen werden, der zweidimensionalen Grafik korrekt zugeordnet.

## <a name="heatmap-script"></a>Heatmap-Skript

### <a name="initializecrashlistasync"></a>InitializeCrashListAsync
`InitializeCrashListAsync` stellt eine Verbindung zu der CashInfo-Easy-Tabelle in Azure her und verwendet <a href="https://msdn.microsoft.com/en-us/library/azure/jj554274(v=azure.10).aspx">`ToListAsync`</a>, um sämtliche Tabelleneinträge in eine Liste einzufügen.

```
private async Task InitializeCrashListAsync()
 {
     Debug.Log("Downloading crash data from Azure...");

     for (int i = 0; i < numberOfAttempts; i++)
     {
         try
         {
             Debug.Log("Connecting... attempt " + (i +1));
             crashesFromServer = await crashesTable.ToListAsync();
             Debug.Log("Done downloading.");
             return;
         }
         catch (System.Exception e)
         {
             Debug.Log("Error connecting: " + e.Message);
         }

         if (i == numberOfAttempts - 1)
             Debug.Log("Connection failed. Check logs, try again later.");
         else
             await Task.Delay(500);
     }
 }
```

### <a name="spawnmarkersfromlist"></a>SpawnMarkersFromList
`SpawnMarkersFromList` durchläuft die Liste mit Abstürzen, die von Azure übermittelt wurden, und instanziiert eine vorgefertigte Absturzmarkierung für jeden Eintrag.

```csharp
private void SpawnMarkersFromList()
{
    foreach (var item in crashesFromServer)
    {
        GameObject marker = GameObject.Instantiate(markerPrefab);
        marker.transform.position = new Vector3 { x = item.X, y = item.Y, z = item.Z };
    }
}
```

### <a name="deletecrashdataasync"></a>DeleteCrashDataAsync

`DeleteCrashDataAsync` wird aufgerufen, wenn der Benutzer auf die Schaltfläche **Daten löschen** drückt. Diese Koordinate durchläuft die lokale Liste mit Abstürzen und ruft <a href="https://msdn.microsoft.com/en-us/library/azure/jj554258(v=azure.10).aspx">`DeleteAsync`</a> für jeden Eintrag auf. Dadurch wird für sämtliche **gelöschten** Spalten in der Easy-Tabelle **TRUE** festgelegt. `ToListAsync` ignoriert diese gelöschten Einträge.

```csharp
public async void DeleteCrashDataAsync()
{
    Debug.Log("Deleting crash data...");
    foreach (var item in crashesFromServer)
    {
        try
        {
            await crashesTable.DeleteAsync(item);
        }
        catch (System.Exception e)
        {
            Debug.Log("Error deleting crash data: " + e.Message);
        }
        Debug.Log("Done deleting crash data.");
    }
    SceneManager.LoadScene(SceneManager.GetActiveScene().name);
}
```

## <a name="next-step"></a>Nächster Schritt

* [Erläuterung zu LeaderboardScene](visual-studio-tools-for-unity-azure-leaderboardscene.md)
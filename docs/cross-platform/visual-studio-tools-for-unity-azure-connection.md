---
title: "Visual Studio-Tools für Unity: Verbindung – Exemplarische Vorgehensweise (Azure) Microsoft-Dokumentation"
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 516A8FB2-8DFF-4BAB-8116-FDCD1C228DB3
author: dantogno
ms.author: v-davian
manager: crdun
ms.openlocfilehash: f21e320fe9e27f6873b9caed3048a93bfa94a9c4
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2017
---
# <a name="test-the-client-connection"></a>Testen der Clientverbindung

Nachdem das Azure MobileServiceClient-Singleton erstellt wurde, kann die Clientverbindung getestet werden.

## <a name="create-the-testclientconnection-script"></a>Erstellen des TestClientConnection-Skripts

1. Erstellen Sie im Ordner **Skripts** in Unity ein neues C#-Skript mit dem Namen **TestClientConnection**.

2. Öffnen Sie das Skript in Visual Studio, löschen Sie ggf. Vorlagencode, und fügen Sie Folgendes hinzu:

  ```csharp
  using System.Collections.Generic;
  using UnityEngine;
  using System.Threading.Tasks;
  using System;
  using System.Linq;
  using Microsoft.WindowsAzure.MobileServices;

  public class TestClientConnection : MonoBehaviour
  {
      void Start()
      {
          Task.Run(TestTableConnection);
      }

      private async Task TestTableConnection()
      {
          var table = AzureMobileServiceClient.Client.GetTable<CrashInfo>();

          Debug.Log("Testing ToListAsync...");
          await TestToListAsync(table);

          Debug.Log("Testing InsertAsync...");
          await TestInsertAsync(table);

          Debug.Log("Testing DeleteAsync...");
          await TestDeleteAsync(table);

          Debug.Log("All testing complete.");
      }

      private async Task TestInsertAsync(IMobileServiceTable<CrashInfo> table)
      {
          try
          {
              var allEntries = await TestToListAsync(table);
              var initialCount = allEntries.Count();

              await table.InsertAsync(new CrashInfo { X = 1, Y = 2, Z = 3 });

              allEntries = await TestToListAsync(table);
              var newCount = allEntries.Count();

              Debug.Assert(newCount == initialCount + 1, "InsertAsync failed!");
          }
          catch (Exception)
          {
              throw;
          }
      }

      private async Task<List<CrashInfo>> TestToListAsync(IMobileServiceTable<CrashInfo> table)
      {
          try
          {
              var allEntries = await table.ToListAsync();
              Debug.Assert(allEntries != null, "ToListAsync failed!");
              return allEntries;
          }
          catch (Exception)
          {

              throw;
          }
      }

      private async Task TestDeleteAsync(IMobileServiceTable<CrashInfo> table)
      {
          var allEntries = await TestToListAsync(table);

          foreach (var item in allEntries)
          {
              try
              {
                  await table.DeleteAsync(item);
              }
              catch (Exception)
              {
                  throw;
              }
          }

          allEntries = await TestToListAsync(table);

          Debug.Assert(allEntries.Count() == 0, "DeleteAsync failed!");
      }
  }
  ```

3. Klicken Sie im **GameObject**-Menü in Unity auf **GameObject > Leeres Objekt erstellen**, um ein leeres GameObject in der Unity-Szene zu erstellen. Nennen Sie es in **TestClientConnection** um.

4. **Ziehen Sie das TestClientConnection-Skript** aus dem **Projektfenster** in Unity in das GameObject „TestClientConnection“ im **Hierarchiefenster**.

5. Klicken Sie im Unity-Menü auf **Datei > Szene speichern unter...**. Geben Sie der Szene den Namen **Clientverbindungstest**, und klicken Sie anschließend auf **Speichern**.

5. Klicken Sie in Unity auf **Wiedergabe**, und beobachten Sie das Konsolenfenster. Achten Sie darauf, dass keine Assertion fehlgeschlagen ist.

6. Öffnen Sie die CashInfo-Easy-Tabelle im Azure-Portal. Jetzt sollten Sie einen Eintrag mit den Koordinaten **X, Y, Z** von **(1, 2, 3)** sowie den Wert **TRUE** in der Spalte **deleted** (gelöscht) sehen. Mit jeder Durchführung des Tests wird ein Eintrag mit dem gleichen Wert, aber einer eindeutigen ID der Tabelle hinzugefügt.

  ![Eintrag in einfacher Tabelle](media/vstu_azure-test-client-connection-image1.png)

## <a name="next-step"></a>Nächster Schritt
* [Importieren der Beispielspielobjekte](visual-studio-tools-for-unity-azure-game-assets.md)

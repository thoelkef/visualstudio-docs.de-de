---
title: "Visual Studio-Tools für Unity: Datenmodell – Exemplarische Vorgehensweise für Azure | Microsoft-Dokumentation"
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6FCCA8D1-0D06-4B2A-A55F-FC3D1FEA0F56
author: dantogno
ms.author: v-davian
manager: crdun
ms.workload:
- azure
- unity
ms.openlocfilehash: 57a6a6aaff1c41a8720f842e20142e3cb1a2e538
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="create-data-model-classes"></a>Erstellen von Datenmodellklassen

Das Unity-Projekt muss Datenmodellklassen enthalten, die mit den Tabellen übereinstimmen, die im Back-End der mobilen Azure App erstellt wurden.

## <a name="create-the-crashinfo-class"></a>Erstellen der CrashInfo-Klasse

1. Fügen Sie in Unity dem Stammverzeichnis **Assets** (Objekte) einen neuen Ordner mit dem Namen **Skripts** hinzu. Erstellen Sie in dem neuen Skriptsordner einen weiteren Ordner mit dem Namen **Datenmodelle**. Dieser dient nur zur Organisation.

2. Erstellen Sie in dem neuen Datenmodellordner ein neues C#-Skript mit dem Namen **CrashInfo**.

3. Öffnen Sie das neue `CrashInfo`-Skript, löschen Sie jeglichen Vorlagencode, einschließlich der Klassendeklaration und Using-Anweisungen, und fügen Sie Folgendes hinzu:

  ```csharp
  public class CrashInfo
  {
      public string Id { get; set; }
      public float X { get; set; }
      public float Y { get; set; }
      public float Z { get; set; }
  }
  ```

  > [!WARNING]
  > Damit die exemplarische Vorgehensweise korrekt ausgeführt wird, muss der Name des Datenmodells mit dem Namen der Easy-Tabelle im Back-End der mobilen Azure App übereinstimmen.

## <a name="create-the-highscoreinfo-class"></a>Erstellen der HighScoreInfo-Klasse

1. Erstellen Sie im Datenmodellordner ein neues C#-Skript mit dem Namen **HighScoreInfo**.

2. Öffnen Sie das neue `HighScoreInfo`-Skript, löschen Sie jeglichen Vorlagencode, einschließlich der Klassendeklaration und Using-Anweisungen, und fügen Sie Folgendes hinzu:

  ```csharp
  public class HighScoreInfo
  {
      public string Name { get; set; }
      public float Time { get; set; }
      public string Id { get; set; }
  }
  ```

  ## <a name="next-step"></a>Nächster Schritt

  * [Implement the Azure MobileServiceClient (Implementieren des Azure-MobileServiceClient)](visual-studio-tools-for-unity-azure-mobile-client.md)

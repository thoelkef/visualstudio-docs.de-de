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
ms.openlocfilehash: e3b6064a3947f57ffcbe6422162c6c72fca0ab21
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2017
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

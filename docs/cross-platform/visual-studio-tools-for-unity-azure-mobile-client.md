---
title: "Visual Studio-Tools für Unity – Exemplarische Vorgehensweise (Azure Mobile Client) | Microsoft-Dokumentation"
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5A8762A1-D843-4FD8-A89B-E5E489ECA03D
author: dantogno
ms.author: v-davian
manager: crdun
ms.workload:
- azure
- unity
ms.openlocfilehash: 451b4f1f2580a55077bf3fc6a9ad3f16a2afaf0f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="implement-the-azure-mobileserviceclient"></a>Implementieren des Azure-MobileServiceClient

<a href="https://msdn.microsoft.com/en-us/library/azure/microsoft.windowsazure.mobileservices.mobileserviceclient(v=azure.10).aspx">MobileServiceClient</a> ist Hauptbestandteil des Azure Mobile Client SDK, mit dem Sie auf das Back-End Ihrer mobilen App zugreifen können.

## <a name="locate-the-url-of-the-mobile-app-backend"></a>Die URL des Back-Ends Ihrer mobilen App

Der `MobileServiceClient`-Konstruktor nimmt die URL der mobilen App als Parameter an. Finden Sie also die URL, bevor Sie fortfahren.

1. Klicken Sie im Azure-Portal auf die Schaltfläche **App Services**.

    ![Auf „App Services“ klicken.](media/vstu_azure-implement-azure-mobileserviceclient-image1.png)

2. Klicken Sie auf den Eintrag für Ihre mobile App.

    ![Auf die mobile App klicken.](media/vstu_azure-implement-azure-mobileserviceclient-image2.png)

3. Kopieren Sie die URL des Back-Ends Ihrer mobilen App.

    ![URL kopieren.](media/vstu_azure-implement-azure-mobileserviceclient-image3.png)

## <a name="create-the-mobileserviceclient-singleton"></a>Erstellen des MobileServiceClient-Singletons

Es sollte nur eine Instanz von `MobileServiceClient` geben, weshalb in der exemplarischen Vorgehensweise verschiedene Singletonmuster verwendet werden.

1. Erstellen Sie im Verzeichnis **Assets/Scripts** (Ressourcen/Skripts) Ihres Unity-Projekts ein neues C#-Skript mit dem Namen **AzureMobileServiceClient**.

2. Öffnen Sie das `AzureMobileServiceClient`-Skript, und löschen Sie ggf. vorhandenen Vorlagencode, einschließlich using-Anweisungen und Klassendeklarationen.

3. Fügen Sie den folgenden Code hinzu:

  ```csharp
  using Microsoft.WindowsAzure.MobileServices;

  public static class AzureMobileServiceClient
  {
      private const bool ignoreTls = true;
      private const string backendUrl = "MOBILE_APP_URL";
      private static MobileServiceClient client;

      public static MobileServiceClient Client
      {
          get
          {
              if (client == null)
              {
                  client = new MobileServiceClient(backendUrl);
              }

              return client;
          }
      }
  }
  ```

  > [!NOTE]
  > Wenn IntelliSense den Microsoft.WindowsAzure-Namespace nicht erkennt, stellen Sie sicher, dass Sie die in [Vorbereiten der Entwicklungsumgebung]() beschriebenen Schritte alle durchgeführt haben.

4. Ersetzen Sie im vorausgehenden Code `MOBILE_APP_URL` durch die URL des Back-Ends Ihrer mobilen App.

## <a name="next-step"></a>Nächster Schritt

* [Aktualisieren des Unity Mono-Sicherheitsspeichers](visual-studio-tools-for-unity-azure-security.md)

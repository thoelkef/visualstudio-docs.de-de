---
title: Verwenden von Emulator Express zum Ausführen und Debuggen von Azure Cloud Services auf einem lokalen Computer | Microsoft-Dokumentation
description: Verwenden von Emulator Express zum Ausführen und Debuggen eines Clouddiensts auf einem lokalen Computer
author: mikejo5000
manager: douge
ms.assetid: 73108f98-a552-4817-b7a1-551367b71906
ms.topic: conceptual
ms.workload: azure-vs
ms.date: 03/06/2017
ms.author: mikejo
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.openlocfilehash: 28dd59e3d691df0199afffe93d68d60668c6afe4
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/05/2018
ms.locfileid: "51001706"
---
# <a name="using-emulator-express-to-run-and-debug-an-azure-cloud-service-on-a-local-machine"></a>Verwenden von Emulator Express zum Ausführen und Debuggen eines Azure-Clouddiensts auf einem lokalen Computer
Mithilfe von Emulator Express können Sie testen und Debuggen eines Clouddiensts, ohne Visual Studio als Administrator ausführen. Sie können die projekteinstellungen für die Verwendung von Emulator Express oder des vollständigen Emulators je nach den Anforderungen des Cloud-Diensts festlegen. Weitere Informationen zum vollständigen Emulator finden Sie unter [Ausführen einer Azure-Anwendung im Serveremulator](/azure/storage/common/storage-use-emulator).

## <a name="using-emulator-express-in-visual-studio"></a>Verwenden von Emulator Express in Visual Studio
Wenn Sie ein Azure-Projekt in Azure SDK 2.3 oder höher erstellen, wird der Emulator Express automatisch verwendet. Verwenden Sie für vorhandene Projekte, die mit einer früheren Version des Azure SDK erstellt wurden die folgenden Schritte aus, um Emulator Express auszuwählen:

1. Erstellen Sie oder öffnen Sie ein Azure-Cloud-Service-Projekt in Visual Studio.

1. In **Projektmappen-Explorer**, mit der rechten Maustaste in des Projekts und wählen Sie im Kontextmenü des **Eigenschaften**.

1. Wählen Sie in den Eigenschaftenseiten die **Web** Registerkarte.

    ![Eigenschaften für ein Azure-Cloud-Service-Projekt](./media/vs-azure-tools-emulator-express-debug-run/web-properties.png)

1. Klicken Sie unter **lokaler Bereitstellungsserver**Option **IIS Express verwenden**.

1. Klicken Sie unter **Emulator**Option **mit Emulator Express**.
   
1. Um Emulator Express zu starten, führen Sie den folgenden Befehl an einer Eingabeaufforderung aus: 

    ```
    csrun.exe /useemulatorexpress
    ```

## <a name="emulator-express-limitations"></a>Emulator Express-Einschränkungen
Die folgenden Probleme sind die Einschränkungen von Emulator Express bekannt: 

- Emulator Express ist nicht kompatibel mit IIS-Webserver.
- Ihre Cloud-Dienst kann mehrere Rollen enthalten, aber jede Rolle ist eine Instanz beschränkt.
- Sie können nicht auf Portnummern unterhalb von 1000 zugreifen. Wenn Sie einen Authentifizierungsanbieter, der üblicherweise einen Port unter 1000 verwendet verwenden, müssen Sie zum Ändern dieses Werts in eine Portnummer, die über 1000.
- Alle Azure-Serveremulator gelten Einschränkungen gelten auch für Emulator Express. Beispielsweise kann nicht mehr als 50 Rolleninstanzen pro Bereitstellung haben. Weitere Informationen zu Azure-Serveremulator, finden Sie unter [Ausführen einer Azure-Anwendung im Serveremulator](http://go.microsoft.com/fwlink/p/?LinkId=623050).

## <a name="next-steps"></a>Nächste Schritte
[Debuggen von Azure Cloud services](https://msdn.microsoft.com/library/azure/ee405479.aspx)

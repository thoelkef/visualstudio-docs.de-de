---
title: Bereitstellen mit Web Deploy
description: Bereitstellen einer app mit Web Deploy in Visual Studio
services: ''
author: mikejo5000
ms.service: ''
ms.topic: include
ms.date: 05/23/2018
ms.author: mikejo
ms.custom: include file
ms.openlocfilehash: 4ef232e64f308699c73c60cbe5b155f1d4ebb725
ms.sourcegitcommit: 1c675dae7c348defb32d9f7ccf7079a1062a1c4b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/03/2018
ms.locfileid: "48244111"
---
Wenn Sie Web Deploy über den Webplattform-Installer installiert haben, können Sie die app direkt aus Visual Studio bereitstellen.

1. Starten Sie Visual Studio mit Administratorrechten, und öffnen Sie das Projekt erneut.

    Zum Bereitstellen Ihrer app mit Web Deploy sind Administratorrechte erforderlich.

1. Klicken Sie im **Projektmappen-Explorer**mit der rechten Maustaste auf den Projektknoten, und wählen Sie **Veröffentlichen**aus.

    Wenn Sie Veröffentlichungsprofile, zuvor konfiguriert haben die **veröffentlichen** angezeigt. Klicken Sie auf **neues Profil**.

1. Für **Veröffentlichungsziel auswählen**Option **IIS, FTP usw.** , und klicken Sie auf **veröffentlichen**.

    ![RemoteDBG_Publish_IISl](../../debugger/media/remotedbg_iis_profile.png "RemoteDBG_Publish_IIS")

1. Geben Sie die Konfigurationsparameter für die Korrektur für der IIS-Konfiguration ein.

    ![RemoteDBG_Publish_WebDeployl](../../debugger/media/remotedbg_iis_webdeploy_config.png "RemoteDBG_Publish_WebDeploy")

    Wenn ein Hostname nicht behoben wird, wenn Sie versuchen, überprüfen Sie in den nächsten Schritten, in der **Server** Text im Feld, und versuchen Sie die IP-Adresse. Umfassen `http://` als Präfix in der **Server** Feld.  Stellen Sie sicher, dass Sie Port 80 der **Server** Text, und stellen Sie sicher, dass Port 80 und Port 8172 in der Firewall geöffnet werden.

1. Wählen Sie **überprüfen**. Wenn die Einrichtung der Verbindung überprüft hat, können Sie versuchen, zu veröffentlichen.

1. Klicken Sie auf **veröffentlichen** zum Veröffentlichen der app.

    Die Registerkarte "Ausgabe" zeigt an, ob die Veröffentlichung erfolgreich war und Ihr Browser öffnet dann die app.

    Wenn Sie erwähnen, Web Deploy-Fehler erhalten, überprüfen Sie die Schritte für die Web Deploy-Installation, und stellen Sie sicher, dass die richtigen Ports geöffnet sind (Web Deploy erfordert auch Port 8172 zu öffnen, auf dem Server sein).

    Wenn die app erfolgreich bereitgestellt, aber nicht ordnungsgemäß ausgeführt werden kann, gibt es möglicherweise ein Problem mit der IIS-Konfiguration, die ASP.NET-Installation oder Konfiguration Ihrer Website vor. Öffnen Sie auf dem Windows-Server die Website aus IIS für genauere Fehlermeldungen, und überprüfen Sie dann die vorangegangenen Schritte erneut aus.

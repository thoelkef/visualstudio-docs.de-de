---
title: Mithilfe von Web Deploy bereitstellen
description: Bereitstellen einer app in Visual Studio mithilfe von Web Deploy
services: ''
author: mikejo5000
ms.service: ''
ms.topic: include
ms.date: 05/23/2018
ms.author: mikejo
ms.custom: include file
ms.openlocfilehash: 4ef232e64f308699c73c60cbe5b155f1d4ebb725
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2018
ms.locfileid: "34794197"
---
Wenn Sie Web Deploy, mit dem Webplattform-Installer installiert haben, können Sie die app direkt in Visual Studio bereitstellen.

1. Starten Sie Visual Studio mit Administratorrechten, und öffnen Sie das Projekt erneut.

    Zum Bereitstellen Ihrer app mithilfe von Web Deploy sind Administratorrechte erforderlich.

1. Klicken Sie im **Projektmappen-Explorer**mit der rechten Maustaste auf den Projektknoten, und wählen Sie **Veröffentlichen**aus.

    Wenn Sie Veröffentlichungsprofile zuvor konfiguriert haben die **veröffentlichen** Bereich wird angezeigt. Klicken Sie auf **neues Profil**.

1. Für **Veröffentlichungsziel auswählen**Option **IIS, FTP usw.** , und klicken Sie auf **veröffentlichen**.

    ![RemoteDBG_Publish_IISl](../../debugger/media/remotedbg_iis_profile.png "RemoteDBG_Publish_IIS")

1. Geben Sie die Korrektur Konfigurationsparameter für die IIS-Konfiguration.

    ![RemoteDBG_Publish_WebDeployl](../../debugger/media/remotedbg_iis_webdeploy_config.png "RemoteDBG_Publish_WebDeploy")

    Wenn Sie ein Hostnamen nicht behoben wird, wenn Sie versuchen, überprüfen Sie in den nächsten Schritten, in der **Server** Text im Feld, und versuchen Sie die IP-Adresse. Umfassen `http://` als Präfix in der **Server** Feld.  Stellen Sie sicher, dass die Verwendung von Port 80 in der **Server** Text ein, und stellen Sie sicher, dass Port 80 und Port 8172 in der Firewall geöffnet werden.

1. Wählen Sie **überprüfen**. Wenn dem Einrichten der Verbindung überprüft hat, können Sie versuchen, veröffentlichen.

1. Klicken Sie auf **veröffentlichen** zum Veröffentlichen der app.

    Die Registerkarte "Ausgabe" zeigt an, ob die Publishing ist erfolgreich, und Ihr Browser öffnet dann die app.

    Wenn Sie einen Web Deploy erwähnen Fehler erhalten, überprüfen Sie die Installationsschritte Web Deploy erneut, und stellen Sie sicher, dass die richtigen Ports geöffnet sind (Web Deploy erfordert außerdem Port 8172 auf dem Server geöffnet sein).

    Wenn die app erfolgreich bereitgestellt, aber nicht ordnungsgemäß ausgeführt werden kann, gibt es möglicherweise ein Problem mit der IIS-Konfiguration, die ASP.NET-Installation oder Konfiguration Ihrer Website. Öffnen Sie auf dem Windows-Server die Website aus IIS finden Sie spezifischere Fehlermeldungen, und überprüfen Sie dann erneut bereits beschriebenen Schritte.

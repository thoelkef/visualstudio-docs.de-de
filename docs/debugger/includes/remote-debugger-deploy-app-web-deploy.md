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
ms.openlocfilehash: 8c843ffa6abcb7517ebfe7cdfb0e742a5f244e07
ms.sourcegitcommit: d1824ab926ebbc4a8057163e0edeaf35cec57433
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/24/2018
ms.locfileid: "34478312"
---
Wenn Sie Web Deploy, mit dem Webplattform-Installer installiert haben, können Sie die app direkt in Visual Studio bereitstellen.

1. Starten Sie Visual Studio mit Administratorrechten, und öffnen Sie das Projekt erneut.

    Zum Bereitstellen Ihrer app mithilfe von Web Deploy sind Administratorrechte erforderlich.

1. Klicken Sie im **Projektmappen-Explorer**mit der rechten Maustaste auf den Projektknoten, und wählen Sie **Veröffentlichen**aus.

    Wenn Sie Veröffentlichungsprofile zuvor konfiguriert haben die **veröffentlichen** Bereich wird angezeigt. Klicken Sie auf **neues Profil**.

1. Für **Veröffentlichungsziel auswählen**Option **IIS, FTP usw.** , und klicken Sie auf **veröffentlichen**.

    ![RemoteDBG_Publish_IISl](../media/remotedbg_iis_profile.png "RemoteDBG_Publish_IIS")

1. Geben Sie die Korrektur Konfigurationsparameter für die IIS-Konfiguration.

    ![RemoteDBG_Publish_WebDeployl](../media/remotedbg_iis_webdeploy_config.png "RemoteDBG_Publish_WebDeploy")

    Wenn Sie ein Hostnamen nicht behoben wird, wenn Sie versuchen, überprüfen Sie in den nächsten Schritten, in der **Server** Text im Feld, und versuchen Sie die IP-Adresse. Umfassen `http://` als Präfix in der **Server** Feld.  Stellen Sie sicher, dass die Verwendung von Port 80 in der **Server** Text ein, und stellen Sie sicher, dass Port 80 in der Firewall geöffnet ist.

1. Klicken Sie auf **Weiter**, wählen Sie eine **Debuggen** Konfiguration, und wählen Sie **entfernen weiterer Dateien am Ziel** unter der **-Datei veröffentlichen** Optionen.

    > [!NOTE]
    > Bei Auswahl eine Releasekonfiguration wird Sie beim Veröffentlichen in der Datei "Web.config"-Debuggen deaktivieren.

1. Klicken Sie auf **Prev**, und wählen Sie dann **Validate**. Wenn dem Einrichten der Verbindung überprüft hat, können Sie versuchen, veröffentlichen.

1. Klicken Sie auf **veröffentlichen** zum Veröffentlichen der app.

    Die Registerkarte "Ausgabe" zeigt an, ob die Publishing ist erfolgreich, und Ihr Browser öffnet dann die app.

    Wenn Sie einen Web Deploy erwähnen Fehler erhalten, überprüfen Sie die Installationsschritte Web Deploy erneut, und stellen Sie sicher, dass die richtigen Ports geöffnet sind (Web Deploy erfordert außerdem Port 8172 auf dem Server geöffnet sein).

    Wenn die app erfolgreich bereitgestellt, aber nicht ordnungsgemäß ausgeführt werden kann, gibt es möglicherweise ein Problem mit der IIS-Konfiguration, die ASP.NET-Installation oder Konfiguration Ihrer Website. Öffnen Sie auf dem Windows-Server die Website aus IIS finden Sie spezifischere Fehlermeldungen, und überprüfen Sie dann erneut bereits beschriebenen Schritte.

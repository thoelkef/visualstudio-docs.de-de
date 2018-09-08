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
ms.openlocfilehash: 8c843ffa6abcb7517ebfe7cdfb0e742a5f244e07
ms.sourcegitcommit: aea5cdb76fbc7eb31d1e5cc3c8d6adb0c743220f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/07/2018
ms.locfileid: "34478312"
---
Wenn Sie Web Deploy über den Webplattform-Installer installiert haben, können Sie die app direkt aus Visual Studio bereitstellen.

1. Starten Sie Visual Studio mit Administratorrechten, und öffnen Sie das Projekt erneut.

    Zum Bereitstellen Ihrer app mit Web Deploy sind Administratorrechte erforderlich.

1. Klicken Sie im **Projektmappen-Explorer**mit der rechten Maustaste auf den Projektknoten, und wählen Sie **Veröffentlichen**aus.

    Wenn Sie Veröffentlichungsprofile, zuvor konfiguriert haben die **veröffentlichen** angezeigt. Klicken Sie auf **neues Profil**.

1. Für **Veröffentlichungsziel auswählen**Option **IIS, FTP usw.** , und klicken Sie auf **veröffentlichen**.

    ![RemoteDBG_Publish_IISl](../media/remotedbg_iis_profile.png "RemoteDBG_Publish_IIS")

1. Geben Sie die Konfigurationsparameter für die Korrektur für der IIS-Konfiguration ein.

    ![RemoteDBG_Publish_WebDeployl](../media/remotedbg_iis_webdeploy_config.png "RemoteDBG_Publish_WebDeploy")

    Wenn ein Hostname nicht behoben wird, wenn Sie versuchen, überprüfen Sie in den nächsten Schritten, in der **Server** Text im Feld, und versuchen Sie die IP-Adresse. Umfassen `http://` als Präfix in der **Server** Feld.  Stellen Sie sicher, dass Sie Port 80 der **Server** Text, und stellen Sie sicher, dass Port 80 in der Firewall geöffnet ist.

1. Klicken Sie auf **Weiter**, wählen Sie eine **Debuggen** -Konfiguration, und wählen Sie **entfernen weiterer Dateien am Ziel** unter der **-Datei veröffentlichen** Optionen.

    > [!NOTE]
    > Wenn Sie eine Releasekonfiguration auswählen, deaktivieren Sie das Debuggen in der Datei "Web.config", bei der Veröffentlichung.

1. Klicken Sie auf **Prev**, und wählen Sie dann **überprüfen**. Wenn die Einrichtung der Verbindung überprüft hat, können Sie versuchen, zu veröffentlichen.

1. Klicken Sie auf **veröffentlichen** zum Veröffentlichen der app.

    Die Registerkarte "Ausgabe" zeigt an, ob die Veröffentlichung erfolgreich war und Ihr Browser öffnet dann die app.

    Wenn Sie erwähnen, Web Deploy-Fehler erhalten, überprüfen Sie die Schritte für die Web Deploy-Installation, und stellen Sie sicher, dass die richtigen Ports geöffnet sind (Web Deploy erfordert auch Port 8172 zu öffnen, auf dem Server sein).

    Wenn die app erfolgreich bereitgestellt, aber nicht ordnungsgemäß ausgeführt werden kann, gibt es möglicherweise ein Problem mit der IIS-Konfiguration, die ASP.NET-Installation oder Konfiguration Ihrer Website vor. Öffnen Sie auf dem Windows-Server die Website aus IIS für genauere Fehlermeldungen, und überprüfen Sie dann die vorangegangenen Schritte erneut aus.

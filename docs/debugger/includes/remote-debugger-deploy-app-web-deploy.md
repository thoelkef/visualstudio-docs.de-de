---
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.openlocfilehash: 27cff46f5a68ef28f247aa159a2b8be5db56b0fe
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
Wenn Sie Web Deploy, mit dem Webplattform-Installer installiert haben, können Sie die app direkt in Visual Studio bereitstellen.

1. Starten Sie Visual Studio mit Administratorrechten, und öffnen Sie das Projekt erneut.

    Zum Bereitstellen Ihrer app mithilfe von Web Deploy sind Administratorrechte erforderlich.

2. Klicken Sie im **Projektmappen-Explorer**mit der rechten Maustaste auf den Projektknoten, und wählen Sie **Veröffentlichen**aus.

3. Für **Veröffentlichungsziel auswählen**Option **IIS, FTP usw.** , und klicken Sie auf **veröffentlichen**.

    ![RemoteDBG_Publish_IISl](../media/remotedbg_iis_profile.png "RemoteDBG_Publish_IIS")

4. Geben Sie die Korrektur Konfigurationsparameter für die IIS-Konfiguration.

    ![RemoteDBG_Publish_WebDeployl](../media/remotedbg_iis_webdeploy_config.png "RemoteDBG_Publish_WebDeploy")

    Wenn Sie ein Hostnamen nicht behoben wird, wenn Sie versuchen, überprüfen Sie in den nächsten Schritten, in der **Server** Text im Feld, und versuchen Sie die IP-Adresse. Umfassen `http://` als Präfix in der **Server** Feld.  Stellen Sie sicher, dass die Verwendung von Port 80 in der **Server** Text ein, und stellen Sie sicher, dass Port 80 in der Firewall geöffnet ist.

6. Klicken Sie auf **Weiter**, wählen Sie eine **Debuggen** Konfiguration, und wählen Sie **entfernen weiterer Dateien am Ziel** unter der **-Datei veröffentlichen** Optionen.

    > [!NOTE]
    > Bei Auswahl eine Releasekonfiguration wird Sie beim Veröffentlichen in der Datei "Web.config"-Debuggen deaktivieren.

5. Klicken Sie auf **Prev**, und wählen Sie dann **Validate**. Wenn dem Einrichten der Verbindung überprüft hat, können Sie versuchen, veröffentlichen.

6. Klicken Sie auf **veröffentlichen** zum Veröffentlichen der app.

    Die Registerkarte "Ausgabe" zeigt an, ob die Publishing ist erfolgreich, und Ihr Browser öffnet dann die app.

    Wenn Sie einen Web Deploy erwähnen Fehler erhalten, überprüfen Sie die Installationsschritte Web Deploy erneut, und stellen Sie sicher, dass die richtigen Ports geöffnet sind (Web Deploy erfordert außerdem Port 8172 auf dem Server geöffnet sein).

    Wenn die app erfolgreich bereitgestellt, aber nicht ordnungsgemäß ausgeführt werden kann, gibt es möglicherweise ein Problem mit der IIS-Konfiguration, die ASP.NET-Installation oder Konfiguration Ihrer Website. Öffnen Sie auf dem Windows-Server die Website aus IIS finden Sie spezifischere Fehlermeldungen, und überprüfen Sie dann erneut bereits beschriebenen Schritte.
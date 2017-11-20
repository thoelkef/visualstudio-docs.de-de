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
ms.openlocfilehash: a55b2a12c9a45c5a3952e3e6f4e1627bec8ba520
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
1. In der **Projektmappen-Explorer**mit der rechten Maustaste auf den Projektknoten, und wählen Sie **veröffentlichen** (für Web Forms, **Web-App veröffentlichen**).

2. In der **veröffentlichen** wählen Sie im Dialogfeld **Ordner**, klicken Sie auf **Durchsuchen**, und erstellen Sie einen neuen Ordner **C:\Publish**.

    ![RemoteDBG_Publish_Local](../media/remotedbg_publish_local.png "RemoteDBG_Publish_Local")

    Wählen Sie für eine Web Forms-app **benutzerdefinierte** Geben Sie im Dialogfeld "Veröffentlichen" einen Profilnamen ein, und wählen Sie **OK**.

3. Klicken Sie auf **Veröffentlichen**.

    Visual Studio veröffentlicht das Projekt den Ordner. Fortschritt zeigt im Ausgabefenster angezeigt.

4. In der **veröffentlichen** (Dialogfeld), klicken Sie auf die **Einstellungen** verknüpfen, und wählen Sie dann die **Einstellungen** Registerkarte.

5. Legen Sie die Konfiguration auf **Debuggen**Option **alle vorhandenen Dateien vor der Veröffentlichung löschen**, und klicken Sie dann auf **speichern**.

    > [!NOTE]
    > Wenn Sie einen Releasebuild verwenden, deaktivieren Sie das Debuggen in der Datei "Web.config" bei der Veröffentlichung.

6. Klicken Sie auf **Veröffentlichen**.

    ![RemoteDBG_Publish_Debug_Config](../media/remotedbg_publish_debug_config.png "RemoteDBG_Publish_Debug_Config")
    
    Die Anwendung veröffentlicht eine **Debuggen** Konfiguration des Projekts, um den lokalen Ordner.

5. Kopieren Sie das ASP.NET-Projektverzeichnis vom Visual Studio-Computer in das lokale Verzeichnis für die ASP.NET app konfiguriert wurde (in diesem Beispiel **C:\Publish**) auf dem Windows Server-Computer. In diesem Lernprogramm gehen wir davon aus, Sie manuell kopieren, aber Sie können andere Tools, z. B. PowerShell, Xcopy oder Robocopy verwenden.

    > [!CAUTION]
    >  Wenn Sie den Code oder Rebuild ändern müssen, müssen Sie erneut veröffentlichen, und wiederholen Sie diesen Schritt. Die ausführbare Datei, die Sie auf den Remotecomputer kopiert haben, muss genau mit der lokalen Quelle und den lokalen Symbolen übereinstimmen.

6. Stellen Sie sicher, dass Sie die app ordnungsgemäß ausführen können, indem die app in Ihrem Browser öffnen, auf dem Windows Server.

    Falls die Anwendung ordnungsgemäß ausgeführt wird, gibt es möglicherweise ein Konflikt zwischen der Version von ASP.NET auf dem Server und Visual Studio-Computer installiert, oder Sie möglicherweise ein Problem bei der Konfiguration von IIS oder die Website. Überprüfen Sie die bereits beschriebenen Schritte.
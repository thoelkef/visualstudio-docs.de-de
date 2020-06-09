---
ms.openlocfilehash: f286002112667ba763419f0e3d6265dbe1942212
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2020
ms.locfileid: "84173877"
---

1. Klicken Sie auf dem Computer, auf dem das ASP.NET-Projekt in Visual Studio geöffnet ist, erst mit der rechten Maustaste auf das Projekt im Projektmappen-Explorer und anschließend mit der linken auf **Veröffentlichen**.

1. Wenn Sie bereits Veröffentlichungsprofile konfiguriert haben, wird der Bereich **Veröffentlichen** angezeigt. Klicken Sie auf **Neues Profil erstellen**.

1. Klicken Sie im Dialogfeld **Pick a publish target** (Veröffentlichungsziel auswählen) auf **Profil importieren**.

    ![„Veröffentlichen“ auswählen](../../deployment/media/tutorial-publish-tool-import-profile.png)

1. Navigieren Sie zum Speicherort der Datei mit Veröffentlichungseinstellungen, die Sie bereits erstellt haben.

1. Navigieren Sie im Dialogfeld **Datei mit Veröffentlichungseinstellungen importieren** zu dem Profil, das Sie im vorherigen Abschnitt erstellt haben, wählen Sie es aus, und klicken Sie dann auf **Öffnen**.

    Dann beginnt Visual Studio mit dem Bereitstellungsprozess, und im Ausgabefenster werden der Fortschritt und die Ergebnisse angezeigt.

    Wenn bei der Bereitstellung Fehler entstehen sollten, klicken Sie auf **Einstellungen**, um die Einstellungen zu bearbeiten. Ändern Sie die Einstellungen, und klicken Sie auf **Überprüfen**, um die neuen Einstellungen zu testen. Wenn der Hostname nicht gefunden wird, geben Sie stattdessen die IP-Adresse in die Felder **Server** und **Ziel-URL** ein.

    ![Bearbeiten von Einstellungen im Tool zum Veröffentlichen](../../deployment/media/tutorial-configure-publish-settings-in-tool.png)

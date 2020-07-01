---
ms.openlocfilehash: a292b37a50bbf667fa5b23f18879cd79c3f76805
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/23/2020
ms.locfileid: "85292089"
---
Web Deploy 3.6 für Hostingserver umfasst zusätzliche Konfigurationsfeatures für die Erstellung der Datei mit Veröffentlichungseinstellungen über die Benutzeroberfläche.

1. Wenn Sie Web Deploy bereits unter Windows Server installiert haben, führen Sie über **Einstellungen** > **Programme** > **Programm deinstallieren** eine Deinstallation durch.

2. Installieren Sie anschließend Web Deploy 3.6 für Hostingserver in Windows Server.

    Verwenden Sie den Webplattform-Installer (Web PI) für die Installation von Web Deploy für Hostingserver. (Sie finden den Link zum Web PI über IIS, wenn Sie links im Server-Manager auf **IIS** klicken. Klicken sie zuerst im Serverbereich mit der rechten Maustaste auf den Server, und wählen Sie dann **Internet Information Services (IIS) Manager (Internetinformationsdienste-Manager)** aus. Verwenden Sie dann den Link **Neue Webplattformkomponenten abrufen** im Fenster **Aktionen**. Sie können den Webplattform-Installer (Web PI) auch über [Downloads](https://www.microsoft.com/web/downloads/platform.aspx) abrufen.

    Im Webplattform-Installer finden Sie **Web Deploy 3.6 für Hostingserver** auf der Registerkarte „Anwendungen“.

3. Installieren Sie, falls noch nicht geschehen, die **Verwaltungsskripts und -tools für IIS**.

    Navigieren Sie zu **Serverrollen auswählen** > **Web Server (IIS)**  > **Verwaltungstools**, wählen Sie die Rolle **IIS Management Scripts and Tools** (Verwaltungsskripts und -tools für IIS) aus, klicken Sie auf **Weiter**, und installieren Sie die Rolle.

    ![Installieren von Verwaltungsskripts und -tools für IIS](../../deployment/media/tutorial-iis-management-scripts-and-tools.png)

    Sie müssen die Skripts und Tools installieren, damit die Datei mit Veröffentlichungseinstellungen erstellt werden kann.

4. (Optional) Überprüfen Sie, ob Web Deploy ordnungsgemäß ausgeführt wird, indem Sie **Einstellungen > System und Sicherheit > Verwaltung > Dienste** öffnen und sich vergewissern, dass der:

    * **Webbereitstellungs-Agent-Dienst** ausgeführt wird (in älteren Versionen lautet der Dienstname anders).

    * **Webverwaltungsdienst** ausgeführt wird.

    Wenn einer der Agent-Dienste nicht läuft, starten Sie den **Webbereitstellungs-Agent-Dienst** neu.

    Wenn der Webbereitstellungs-Agent-Dienst gar nicht vorhanden ist, navigieren Sie zu **Einstellungen > Programm > Programm deinstallieren**, und suchen Sie die **Microsoft Web Deploy-\<version>** . **Ändern** Sie die Installation, und vergewissern Sie sich, dass Sie für die Web Deploy-Komponenten **Will be installed to the local hard drive** (Wird auf der lokalen Festplatte installiert) auswählen. Führen Sie die Schritte zur Änderung der Installation durch.
---
title: Entsperren Sie den Download der Remotetools
ms.custom: ''
ms.date: 07/19/2018
ms.technology: vs-ide-debug
ms.topic: troubleshooting
helpviewer_keywords:
- remote debugging, unblock download
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e0586b8f0699ec2eca5843d59df1b6ddd7cecbd3
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/20/2018
ms.locfileid: "39180659"
---
# <a name="how-to-unblock-the-download-of-the-remote-tools-on-windows-server"></a>Vorgehensweise: entsperren Sie den Download der Remotetools unter Windows Server

Die standardsicherheitseinstellungen in Internet Explorer unter Windows Server können zum Herunterladen von Komponenten wie z. B. die Remotetools zeitaufwändige gestalten.

* Durch die verstärkte Sicherheitskonfiguration für Internet Explorer, der verhindert, dass Sie von Websites öffnen und den Zugriff auf Webressourcen, es sei denn, die Domäne, die mit der Ressource explizit zugelassen wird aktiviert ist (d. h. vertrauenswürdig). Obwohl Sie diese Einstellung deaktivieren können, empfohlen nicht es, da er ein Sicherheitsrisiko darstellen kann.

* Unter Windows Server 2016 eine Standardeinstellung in **Internetoptionen** > **Sicherheit** > **Internet**  >   **Stufe** > **Downloads** auch deaktiviert Dateidownloads. Wenn Sie die Remoteserver-Verwaltungstools unter Windows Server direkt herunterladen möchten, müssen Sie die Datei zum Herunterladen aktivieren.

Herunterladen von Tools unter Windows Server, empfehlen wir eine der folgenden:

* Laden Sie die Remoteserver-Verwaltungstools auf einem anderen Computer wie die einer ausgeführten Visual Studio, und kopieren Sie die *.exe* -Datei mit Windows Server.

* Ausführen des Remotedebuggers [aus einer Dateifreigabe](../debugger/remote-debugging.md#fileshare_msvsmon) auf Ihrem Computer Visual Studio.

* Laden Sie die Remoteserver-Verwaltungstools direkt auf Windows Server, und akzeptieren Sie die aufforderungen, um den vertrauenswürdigen Sites hinzufügen. Moderne Websites enthalten häufig viele Ressourcen von Drittanbietern, damit dies zahlreiche Anweisungen führen kann. Darüber hinaus müssen alle umgeleiteten Links manuell hinzugefügt werden. Sie können auch einige der vertrauenswürdigen Sites hinzufügen, bevor Sie den Download ab. Wechseln Sie zu **Internetoptionen > Sicherheit > Vertrauenswürdige Sites > Websites** und fügen Sie den folgenden Websites hinzu.

  * VisualStudio.Microsoft.com
  * download.visualstudio.microsoft.com
  * Informationen zu: leer

  Fügen Sie bei älteren Versionen des Debuggers auf my.visualstudio.com wird diese zusätzliche Websites hinzu, stellen Sie sicher, dass diese Anmeldung erfolgreich ist:

  * microsoft.com
  * go.microsoft.com
  * 0download.microsoft.com
  * My.VisualStudio.com
  * "Login.microsoftonline.com"
  * Login.Live.com
  * Secure.aadcdn.microsoftonline-p.com
  * msft.STS.Microsoft.com
  * auth.GFX.ms
  * app.vssps.visualstudio.com
  * vlscppe.Microsoft.com
  * Query.Prod.CMS.RT.Microsoft.com

    Wenn Sie diese Domänen, die beim Herunterladen der Remoteserver-Verwaltungstools hinzufügen möchten, und wählen Sie dann **hinzufügen** Aufforderung.

    ![Blockierte Content (Dialogfeld)](../debugger/media/remotedbg-blocked-content.png)

    Wenn Sie die Software herunterladen, erhalten Sie einige zusätzlichen Anforderungen zum Laden von verschiedenen Website-Skripts und Ressourcen berechtigt zu gewähren. Auf my.visualstudio.com empfehlen wir, dass Sie, die zusätzlichen Domänen hinzufügen an, stellen Sie sicher, dass diese Anmeldung erfolgreich ist.
---
title: Freischalten des Remotetooldownloads
ms.date: 07/19/2018
ms.topic: troubleshooting
helpviewer_keywords:
- remote debugging, unblock download
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8a243033bf5831952d83fdf688302651e02b76b7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62903022"
---
# <a name="how-to-unblock-the-download-of-the-remote-tools-on-windows-server"></a>Vorgehensweise: Freischalten des Downloads der Remotetools unter Windows Server

Aufgrund der Standardsicherheitseinstellungen in Internet Explorer unter Windows Server kann es sehr zeitaufwändig sein, Komponenten wie die Remotetools herunterzuladen.

* Die verstärkte Sicherheitskonfiguration ist in Internet Explorer aktiviert. Sie können also weder Websites öffnen noch auf Webressourcen zugreifen, es sei denn, die Domäne, die die Ressource enthält, wurde explizit zugelassen (d. h. sie ist vertrauenswürdig). Obwohl Sie diese Einstellung deaktivieren können, wird dies nicht empfohlen, da die Deaktivierung ein Sicherheitsrisiko darstellen kann.

* Unter Windows Server 2016 werden Dateidownloads durch eine Standardeinstellung unter **Internetoptionen** > **Sicherheit** > **Internet** > **Stufe anpassen** > **Downloads** deaktiviert. Wenn Sie die Remotetools direkt unter Windows Server herunterladen möchten, müssen Sie zunächst den Dateidownload aktivieren.

Zum Herunterladen der Tools unter Windows Server wird eine der folgenden Vorgehensweisen empfohlen:

* Laden Sie die Remotetools auf einem anderen Computer herunter, z. B. auf dem Computer, auf dem Visual Studio ausgeführt wird. Kopieren Sie dann die *EXE*-Datei zu Windows Server.

* Führen Sie den Remotedebugger [auf einer Dateifreigabe](../debugger/remote-debugging.md#fileshare_msvsmon) auf Ihrem Visual Studio-Computer aus.

* Laden Sie die Remotetools direkt unter Windows Server herunter, und akzeptieren Sie die Aufforderungen zum Hinzufügen von vertrauenswürdigen Websites. Moderne Websites enthalten häufig viele Drittanbieterressourcen. Möglicherweise werden Ihnen daher sehr viele Aufforderungen angezeigt. Außerdem müssen Umleitungs-URLs, sofern vorhanden, möglicherweise manuell hinzugefügt werden. Sie können einige der vertrauenswürdigen Websites bereits vor dem Download hinzufügen. Navigieren Sie zu **Internetoptionen > Sicherheit > Vertrauenswürdige Sites > Sites**, und fügen Sie die folgenden Websites hinzu.

  * visualstudio.microsoft.com
  * download.visualstudio.microsoft.com
  * about:blank

  Fügen Sie auf my.visualstudio.com für ältere Versionen des Debuggers außerdem diese Websites hinzu, um sicherzustellen, dass die Anmeldung erfolgreich ist:

  * microsoft.com
  * go.microsoft.com
  * 0download.microsoft.com
  * my.visualstudio.com
  * login.microsoftonline.com
  * login.live.com
  * secure.aadcdn.microsoftonline-p.com
  * msft.sts.microsoft.com
  * auth.gfx.ms
  * app.vssps.visualstudio.com
  * vlscppe.microsoft.com
  * query.prod.cms.rt.microsoft.com

    Wenn Sie diese Domänen beim Herunterladen der Remotetools hinzufügen möchten, klicken Sie auf **Hinzufügen**, wenn Sie dazu aufgefordert werden.

    ![Dialogfeld zu blockierten Inhalten](../debugger/media/remotedbg-blocked-content.png)

    Wenn Sie die Software herunterladen, werden Sie möglicherweise auch dazu aufgefordert, die Berechtigung zum Laden verschiedener Websiteskripts und -ressourcen zu erteilen. Es ist empfehlenswert, auf my.visualstudio.com die zusätzlichen Domänen hinzuzufügen, um sicherzustellen, dass die Anmeldung erfolgreich ist.
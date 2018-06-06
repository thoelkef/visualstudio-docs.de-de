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
ms.openlocfilehash: c22ba73b464f91bf3036541304cdf94e8660970d
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2018
ms.locfileid: "34794212"
---
1. Wenn Sie Ihre Anwendungen mit Web Deploy in Visual Studio bereitstellen möchten, installieren Sie die neueste Version von Web Deploy auf dem Server.

    Um Web Deploy installieren, verwenden die [Webplattform-Installer (WebPI)](https://www.microsoft.com/web/downloads/platform.aspx). (Wählen Sie den Webplattform-Installer Link von IIS finden **IIS** im linken Bereich des Server-Managers. Mit der rechten Maustaste in des Servers, und wählen Sie **(Internet Information Services, IIS) Manager**.)

    In den Webplattform-Installer finden Sie Web Deploy in der Registerkarte "Anwendungen". Sie erhalten auch ein Installationsprogramm direkt aus der [Microsoft Download Center](https://www.microsoft.com/search/result.aspx?q=webdeploy&form=dlc). 

2. Vergewissern Sie sich, Web Deploy durch Öffnen des ordnungsgemäß ausgeführt wird **Systemsteuerung > System und Sicherheit > Verwaltung > Dienste** und stellen Sie sicher, dass **Webbereitstellungs-Agent-Dienst** ausgeführt wird (die Name des Diensts unterscheidet sich in älteren Versionen).

    Wenn der Agent-Dienst nicht ausgeführt wird, starten Sie ihn aus. Wenn es nicht vorhanden ist, wechseln Sie zu **Systemsteuerung > Programme > Programm deinstallieren**, suchen **Microsoft Web Deploy <version>** . Wählen Sie auf **ändern** die Installation und stellen Sie sicher, dass Sie auswählen, **wird auf der lokalen Festplatte installiert werden** für die Web Deploy-Komponenten. Führen Sie die Installationsschritte ändern.
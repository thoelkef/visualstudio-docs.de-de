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
ms.sourcegitcommit: 1c675dae7c348defb32d9f7ccf7079a1062a1c4b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/03/2018
ms.locfileid: "48244118"
---
1. Wenn Sie beabsichtigen, Ihre Anwendungen mit Web Deploy in Visual Studio bereitstellen, installieren Sie die neueste Version von Web Deploy auf dem Server.

    Um Web Deploy zu installieren, verwenden die [Webplattform-Installer (WebPI)](https://www.microsoft.com/web/downloads/platform.aspx). (Um den Webplattform-Installer-Link aus IIS zu suchen, wählen **IIS** im linken Bereich des Server-Managers. Mit der rechten Maustaste in des Servers, und wählen Sie **(Internet Information Services, IIS) Manager**.)

    In den Webplattform-Installer finden Sie Web Deploy auf der Registerkarte "Anwendungen". Sie erhalten auch ein Installationsprogramm direkt aus der [Microsoft Download Center](https://www.microsoft.com/search/result.aspx?q=webdeploy&form=dlc). 

2. Stellen Sie sicher, dass Web Deploy öffnen ordnungsgemäß ausgeführt wird **Systemsteuerung > System und Sicherheit > Verwaltung > Dienste** und stellen Sie sicher, dass **Webbereitstellungs-Agent-Dienst** ausgeführt wird (die Name des Diensts unterscheidet sich in älteren Versionen).

    Wenn der Agent-Dienst nicht ausgeführt wird, starten Sie ihn aus. Wenn es nicht vorhanden ist, fahren Sie mit **Systemsteuerung > Programme > Programm deinstallieren**, finden Sie **Microsoft Web Deploy <version>** . Wählen Sie auf **Änderung** die Installation und stellen Sie sicher, dass Sie auswählen **auf der lokalen Festplatte installiert werden** für die Web Deploy-Komponenten. Führen Sie die Installationsschritte ändern.
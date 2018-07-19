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
ms.openlocfilehash: 103000c2ded944236762ffd55603877ece7b7968
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2018
ms.locfileid: "38809442"
---
Diese Schritte zeigen nur eine einfache Konfiguration von IIS. Ausführlichere Informationen zu einem Windows-Desktop-Computer installieren, finden Sie [Publishing to IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration) oder [IIS 8.0 mithilfe von ASP.NET 3.5 und ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

Für Windows Server-Betriebssysteme verwenden die **Rollen und Features hinzufügen** Assistenten über die **verwalten** Link oder die **Dashboard** -link in **fürServer-Manager**. Aktivieren Sie im Schritt **Serverrollen** das Kontrollkästchen für **Webserver (IIS)**.

![Die Rolle „Webserver (IIS)“ wird im Schritt „Serverrollen auswählen“ ausgewählt.](../media/remotedbg-server-roles-ws2012.png)

Wählen Sie im Schritt **Rollendienste** die gewünschten IIS-Rollendienste aus, oder übernehmen Sie die angegebenen Standardrollendienste. Wenn Sie mit der Bereitstellung aktivieren möchten Sie veröffentlichungseinstellungen und Web Deploy, stellen Sie sicher, dass **IIS-Verwaltungsskripts und-Tools** ausgewählt ist.

Die Bestätigung Schritte zum Installieren der Webserverrolle und Dienste fortgesetzt werden. Ein Server-/IIS-Neustart ist nach der Installation der Rolle „Webserver (IIS)“ nicht erforderlich.
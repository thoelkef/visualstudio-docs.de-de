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
ms.openlocfilehash: dbc9d727dc412e3d354d806a45c352eef810cd99
ms.sourcegitcommit: 9357209350167e1eb7e50b483e44893735d90589
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/05/2018
---
Diese Schritte zeigen nur eine Standardkonfiguration von IIS. Ausführlichere Informationen oder an einen Windows-Desktop-Computer installieren, finden Sie unter [in IIS veröffentlichen](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration) oder [IIS 8.0 mithilfe von ASP.NET 3.5 und ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

Für Windows Server-Betriebssysteme verwenden die **Hinzufügen von Rollen und Features** Assistenten über die **verwalten** Link oder die **Dashboard** link **Server-Manager**. Aktivieren Sie im Schritt **Serverrollen** das Kontrollkästchen für **Webserver (IIS)**.

![Die Rolle „Webserver (IIS)“ wird im Schritt „Serverrollen auswählen“ ausgewählt.](../media/remotedbg-server-roles-ws2012.png)

Wählen Sie im Schritt **Rollendienste** die gewünschten IIS-Rollendienste aus, oder übernehmen Sie die angegebenen Standardrollendienste.

Durch die Bestätigung Schritte zum Installieren der Webserverrolle und Dienste fortgesetzt werden. Ein Server-/IIS-Neustart ist nach der Installation der Rolle „Webserver (IIS)“ nicht erforderlich.
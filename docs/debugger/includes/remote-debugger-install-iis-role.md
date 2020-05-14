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
ms.openlocfilehash: 13ca035b01ec8af1277d70b3c792293a1af4687a
ms.sourcegitcommit: 748d9cd7328a30f8c80ce42198a94a4b5e869f26
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68149228"
---
Diese Schritte zeigen nur eine Basiskonfiguration von IIS. Ausführlichere Informationen oder eine Anleitung für die Installation auf einem Windows-Desktopcomputer finden Sie unter [Veröffentlichen in IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration) oder [IIS 8.0 Using ASP.NET 3.5 and ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) (IIS 8.0 mithilfe von ASP.NET 3.5 und ASP.NET 4.5, in englischer Sprache).

Verwenden Sie für Windows Server-Betriebssysteme den Assistenten **Rollen und Features hinzufügen** über den Link **Verwalten** oder den Link **Dashboard** im **Server-Manager**. Aktivieren Sie im Schritt **Serverrollen** das Kontrollkästchen für **Webserver (IIS)** .

![Die Rolle „Webserver (IIS)“ wird im Schritt „Serverrollen auswählen“ ausgewählt.](../media/remotedbg-server-roles-ws2012.png)

Wählen Sie im Schritt **Rollendienste** die gewünschten IIS-Rollendienste aus, oder übernehmen Sie die angegebenen Standardrollendienste. Wenn Sie die Bereitstellung mithilfe von Veröffentlichungseinstellungen und Web Deploy aktivieren möchten, stellen Sie sicher, dass **IIS-Verwaltungsskripts und -tools** ausgewählt ist.

Führen Sie die Bestätigungsschritte durch, um die Webserverrolle und die Dienste zu installieren. Ein Server-/IIS-Neustart ist nach der Installation der Rolle „Webserver (IIS)“ nicht erforderlich.
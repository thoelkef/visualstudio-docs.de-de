---
title: Proxyautorisierung erforderlich | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: troubleshooting
ms.assetid: c2d24ae1-9902-460e-b72a-0299eed9ee82
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 848817691d7fae32f2240e3d6cac4451c4ce58c4
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297820"
---
# <a name="proxy-authorization-required"></a>Proxyautorisierung erforderlich
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

The **Proxy authorization required** error generally occurs when users are connected to Visual Studio online resources through a proxy server, and the proxy server blocks the calls.

To correct this error, try one or more of the following steps:

- Starten Sie Visual Studio neu. Das Dialogfeld Proxy-Authentifizierung sollte angezeigt werden. Geben Sie Ihre Anmeldeinformationen in das Dialogfeld ein.

- Wenn durch die oben genannten Schritte das Problem nicht behoben wird, besteht die Möglichkeit, dass der Proxyserver Sie nicht zur Eingabe von Anmeldeinformationen für https://go.microsoft.com -Adressen, sondern für die *. visualStudio.com-Adressen auffordert. For these servers, you need to add the following URLs to the allow list to unblock all sign-in scenarios in Visual Studio:

  - *.windows.net

  - *.microsoftonline.com

  - *.visualstudio.com

  - *.microsoft.com

  - *.live.com

- You can remove the https://go.microsoft.com address from the allow list so that the proxy authentication dialog shows up for both the https://go.microsoft.com address and the server endpoints when Visual Studio is restarted.

- If you want to use your default credentials with your proxy, do the following:

   1. Suchen Sie „devenv.exe.config“ (die devenv.exe-Konfigurationsdatei) in **%ProgramFiles%\Microsoft Visual Studio 14.0\Common7\IDE** (oder **%ProgramFiles(x86)%\Microsoft Visual Studio 14.0\Common7\IDE**).

   2. Suchen Sie in der Konfigurationsdatei die `<system.net>` -Sperre und fügen Sie diesen Code hinzu:

      ```xml
      <defaultProxy enabled="true" useDefaultCredentials="true">
          <proxy bypassonlocal="True" proxyaddress=" HYPERLINK "http://<yourproxy:port#" http://<yourproxy:port#>"/>
      </defaultProxy>
      ```

      Insert the correct proxy address for your network in `proxyaddress="<http://<yourproxy:port#>`.

- Follow the instructions in [this blog post](https://blogs.msdn.microsoft.com/rido/2010/05/06/how-to-connect-to-tfs-through-authenticated-web-proxy/) to add code that allows you to use the proxy.

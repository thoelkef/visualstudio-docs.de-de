---
title: Proxyautorisierung erforderlich | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: troubleshooting
ms.assetid: c2d24ae1-9902-460e-b72a-0299eed9ee82
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: f2de40c520bca0ea04f50ec782fec2dda531172e
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2019
ms.locfileid: "67822070"
---
# <a name="proxy-authorization-required"></a>Proxyautorisierung erforderlich
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die **Proxyautorisierung erforderlich** Fehler tritt im Allgemeinen auf, wenn Benutzer mit Visual Studio online-Ressourcen über einen Proxyserver verbunden sind, und der Proxyserver die Aufrufe blockiert.

Um diesen Fehler zu beheben, versuchen Sie eine oder mehrere der folgenden Schritte aus:

- Starten Sie Visual Studio neu. Das Dialogfeld Proxy-Authentifizierung sollte angezeigt werden. Geben Sie Ihre Anmeldeinformationen in das Dialogfeld ein.

- Wenn durch die oben genannten Schritte das Problem nicht behoben wird, besteht die Möglichkeit, dass der Proxyserver Sie nicht zur Eingabe von Anmeldeinformationen für http://go.microsoft.com -Adressen, sondern für die *. visualStudio.com-Adressen auffordert. Für diese Server müssen Sie die folgenden URLs der Liste "zulassen" Blockierung aller anmeldeszenarien in Visual Studio hinzufügen:

  - *.windows.net

  - *.microsoftonline.com

  - *.visualstudio.com

  - *.microsoft.com

  - *.live.com

- Können Sie entfernen die http://go.microsoft.com aus der Liste zugelassener zu beheben, sodass das Dialogfeld Proxy-Authentifizierung für beide angezeigt werden, wird die http://go.microsoft.com Adresse und den Serverendpunkten, wenn Visual Studio neu gestartet wird.

- Wenn Sie die standardmäßigen Anmeldeinformationen mit Ihrem Proxy verwenden möchten, führen Sie folgende Schritte aus:

   1. Suchen Sie „devenv.exe.config“ (die devenv.exe-Konfigurationsdatei) in **%ProgramFiles%\Microsoft Visual Studio 14.0\Common7\IDE** (oder **%ProgramFiles(x86)%\Microsoft Visual Studio 14.0\Common7\IDE**).

   2. Suchen Sie in der Konfigurationsdatei die `<system.net>` -Sperre und fügen Sie diesen Code hinzu:

      ```xml
      <defaultProxy enabled="true" useDefaultCredentials="true">
          <proxy bypassonlocal="True" proxyaddress=" HYPERLINK "http://<yourproxy:port#" http://<yourproxy:port#>"/>
      </defaultProxy>
      ```

      Fügen Sie die korrekte Proxy-Adresse für Ihr Netzwerk in `proxyaddress="<http://<yourproxy:port#>`.

- Befolgen Sie die Anweisungen in [in diesem Blogbeitrag](http://blogs.msdn.com/b/rido/archive/2010/05/06/how-to-connect-to-tfs-through-authenticated-web-proxy.aspx) Code hinzufügen, die Sie den Proxy verwenden können.

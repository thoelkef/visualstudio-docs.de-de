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
# <a name="proxy-authorization-required"></a>Proxyautorisierung erforderlich.
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Der Fehler " **Proxy Autorisierung erforderlich** " tritt im Allgemeinen auf, wenn Benutzer über einen Proxy Server mit Visual Studio Online-Ressourcen verbunden sind und der Proxy Server die Aufrufe blockiert.

Um diesen Fehler zu beheben, führen Sie einen oder mehrere der folgenden Schritte aus:

- Starten Sie Visual Studio neu. Das Dialogfeld Proxy-Authentifizierung sollte angezeigt werden. Geben Sie Ihre Anmeldeinformationen in das Dialogfeld ein.

- Wenn durch die oben genannten Schritte das Problem nicht behoben wird, besteht die Möglichkeit, dass der Proxyserver Sie nicht zur Eingabe von Anmeldeinformationen für https://go.microsoft.com-Adressen, sondern für die *. visualStudio.com-Adressen auffordert. Für diese Server müssen Sie die folgenden URLs zur Zulassungsliste hinzufügen, um die Blockierung aller Anmelde Szenarien in Visual Studio zu ermöglichen:

  - *.windows.net

  - *.microsoftonline.com

  - *. visualStudio.com

  - *.microsoft.com

  - *.live.com

- Sie können die https://go.microsoft.com Adresse aus der Zulassungsliste entfernen, damit das Dialogfeld für die Proxy Authentifizierung sowohl für die https://go.microsoft.com Adresse als auch die Server Endpunkte angezeigt wird, wenn Visual Studio neu gestartet wird.

- Wenn Sie Ihre Standard Anmelde Informationen mit Ihrem Proxy verwenden möchten, gehen Sie folgendermaßen vor:

   1. Suchen Sie „devenv.exe.config“ (die devenv.exe-Konfigurationsdatei) in **%ProgramFiles%\Microsoft Visual Studio 14.0\Common7\IDE** (oder **%ProgramFiles(x86)%\Microsoft Visual Studio 14.0\Common7\IDE**).

   2. Suchen Sie in der Konfigurationsdatei die `<system.net>` -Sperre und fügen Sie diesen Code hinzu:

      ```xml
      <defaultProxy enabled="true" useDefaultCredentials="true">
          <proxy bypassonlocal="True" proxyaddress=" HYPERLINK "http://<yourproxy:port#" http://<yourproxy:port#>"/>
      </defaultProxy>
      ```

      Fügen Sie die korrekte Proxy Adresse für Ihr Netzwerk in `proxyaddress="<http://<yourproxy:port#>`ein.

- Befolgen Sie die Anweisungen in [diesem Blogbeitrag](https://blogs.msdn.microsoft.com/rido/2010/05/06/how-to-connect-to-tfs-through-authenticated-web-proxy/) , um Code hinzuzufügen, mit dem Sie den Proxy verwenden können.

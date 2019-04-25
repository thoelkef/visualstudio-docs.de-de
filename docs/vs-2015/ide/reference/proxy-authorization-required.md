---
title: Proxyautorisierung erforderlich | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
ms.assetid: c2d24ae1-9902-460e-b72a-0299eed9ee82
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 74f8fdd738c613977a73cc3d79b5ba880c7e6e74
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60116094"
---
# <a name="proxy-authorization-required"></a>Proxyautorisierung erforderlich
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Dieser Fehler tritt normalerweise auf, wenn Benutzer in Visual Studio Online über einen Proxyserver verbunden sind, und der Proxy-Server die Aufrufe blockiert. Visual Studio Online wird verwendet, um den Benutzer in der IDE angemeldet zu lassen.  
  
## <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
- Starten Sie Visual Studio neu. Das Dialogfeld Proxy-Authentifizierung sollte angezeigt werden. Geben Sie Ihre Anmeldeinformationen in das Dialogfeld ein.  
  
- Wenn durch die oben genannten Schritte das Problem nicht behoben wird, besteht die Möglichkeit, dass der Proxyserver Sie nicht zur Eingabe von Anmeldeinformationen für http://go.microsoft.com-Adressen, sondern für die *. visualStudio.com-Adressen auffordert. Für diese Server müssen Sie der Whitlist die Elemente der folgenden Liste hinzufügen, um die Blockierung aller Anmeldeszenarien in Visual Studio aufzuheben:  
  
    - *.windows.net  
  
    - *.microsoftonline.com  
  
    - *.visualstudio.com  
  
    - *.microsoft.com  
  
    - *.live.com  
  
- Andernfalls können Sie entfernen die http://go.microsoft.com -Adresse aus der Whitelist, damit das Dialogfeld Proxy-Authentifizierung für beide angezeigt werden, wird die http://go.microsoft.com Adresse und den Serverendpunkten, wenn Visual Studio neu gestartet wird.  
  
- ODER  
  
- Wenn Sie die standardmäßigen Anmeldeinformationen mit Ihrem Proxy verwenden möchten, können Sie Folgendes tun:  
  
    1. Suchen Sie „devenv.exe.config“ (die devenv.exe-Konfigurationsdatei) in **%ProgramFiles%\Microsoft Visual Studio 14.0\Common7\IDE** (oder **%ProgramFiles(x86)%\Microsoft Visual Studio 14.0\Common7\IDE**).  
  
    2. Suchen Sie in der Konfigurationsdatei die `<system.net>` -Sperre und fügen Sie diesen Code hinzu:  
  
        ```xml  
        <defaultProxy enabled="true" useDefaultCredentials="true">  
            <proxy bypassonlocal="True" proxyaddress=" HYPERLINK "http://<yourproxy:port#" http://<yourproxy:port#>"/>  
        </defaultProxy>  
  
        ```  
  
         Sie müssen die korrekte Proxy-Adresse für Ihr Netzwerk in `proxyaddress="<http://<yourproxy:port#>`einfügen.  
  
- ODER  
  
- Alternativ können Sie die Anweisungen in [diesem Beitrag](http://blogs.msdn.com/b/rido/archive/2010/05/06/how-to-connect-to-tfs-through-authenticated-web-proxy.aspx) befolgen, um Code hinzuzufügen, mit dem Sie den Proxy verwenden können.

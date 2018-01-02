---
title: "Fehler „Proxyautorisierung erforderlich“ | Microsoft-Dokumentation"
ms.custom: 
ms.date: 09/22/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c2d24ae1-9902-460e-b72a-0299eed9ee82
caps.latest.revision: "4"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6544edb62bac07f5ab787e4a3b2f8abaebafa777
ms.sourcegitcommit: cc288456329aefca1fdaa7ce74751ce195985c14
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/17/2017
---
# <a name="proxy-authorization-required"></a>Proxyautorisierung erforderlich

Dieser Fehler tritt normalerweise auf, wenn Benutzer über einen Proxyserver mit dem Internet verbunden sind, und der Proxyserver die Aufrufe einiger Netzwerkressourcen blockiert, die von Visual Studio ausgeführt werden.

## <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler

- Starten Sie Visual Studio neu. Das Dialogfeld Proxy-Authentifizierung sollte angezeigt werden. Geben Sie Ihre Anmeldeinformationen in das Dialogfeld ein.

- Wenn durch die oben genannten Schritte das Problem nicht behoben wird, liegt dies möglicherweise daran, dass der Proxyserver Sie nicht zur Eingabe von Anmeldeinformationen für „http://go.microsoft.com“-Adressen, sondern für „*.visualStudio.com“-Adressen auffordert. Für diese Server müssen Sie eine Whitelist der folgenden URLs erstellen, um die Blockierung aller Anmeldeszenarios in Visual Studio aufzuheben:

    - *.windows.net

    - *.microsoftonline.com

    - *.visualstudio.com

    - *.microsoft.com

    - *.live.com

- Sie können die Adresse „http://go.microsoft.com“ andernfalls aus der Whitelist entfernen, damit das Dialogfeld „Proxy-Authentifizierung“ beim Neustart von Visual Studio sowohl für die Adresse „http://go.microsoft.com“ als auch die Serverendpunkte angezeigt wird.

    ODER

- Wenn Sie die standardmäßigen Anmeldeinformationen mit Ihrem Proxy verwenden möchten, können Sie Folgendes tun:

    1. Suchen Sie **devenv.exe.config** (die Konfigurationsdatei „devenv.exe“) in **%ProgramFiles%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE** oder **%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE**.

    1. Suchen Sie in der Konfigurationsdatei die `<system.net>` -Sperre und fügen Sie diesen Code hinzu:

        ```xml
        <defaultProxy enabled="true" useDefaultCredentials="true">
            <proxy bypassonlocal="True" proxyaddress=" HYPERLINK "http://<yourproxy:port#" http://<yourproxy:port#>"/>
        </defaultProxy>
        ```

        Sie müssen die korrekte Proxy-Adresse für Ihr Netzwerk in `proxyaddress="<http://<yourproxy:port#>`einfügen.

    ODER

- Alternativ können Sie die Anweisungen in [diesem Beitrag](http://blogs.msdn.com/b/rido/archive/2010/05/06/how-to-connect-to-tfs-through-authenticated-web-proxy.aspx) befolgen, um Code hinzuzufügen, mit dem Sie den Proxy verwenden können.

## <a name="see-also"></a>Siehe auch

[Internet resources used by Visual Studio (Von Visual Studio verwendete Internetressourcen)](../connected-environment.md)
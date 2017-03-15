---
title: "Proxyautorisierung erforderlich | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c2d24ae1-9902-460e-b72a-0299eed9ee82
caps.latest.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 4
---
# Proxyautorisierung erforderlich
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Dieser Fehler tritt normalerweise auf, wenn Benutzer in Visual Studio Online über einen Proxyserver verbunden sind, und der Proxy\-Server die Aufrufe blockiert. Visual Studio Online wird verwendet, um den Benutzer in der IDE angemeldet zu lassen.  
  
## So beheben Sie diesen Fehler  
  
-   Starten Sie Visual Studio neu. Das Dialogfeld Proxy\-Authentifizierung sollte angezeigt werden. Geben Sie Ihre Anmeldeinformationen in das Dialogfeld ein.  
  
-   Wenn durch die oben genannten Schritte das Problem nicht behoben wird, liegt dies möglicherweise daran, dass der Proxyserver Sie nicht zur Eingabe von Anmeldeinformationen für „http:\/\/go.microsoft.com“\-Adressen, sondern für „\*.visualStudio.com“\-Adressen auffordert. Für diese Server müssen Sie der Whitlist die Elemente der folgenden Liste hinzufügen, um die Blockierung aller Anmeldeszenarien in Visual Studio aufzuheben:  
  
    -   \*.windows.net  
  
    -   \*.microsoftonline.com  
  
    -   \*.visualstudio.com  
  
    -   \*.microsoft.com  
  
    -   \*.live.com  
  
-   Sie können die Adresse „http:\/\/go.microsoft.com“ andernfalls aus der Whitelist entfernen, damit das Dialogfeld „Proxy\-Authentifizierung“ beim Neustart von Visual Studio sowohl für die Adresse „http:\/\/go.microsoft.com“ als auch die Serverendpunkte angezeigt wird.  
  
-   ODER  
  
-   Wenn Sie die standardmäßigen Anmeldeinformationen mit Ihrem Proxy verwenden möchten, können Sie Folgendes tun:  
  
    1.  Suchen Sie „devenv.exe.config“ \(die devenv.exe\-Konfigurationsdatei\) in **%ProgramFiles%\\Microsoft Visual Studio 14.0\\Common7\\IDE** \(oder **%ProgramFiles\(x86\)%\\Microsoft Visual Studio 14.0\\Common7\\IDE**\).  
  
    2.  Suchen Sie in der Konfigurationsdatei die `<system.net>`\-Sperre und fügen Sie diesen Code hinzu:  
  
        ```xml  
        <defaultProxy enabled="true" useDefaultCredentials="true">  
            <proxy bypassonlocal="True" proxyaddress=" HYPERLINK "http://<yourproxy:port#" http://<yourproxy:port#>"/>  
        </defaultProxy>  
  
        ```  
  
         Sie müssen die korrekte Proxy\-Adresse für Ihr Netzwerk in `proxyaddress="<http://<yourproxy:port#>` einfügen.  
  
-   ODER  
  
-   Alternativ können Sie die Anweisungen in [diesem Beitrag](http://blogs.msdn.com/b/rido/archive/2010/05/06/how-to-connect-to-tfs-through-authenticated-web-proxy.aspx) befolgen, um Code hinzuzufügen, mit dem Sie den Proxy verwenden können.
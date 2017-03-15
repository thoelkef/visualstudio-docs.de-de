---
title: "Befehl &quot;ShowWebBrowser&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "view.showwebbrowser"
helpviewer_keywords: 
  - "ShowWebBrowser-Befehl"
  - "View.ShowWebBrowser-Befehl"
ms.assetid: c6a4fbd6-8e9d-45cc-8b2f-93990d065e78
caps.latest.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# Befehl &quot;ShowWebBrowser&quot;
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Zeigt die in einem Webbrowserfenster angegebene URL entweder in der integrierten Entwicklungsumgebung \(IDE\) oder außerhalb der IDE an.  
  
## Syntax  
  
```  
View.ShowWebBrowser URL [/new][/ext]  
```  
  
## Argumente  
 `URL`  
 Erforderlich.  Die URL \(Uniform Resource Locator\) für die Website.  
  
## Schalter  
 \/new  
 Optional.  Gibt an, dass die Seite in einer neuen Instanz des Webbrowsers angezeigt werden soll.  
  
 \/ext  
 Optional.  Gibt an, dass die Seite im Standardwebbrowser außerhalb der IDE angezeigt werden soll.  
  
## Hinweise  
 Der Alias für den **ShowWebBrowser**\-Befehl lautet **navigate** oder **nav**.  
  
## Beispiel  
 Das folgende Beispiel zeigt die MSDN Online\-Homepage in einem Webbrowser außerhalb der IDE an.  Wenn eine Instanz des Webbrowsers bereits geöffnet ist, wird diese verwendet; andernfalls wird eine neue Instanz geöffnet.  
  
```  
>View.ShowWebBrowser http://msdn.microsoft.com /ext  
```  
  
## Siehe auch  
 [Visual Studio\-Befehle](../../ide/reference/visual-studio-commands.md)   
 [Befehlsfenster](../../ide/reference/command-window.md)   
 [Such\/Befehlsfeld](../../ide/find-command-box.md)   
 [Visual Studio\-Befehlsaliase](../../ide/reference/visual-studio-command-aliases.md)
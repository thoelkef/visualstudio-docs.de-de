---
title: "Websteuerelementbibliothek (verwalteter Code) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Debuggen [Visual Studio], Websteuerelementbibliotheken"
  - "Debuggen von DLLs"
ms.assetid: 2413883f-9e88-406d-b874-0ed743b75d40
caps.latest.revision: 26
caps.handback.revision: 26
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Websteuerelementbibliothek (verwalteter Code)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Durch die Projektvorlage für eine Websteuerelementbibliothek wird eine DLL erstellt.  Da es sich bei der Klassenbibliothek um eine DLL handelt, kann sie nicht direkt ausgeführt werden.  Erstellen Sie eine [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]\-Seite erstellen, in die das Steuerelement eingebettet ist.  Weitere Informationen hierzu finden Sie unter [Web Control Library Template](http://msdn.microsoft.com/de-de/00666b07-71d2-4ace-a13c-cc130a3ce372).  
  
### So debuggen Sie eine Websteuerelementbibliothek \(Methode 1\)  
  
1.  Öffnen Sie ein vorhandenes Websteuerelementbibliothek\-Projekt, oder erstellen Sie ein neues.  
  
2.  Erstellen Sie eine [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]\-Seite, in die das Steuerelement eingebettet ist.  
  
3.  Erstellen Sie in der Website, die die [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]\-Testumgebung hostet, ein Unterverzeichnis mit dem Namen `/Code`.  
  
4.  Kopieren Sie den Quellcode für das Steuerelement in das `/Code`\-Unterverzeichnis.  
  
5.  Öffnen Sie den Quellcode im `/Code`\-Unterverzeichnis, und legen Sie Haltepunkte fest.  
  
6.  Öffnen Sie ein Browserfenster, und geben Sie die URL ein, der auf die Testumgebung zeigt.  Sobald ein Haltepunkt im Steuerelement erreicht ist, können Sie mit dem Debuggen beginnen.  
  
### So debuggen Sie eine Websteuerelementbibliothek \(Methode 2\)  
  
1.  Erstellen Sie ein Hostanwendungsprojekt und ein Websteuerelementprojekt in der gleichen Projektmappe.  
  
2.  Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf die Hostanwendung, und wählen Sie **Verweis hinzufügen** aus.  
  
3.  Fügen Sie dem Websteuerelementprojekt einen Verweis hinzu.  
  
## Siehe auch  
 [ASP.NET\-Webanwendungen](../debugger/debugging-preparation-aspnet-web-applications.md)
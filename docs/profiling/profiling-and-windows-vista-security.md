---
title: "Profilerstellung und Sicherheit in Windows&#160;Vista | Microsoft Docs"
ms.custom: ""
ms.date: "12/08/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Profilerstellungstools, Sicherheit"
  - "Leistungstools, Sicherheit"
ms.assetid: 842112fc-b886-4801-8cd7-a25b314b0393
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Profilerstellung und Sicherheit in Windows&#160;Vista
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Abhängig von den Benutzerzugriffsberechtigungen, die vom Computeradministrator in den [!INCLUDE[wiprlhext](../debugger/includes/wiprlhext_md.md)]\-Einstellungen festgelegt wurden, kann ein einzelner Benutzer über die Sicherheitsberechtigung zum Erstellen eines Prozessprofils auf diesem Computer verfügen.  In den folgenden Beispielen werden mögliche Unterschiede zwischen Benutzern veranschaulicht:  
  
-   Einige Benutzer können u. U. auf erweiterte Profilerstellungsfeatures zugreifen, wenn der Administrator festgelegt hat, dass Treiber und Dienst gestartet werden.  
  
-   Domänenbenutzer können u. U. ausschließlich auf die Sampling\-Profilerstellung zugreifen.  
  
-   Einige Benutzer können allen anderen Benutzern möglicherweise den Zugriff auf die Profilerstellung verweigern.  
  
 Weitere Informationen finden Sie in den ADMIN\-Optionen unter [VSPerfCmd](../profiling/vsperfcmd.md).  
  
## Sitzungsübergreifende Profilerstellung  
 *Sitzungsübergreifende Profilerstellung* ist die Fähigkeit, ein Profil für einen Prozess zu erstellen, der in einer anderen Anmeldesitzung ausgeführt wird.  Die meisten Dienste werden in Sitzung 0 ausgeführt, und für Benutzer ist keine direkte Ausführung in Sitzung 0 möglich.  Mit der Schaltfläche **An den Prozess anhängen** in der Symbolleiste des Leistungs\-Explorers oder der \/attach\-Option des VSPerfCmd\-Befehlszeilentools können Sie für die meisten Prozesse in unterschiedlichen Anmeldesitzungen ein Profil erstellen.  
  
 Um eine Liste der verfügbaren Prozesse anzuzeigen, legen Sie die Sichtbarkeitsoptionen für die prozessübergreifende Profilerstellung fest.  Diese Optionen sind im Fenster **An den Prozess anhängen** verfügbar, das angezeigt wird, wenn Sie auf **An den Prozess anhängen** klicken:  
  
-   **Prozesse aller Benutzer anzeigen**  
  
     Wenn diese Option nicht aktiviert wird, werden in der Liste nur die Prozesse aufgelistet, die sich im Besitz des aktuellen Benutzers befinden.  Wenn **Prozesse aller Benutzer anzeigen** aktiviert ist, werden in der Liste Prozesse von allen Benutzern angezeigt.  
  
-   **Prozesse in allen Sitzungen anzeigen**  
  
     Wenn diese Option nicht aktiviert wird, werden in der Liste Prozesse in der aktuellen Sitzung aufgelistet.  Wenn diese Option aktiviert wird, werden in der Liste Prozesse in sämtlichen Sitzungen aufgelistet.  
  
## Siehe auch  
 [Übersichten](../profiling/overviews-performance-tools.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [How to: Attach to a Running Process](http://msdn.microsoft.com/de-de/636d0a52-4bfd-48d2-89ad-d7b9ca4dc4f4)
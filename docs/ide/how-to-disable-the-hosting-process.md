---
title: "Gewusst wie: Deaktivieren des Hostprozesses | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Hostingprozess, Deaktivieren"
  - "vshost.exe, Deaktivieren des Hostingprozesses"
ms.assetid: 9157488d-737f-454b-8d8d-36f99de38bb0
caps.latest.revision: 10
caps.handback.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Gewusst wie: Deaktivieren des Hostprozesses
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Aufrufe an bestimmte APIs können beeinflusst werden, wenn der Hostprozesses aktiviert wird.  In diesen Fällen ist es erforderlich, den Hostprozess zu deaktivieren, damit korrekte Ergebnisse zurückgegeben werden.  
  
### So deaktivieren Sie den Hostprozess  
  
1.  Öffnen Sie ein ausführbares Projekt in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Projekte, die keine ausführbare Dateien erzeugen \(z. B. Klassenbibliothek\- oder Dienstprojekte\) verfügen über diese Option nicht.  
  
2.  Klicken Sie im Menü **Projekt** auf **Eigenschaften**.  
  
3.  Klicken Sie auf die Registerkarte **Debuggen**.  
  
4.  Deaktivieren Sie das Kontrollkästchen **Visual Studio\-Hostprozess aktivieren**.  
  
 Wenn der Hostprozess deaktiviert ist, sind mehrere Debugfeatures nicht verfügbar oder weisen eine eingeschränkte Leistung auf.  Weitere Informationen finden Sie unter [Debuggen und der Hostprozess](../debugger/debugging-and-the-hosting-process.md).  
  
 Generelle Einschränkungen bei deaktiviertem Hostprozess:  
  
-   Die Vorlaufzeit bis zum Start des Debugvorgangs bei [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]\-Anwendungen verlängert sich.  
  
-   Die Ausdrucksauswertung zur Entwurfszeit ist nicht verfügbar.  
  
-   Das Debuggen teilweise vertrauenswürdiger Anwendungen ist nicht möglich.  
  
## Siehe auch  
 [Debuggen und der Hostprozess](../debugger/debugging-and-the-hosting-process.md)   
 [Hostprozess \(vshost.exe\)](../ide/hosting-process-vshost-exe.md)   
 [Builds During Application Development](http://msdn.microsoft.com/de-de/c9497d62-3b7b-4449-88e8-cf27acc9efe6)
---
title: "The following components could not be browsed: | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS_E_CANNOTBROWSECOM"
  - "VS.Message.0x00006A6D"
  - "VS_E_LOADTYPELIBFAILED"
  - "VS_E_INVALIDCOMCOMPONENT"
  - "VS_E_UNRECOGNIZEDCOMPONENT"
  - "VS.Message.0x00006A6E"
  - "VS.Message.ObjectBrowserErrors"
  - "vs.Message.0x00005AC3"
  - "VS.Message.0x00005AC4"
  - "VS.Message.0x00005AC5"
  - "VS_E_REGFAILEDCOMCOMPONENT"
ms.assetid: 83b03767-eecb-47a4-8029-166308c7dded
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# The following components could not be browsed:
Dieses Meldungsfeld dient zur Anzeige verschiedener Fehler, die sich auf den Objektkatalog und das Dialogfeld Komponentenauswahl beziehen.  Die folgenden Fehler treten am häufigsten auf.  
  
## Komponente oder Dateityp kann nicht im Objektkatalog angezeigt werden.  
 Dieser Fehler tritt normalerweise auf, wenn Sie einen ungültigen oder nicht vorhandenen Datei\- oder Pfadnamen angegeben haben oder eine Datei nicht mit dem Objektkatalog gefunden werden kann.  
  
#### So beheben Sie diesen Fehler  
  
-   Überprüfen Sie, dass für den angegebenen Dateinamen eine entsprechende Komponente \(.NET\-Assembly, COM\-Typbibliothek oder Quellcode\-Browser\-Datei\) vorhanden ist und durchsucht werden kann.  
  
## Die Datei ist keine gültige .NET\-Framework\- oder COM\-Komponente.  
 Dieser Fehler tritt normalerweise auf, wenn die angegebene Komponente weder eine .NET Framework\-Assembly noch eine COM\-Typbibliothek darstellt.  
  
#### So beheben Sie diesen Fehler  
  
-   Wählen Sie eine andere Komponente aus, die durchsucht werden soll.  
  
## Keine Registrierung der Datei als COM\-Komponente möglich.  
 Dieser Fehler tritt normalerweise auf, wenn die Typbibliothek für eine COM\-Komponente nicht registriert werden kann.  Die Typbibliothek ist eventuell nicht vorhanden oder fehlerhaft.  
  
#### So beheben Sie diesen Fehler  
  
-   Installieren Sie die Komponente neu, und führen Sie den Vorgang erneut aus.  
  
## Es ist keine entsprechende Typbibliothek registriert, oder die registrierten Informationen sind ungültig.  
 Die angegebene Typbibliothek ist nicht mehr vorhanden oder enthält ungültige Daten.  
  
#### So beheben Sie diesen Fehler  
  
-   Überprüfen Sie, dass die Typbibliothek vorhanden und korrekt registriert worden ist.  
  
## Die zum Durchsuchen der COM\-Typbibliothek notwendigen Komponenten sind nicht vorhanden oder nicht richtig registriert.  
 Die Datei vstlbinf.dll ist nicht vorhanden oder nicht korrekt registriert.  
  
#### Problembehandlung  
  
1.  Suchen Sie auf dem Computer nach vstlbinf.dll, und registrieren Sie die Datei unter Verwendung der Datei regsvr32.exe.  
  
     \- oder \-  
  
2.  Wenn die Datei vstlbinf.dll nicht auf dem Computer vorhanden ist, installieren Sie dieses Produkt erneut.  
  
## Siehe auch  
 [Object Browser](http://msdn.microsoft.com/de-de/f89acfc5-1152-413d-9f56-3dc16e3f0470)   
 [Edit Custom Component Set Dialog Box](http://msdn.microsoft.com/de-de/dc995bd7-afbf-4389-ba1c-f377b677ded7)
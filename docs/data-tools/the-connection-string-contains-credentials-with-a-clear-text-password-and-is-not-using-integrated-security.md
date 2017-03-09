---
title: "Die Verbindungszeichenfolge enth&#228;lt Anmeldeinformationen mit einem Kennwort in Klartext und ohne integrierte Sicherheit | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 501d85af-92e0-4471-b280-8a59c0688575
caps.latest.revision: 3
caps.handback.revision: 1
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Die Verbindungszeichenfolge enth&#228;lt Anmeldeinformationen mit einem Kennwort in Klartext und ohne integrierte Sicherheit
Möchten Sie die Verbindungszeichenfolge mit vertraulichen Informationen in der aktuellen DBML\-Datei und in den Anwendungskonfigurationsdateien speichern?Klicken Sie auf Nein, um die Verbindungszeichenfolge ohne die vertraulichen Informationen zu speichern.  
  
 Beim Arbeiten mit Datenverbindungen, die vertrauliche Informationen enthalten \(in der Verbindungszeichenfolge enthaltene Kennwörter\) haben Sie die Option, die Verbindungszeichenfolge mit den vertraulichen Informationen oder ohne diese in der DBML\-Datei und der Anwendungskonfigurationsdatei des Projekts zu speichern.  
  
> [!WARNING]
>  Wenn Sie die Eigenschaften **Verbindung** und **Anwendungseinstellungen** auf **False** festlegen, wird das Kennwort der DBML\-Datei hinzugefügt.  
  
### So speichern Sie die Verbindungszeichenfolge mit den vertraulichen Informationen in den Anwendungseigenschaften des Projekts  
  
-   Klicken Sie auf **Ja**.  
  
     Die Verbindungszeichenfolge wird als Anwendungseinstellung gespeichert.Die Verbindungszeichenfolge enthält die vertraulichen Informationen als Klartext.Die vertraulichen Informationen sind nicht in der DBML\-Datei enthalten.  
  
### So speichern Sie die Verbindungszeichenfolge ohne die vertraulichen Informationen in den Anwendungseigenschaften des Projekts  
  
-   Klicken Sie auf **Nein**.  
  
     Die Verbindungszeichenfolge wird als Anwendungseinstellung gespeichert, jedoch ohne das Kennwort.  
  
## Siehe auch  
 [Object Relational Designer \(O\/R\-Designer\)](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Herstellen von Datenverbindungen in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)
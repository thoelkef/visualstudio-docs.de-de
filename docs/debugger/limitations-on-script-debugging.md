---
title: "Einschr&#228;nkungen beim Skriptdebugging | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
  - "ASPX-Haltepunktzuordnung, Einschränkungen"
  - "Haltepunktzuordnung, Einschränkungen"
  - "Skriptdebuggen, Einschränkungen"
ms.assetid: 280eead5-693c-47af-967f-dfe9d23f84db
caps.latest.revision: 22
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 22
---
# Einschr&#228;nkungen beim Skriptdebugging
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] unterstützt das Debuggen von clientseitigem Skript. Dabei gelten die in diesem Thema erörterten Einschränkungen.  
  
## Einschränkungen beim Zuordnen von Haltepunkten mit clientseitigem Skript  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ermöglicht es Ihnen, einen Haltepunkt in einer serverseitigen ASPX\- oder HTML\-Datei festzulegen, die zur Laufzeit in eine clientseitige Datei transformiert wird.  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ordnet den Haltepunkt aus der serverseitigen Datei einem entsprechenden Haltepunkt in der clientseitigen Datei zu. Dies unterliegt den folgenden Einschränkungen:  
  
-   Haltepunkte müssen innerhalb von `<script>`\-Blöcken festgelegt werden.  Haltepunkte in eingebetteten Skripts oder `<% %>`\-Blöcken können nicht zugeordnet werden.  
  
-   Die Browser\-URL für die Seite muss den Seitennamen enthalten.  Beispiel: http:\/\/microsoft.com\/default.apsx.  Bei der Zuordnung von Haltepunkten wird die Umleitung von einer Adresse wie http:\/\/microsoft.com zur Standardseite nicht erkannt.  
  
-   Der Haltepunkt muss in der Seite festgelegt werden, die in der Browser\-URL angegeben ist, und nicht in einer ASPX\-Steuerelementdatei \(ascx\), Masterseite oder einer anderen auf dieser Seite enthaltenen Datei.  Haltepunkte in eingeschlossenen Seiten können nicht zugeordnet werden.  
  
-   Haltepunkte in `<script defer=true>`\-Blöcken können nicht zugeordnet werden.  
  
-   Bei Haltepunkten in `<script id="">`\-Blöcken wird das `id`\-Attribut bei der Zuordnung von Haltepunkten ignoriert.  
  
## Zuordnung von Haltepunkten und doppelte Zeilen  
 Um die entsprechende Stelle in serverseitigen und clientseitigen Skripts zu finden, wird der Code durch den Algorithmus für die Zuordnung von Haltepunkten zeilenweise überprüft.  Beim Algorithmus wird davon ausgegangen, dass jede Zeile einmal vorkommt.  Wenn mindestens zwei Zeilen denselben Code enthalten und Sie einen Haltepunkt für eine dieser doppelten Zeilen festlegen, wird vom Algorithmus für die Zuordnung von Haltepunkten möglicherweise die falsche Entsprechung in der clientseitigen Datei ausgewählt.  Um das zu verhindern, fügen Sie der Zeile mit dem festgelegten Haltepunkt einen Kommentar hinzu.  Beispiel:  
  
```  
i++ ;  
i ++; // I added a comment, so this line is now unique  
i ++;  
```
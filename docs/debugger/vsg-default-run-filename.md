---
title: "VSG_DEFAULT_RUN_FILENAME | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ea549d2f-c857-458c-93c7-bc5a2d11d15d
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# VSG_DEFAULT_RUN_FILENAME
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Definiert den Standarddateinamen der Grafikprotokolldatei.  
  
## Syntax  
  
```cpp  
#define VSG_DEFAULT_FILENAME filename  
```  
  
#### Parameter  
 `filename`  
 Der Dateiname, der der Grafikprotokolldatei standardmäßig zugewiesen wird, wenn Grafikinformationen programmgesteuert erfasst werden.  
  
## Wert  
 Ein Zeichenfolgenliteral, das den Dateinamen der Grafikprotokolldatei darstellt.  Standardmäßig ist dies L"default.vsglog".  
  
```cpp  
#define VSG_DEFAULT_FILENAME L"default.vsglog"  
```  
  
## Hinweise  
 Wenn das Präprozessorsymbol `DONT_SAVE_VSGLOG_TO_TEMP` definiert ist, ist der Dateiname relativ zum aktuellen Verzeichnis der aufgezeichneten App oder ein absoluter Pfad. Andernfalls ist er relativ zum Verzeichnis der temporären Dateien des Benutzers und kann kein absoluter Pfad sein.  
  
 Um den definierten Dateinamen zu ändern, müssen Sie ihn erneut definieren, bevor Sie `vsgcapture.h` in Ihr Programm einschließen.  
  
## Beispiel  
 Dieses Beispiel zeigt, wie der Standarddateiname der Erfassungsdatei geändert wird:  
  
```cpp  
// Redefine the default capture filename before including vsgcapture.h  
#define VSG_DEFAULT_FILENAME L"capture.vsglog"  
  
#include <vsgcapture.h>  
```  
  
## Siehe auch  
 [DONT\_SAVE\_VSGLOG\_TO\_TEMP](../debugger/dont-save-vsglog-to-temp.md)
---
title: "VsgDbg::VsgDbg (Konstruktor) | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 670651e6-5e79-4845-b0c2-671beb7055a8
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# VsgDbg::VsgDbg (Konstruktor)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Erstellt eine Instanz der `VsgDbg`\-Klasse mit oder ohne das Vorbereiten einer In\-App\-Komponente der Grafikdiagnose, um Grafikinformationen standardmäßig aktiv zu erfassen und aufzuzeichnen, basierend auf dem angegebenen booleschen Parameter.  
  
## Syntax  
  
```cpp  
VsgDbg(  
  bDefaultInit  
);  
```  
  
#### Parameter  
 `bDefaultInit`  
 `true`, um anzugeben, dass die In\-App\-Komponente der Grafikdiagnose vorbereitet werden muss, um aktiv Grafikinformationen zu erfassen und aufzuzeichnen; `false`, um anzugeben, dass die In\-App\-Komponente der Grafikdiagnose nicht vorbereitet werden soll, um zu diesem Zeitpunkt aktiv Grafikinformationen zu erfassen und aufzuzeichnen.  
  
## Hinweise  
 Wenn der Konstruktor mit `bDefaultInit` auf `true` festgelegt aufgerufen wird, wird der Dateiname der Grafikprotokolldatei dadurch bestimmt, wie die Präprozessorsymbole `DONT_SAVE_VSGLOG_TO_TEMP` und `VSG_DEFAULT_RUN_FILENAME` definiert sind, bevor `vsgcapture.h` in die App eingeschlossen wird.  
  
 Wenn der Konstruktor mit `bDefaultInit` festgelegt auf `false` aufgerufen wird, kann die In\-App\-Komponente der Grafikdiagnose vorbereitet werden, um Grafikinformationen zu einem späteren Zeitpunkt aktiv zu erfassen und aufzuzeichnen, indem die `Init`\-Funktion aufgerufen wird.  
  
## Siehe auch  
 [VsgDbg::~VsgDbg \(Destruktor\)](../debugger/vsgdbg-tilde-vsgdbg-destructor.md)   
 [Init](../debugger/init.md)   
 [DONT\_SAVE\_VSGLOG\_TO\_TEMP](../debugger/dont-save-vsglog-to-temp.md)   
 [VSG\_DEFAULT\_RUN\_FILENAME](../debugger/vsg-default-run-filename.md)
---
title: 'Vsgdbg:: Vsgdbg (Konstruktor) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 670651e6-5e79-4845-b0c2-671beb7055a8
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f2a35443dbf4fc413908c61e989d2138122c0991
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47514968"
---
# <a name="vsgdbgvsgdbg-constructor"></a>VsgDbg::VsgDbg (Konstruktor)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [vsgdbg:: Vsgdbg (Konstruktor)](https://docs.microsoft.com/visualstudio/debugger/graphics/vsgdbg-vsgdbg-constructor).  
  
Erstellt eine Instanz der `VsgDbg`-Klasse mit oder ohne das Vorbereiten einer In-App-Komponente der Grafikdiagnose, um Grafikinformationen standardmäßig aktiv zu erfassen und aufzuzeichnen, basierend auf dem angegebenen booleschen Parameter.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
VsgDbg(  
  bDefaultInit  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `bDefaultInit`  
 `true`, um anzugeben, dass die In-App-Komponente der Grafikdiagnose vorbereitet werden muss, um aktiv Grafikinformationen zu erfassen und aufzuzeichnen; `false`, um anzugeben, dass die In-App-Komponente der Grafikdiagnose nicht vorbereitet werden soll, um zu diesem Zeitpunkt aktiv Grafikinformationen zu erfassen und aufzuzeichnen.  
  
## <a name="remarks"></a>Hinweise  
 Wenn der Konstruktor aufgerufen wird, mit `bDefaultInit` festgelegt `true`, richtet sich der Dateiname der grafikprotokolldatei an, wie die `DONT_SAVE_VSGLOG_TO_TEMP` und `VSG_DEFAULT_RUN_FILENAME` Präprozessorsymbole definiert sind, bevor `vsgcapture.h` befindet sich in Ihrer app.  
  
 Wenn der Konstruktor mit `bDefaultInit` festgelegt auf `false` aufgerufen wird, kann die In-App-Komponente der Grafikdiagnose vorbereitet werden, um Grafikinformationen zu einem späteren Zeitpunkt aktiv zu erfassen und aufzuzeichnen, indem die `Init`-Funktion aufgerufen wird.  
  
## <a name="see-also"></a>Siehe auch  
 [VsgDbg:: ~ VsgDbg (Destruktor)](../debugger/vsgdbg-tilde-vsgdbg-destructor.md)   
 [Init](../debugger/init.md)   
 [DONT_SAVE_VSGLOG_TO_TEMP](../debugger/dont-save-vsglog-to-temp.md)   
 [VSG_DEFAULT_RUN_FILENAME](../debugger/vsg-default-run-filename.md)




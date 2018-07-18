---
title: 'Vsgdbg:: Vsgdbg (Konstruktor) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 670651e6-5e79-4845-b0c2-671beb7055a8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 04f33b117a7ee47fb0c11932c3722f6f2a4a3541
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
ms.locfileid: "31473302"
---
# <a name="vsgdbgvsgdbg-constructor"></a>VsgDbg::VsgDbg (Konstruktor)
Erstellt eine Instanz der `VsgDbg`-Klasse mit oder ohne das Vorbereiten einer In-App-Komponente der Grafikdiagnose, um Grafikinformationen standardmäßig aktiv zu erfassen und aufzuzeichnen, basierend auf dem angegebenen booleschen Parameter.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
VsgDbg(  
  bDefaultInit  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `bDefaultInit`  
 `true`, um anzugeben, dass die In-App-Komponente der Grafikdiagnose vorbereitet werden muss, um aktiv Grafikinformationen zu erfassen und aufzuzeichnen; `false`, um anzugeben, dass die In-App-Komponente der Grafikdiagnose nicht vorbereitet werden soll, um zu diesem Zeitpunkt aktiv Grafikinformationen zu erfassen und aufzuzeichnen.  
  
## <a name="remarks"></a>Hinweise  
 Wenn der Konstruktor aufgerufen wird, mit `bDefaultInit` festgelegt `true`, der Dateiname der grafikprotokolldatei wird bestimmt, wie die `DONT_SAVE_VSGLOG_TO_TEMP` und `VSG_DEFAULT_RUN_FILENAME` Präprozessorsymbole definiert sind, bevor `vsgcapture.h` in Ihrer app enthalten ist.  
  
 Wenn der Konstruktor mit `bDefaultInit` festgelegt auf `false` aufgerufen wird, kann die In-App-Komponente der Grafikdiagnose vorbereitet werden, um Grafikinformationen zu einem späteren Zeitpunkt aktiv zu erfassen und aufzuzeichnen, indem die `Init`-Funktion aufgerufen wird.  
  
## <a name="see-also"></a>Siehe auch  
 [VsgDbg:: ~ VsgDbg (Destruktor)](vsgdbg-tilde-vsgdbg-destructor.md)   
 [Init](init.md)   
 [DONT_SAVE_VSGLOG_TO_TEMP](dont-save-vsglog-to-temp.md)   
 [VSG_DEFAULT_RUN_FILENAME](vsg-default-run-filename.md)
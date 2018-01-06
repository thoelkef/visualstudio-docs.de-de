---
title: Kopieren (programmgesteuerte Aufzeichnung) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 30ec235a-0abb-44b9-8852-61bc9e67ce22
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 7f8fce1893363ac6df0e6d22320f718833a1114e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="copy-programmatic-capture"></a>Kopieren (Programmgesteuerte Aufzeichnung)
Kopiert den Inhalt der aktiven Grafikprotokolldatei (VSGLOG) in eine neue Datei.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
void Copy(  
  wchar_t const * szNewVSGLog  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `szNewVSGLog`  
 Der Dateiname der neuen Grafikprotokolldatei.  
  
## <a name="remarks"></a>Hinweise  
 Um die Grafikinformationen in eine neuen Datei zu kopieren, müssen Sie bereits einige Grafikinformationen erfasst haben, andernfalls geschieht nichts.
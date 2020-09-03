---
title: Kopieren (programmgesteuerte Aufzeichnung) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 30ec235a-0abb-44b9-8852-61bc9e67ce22
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fa79ffc2081ba92b905838658fe6aa758a675192
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68161510"
---
# <a name="copy-programmatic-capture"></a>Kopieren (Programmgesteuerte Aufzeichnung)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kopiert den Inhalt der aktiven Grafikprotokolldatei (VSGLOG) in eine neue Datei.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
void Copy(  
  wchar_t const * szNewVSGLog  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `szNewVSGLog`  
 Der Dateiname der neuen Grafikprotokolldatei.  
  
## <a name="remarks"></a>Hinweise  
 Um die Grafikinformationen in eine neuen Datei zu kopieren, müssen Sie bereits einige Grafikinformationen erfasst haben, andernfalls geschieht nichts.

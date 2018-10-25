---
title: 'Idiaenumframedata:: Skip | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData::Skip method
ms.assetid: 67140b4c-7125-4895-932d-42412326da29
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0079e4a1631693d4bfd55112043b407d6ecb781a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49863671"
---
# <a name="idiaenumframedataskip"></a>IDiaEnumFrameData::Skip
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Überspringt eine angegebene Anzahl von Frames von Datenelementen in einer Enumerationsfolge.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT Skip (   
   ULONG celt  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 celt  
 [in] Die Anzahl der Frames-Datenelemente in der Enumerationsfolge übersprungen.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` es sind keine weitere Datensätze zu überspringen.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)




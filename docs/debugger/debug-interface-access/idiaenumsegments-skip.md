---
title: 'Idiaenumsegments:: Skip | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaEnumSegments::Skip method
ms.assetid: ec67039f-da8c-4e70-8db7-957d7d5281e8
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 72f327dc469eef73e560df6da83ce65c038cff0c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="idiaenumsegmentsskip"></a>IDiaEnumSegments::Skip
Überspringt eine angegebene Anzahl von Segmenten in einem Enumerationsfolge an.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT Skip (   
   ULONG celt  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 celt  
 [in] Die Anzahl der Segmente in der Enumeration Sequenz zu überspringen.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls gibt `S_FALSE` Wenn es keine weiteren Segmente mehr sind für überspringen.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)
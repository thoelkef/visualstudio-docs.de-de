---
title: 'Idiaenumsegments:: Clone | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaEnumSegments::Clone method
ms.assetid: 93deaac6-72ab-4408-ba14-66174a618757
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 868921194036b9c5c5162e759e750bed7f6a0882
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="idiaenumsegmentsclone"></a>IDiaEnumSegments::Clone
Erstellt einen Enumerator, der den gleichen Enumeration Status als der aktuelle Enumerator enthält.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT Clone (   
   IDiaEnumSegments** ppenum  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 ppenum  
 [out] Gibt eine [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md) Objekt, das ein Duplikat des Enumerators enthält. Die Segmente werden nicht dupliziert werden, nur den Enumerator.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)
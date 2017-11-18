---
title: IDiaStackWalkHelper::pdataForVA | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaStackWalkHelper2::pdataByVA method
ms.assetid: fafc38fe-74dc-4726-9a51-eebf3a673d7f
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4925a4a37395dd53fabb1d8d7ba7f80bc5cc6c93
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="idiastackwalkhelperpdataforva"></a>IDiaStackWalkHelper::pdataForVA
Gibt zurück, der PDATA-Datenblock, die der virtuellen Adresse zugeordnet.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT pdataForVA(   
   ULONGLONG  va,  
   DWORD      cbData,  
   DWORD*     pcbData,  
   BYTE*      pbData  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `va`  
 [in] Gibt die virtuelle Adresse der Daten zu erhalten.  
  
 `cbData`  
 [in] Die Größe der Daten in Bytes zu erhalten.  
  
 `pcbData`  
 [out] Gibt die tatsächliche Größe der Daten in Byte, das abgerufen wurde.  
  
 `pbData`  
 [in, out] Ein Puffer, der mit der angeforderten Daten ausgefüllt ist. Nicht mit `NULL`.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`. Gibt `S_FALSE` Wenn keine PDATA für die angegebene Adresse vorhanden ist. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 PDATA (im Abschnitt mit dem Namen ".pdata") eine Kompiliereinheit enthält Informationen zur Ausnahmebehandlung für Funktionen.  
  
 Der Aufrufer weiß, wie viele Daten zurückgegeben werden, damit der Aufrufer nicht erforderlich verfügt, um Unterstützung bitten für wie viele Daten zur Verfügung steht. Daher ist es zulässig, eine Implementierung dieser Methode einen Fehler wird zurückgegeben, wenn die `pbData` Parameter ist `NULL`.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
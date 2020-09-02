---
title: 'IDiaStackFrame:: get_rawLVarInstanceValue | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_rawLVarInstanceValue method
ms.assetid: ce526259-85a6-475b-9274-0b3a21d95db2
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c8ff78c38ad077084b3dea9c96e3251ffddb2206
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62573013"
---
# <a name="idiastackframeget_rawlvarinstancevalue"></a>IDiaStackFrame::get_rawLVarInstanceValue
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Diese Methode ruft den Wert der angegebenen lokalen Variablen als Rohdaten Bytes ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT get_rawLVarInstanceValue(  
   IDiaLVarInstance* pInstance,  
   DWORD             cbDataMax,  
   DWORD*            pcbData,  
   BYTE*             pbData  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pInstance`  
 in Ein- `IDiaLVarInstance` Objekt, das eine Instanz der lokalen Variablen darstellt, für die der Wert zu erhalten ist.  
  
 `cbDataMax`  
 in Maximale Anzahl von Bytes im Puffer, auf die von verwiesen wird `pbData` . Dies kann ein Maximum von 8 Bytes ( `sizeof(ULONGLONG)` ) sein.  
  
 `pcbData`  
 vorgenommen Gibt die tatsächliche Anzahl von Bytes zurück, die im Puffer gespeichert werden.  
  
 `pbData`  
 vorgenommen Ein Puffer, der mit Daten aufgefüllt werden soll. Dieser darf nicht `NULL` sein.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)

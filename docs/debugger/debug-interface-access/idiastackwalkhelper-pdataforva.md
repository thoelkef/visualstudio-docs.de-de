---
title: IDiaStackWalkHelper::pdataForVA | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::pdataByVA method
ms.assetid: fafc38fe-74dc-4726-9a51-eebf3a673d7f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 42ab689c5c94fcf0200775d9fdd59ac2a0f7202c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54916976"
---
# <a name="idiastackwalkhelperpdataforva"></a>IDiaStackWalkHelper::pdataForVA
Gibt zurück, der PDATA-Datenblock, der der virtuellen Adresse zugeordnet.  
  
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
 [in] Gibt an, die virtuelle Adresse der Daten zu erhalten.  
  
 `cbData`  
 [in] Die Größe der Daten in Bytes abgerufen.  
  
 `pcbData`  
 [out] Gibt die tatsächliche Größe der Daten in Byte, das abgerufen wurde.  
  
 `pbData`  
 [in, out] Ein Puffer, der mit der angeforderten Daten gefüllt wird. Darf nicht `NULL` sein.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt bei Erfolg `S_OK` zurück. Gibt `S_FALSE` liegt keine PDATA für die angegebene Adresse. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Der pdata-Abschnitt (Abschnitt mit dem Namen ".pdata-Datensatz") eine Kompiliereinheit enthält Informationen über Ausnahmebehandlung für Funktionen.  
  
 Der Aufrufer weiß, wie viele Daten befinden, zurückgegeben werden, damit der Aufrufer nicht erforderlich verfügt, stellen Sie für wie viele Daten zur Verfügung steht. Daher ist es für eine Implementierung dieser Methode einen Fehler zurückgegeben, wenn die `pbData` Parameter `NULL`.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
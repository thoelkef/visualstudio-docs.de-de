---
title: IDiaStackWalkHelper::pdataForVA | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::pdataByVA method
ms.assetid: fafc38fe-74dc-4726-9a51-eebf3a673d7f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ec11596091f7039d9f711acc0d96510340a77c6c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49901423"
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
 [in, out] Ein Puffer, der mit der angeforderten Daten gefüllt wird. Nicht möglich, `NULL`.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`. Gibt `S_FALSE` liegt keine PDATA für die angegebene Adresse. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Der pdata-Abschnitt (Abschnitt mit dem Namen ".pdata-Datensatz") eine Kompiliereinheit enthält Informationen über Ausnahmebehandlung für Funktionen.  
  
 Der Aufrufer weiß, wie viele Daten befinden, zurückgegeben werden, damit der Aufrufer nicht erforderlich verfügt, stellen Sie für wie viele Daten zur Verfügung steht. Daher ist es für eine Implementierung dieser Methode einen Fehler zurückgegeben, wenn die `pbData` Parameter `NULL`.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
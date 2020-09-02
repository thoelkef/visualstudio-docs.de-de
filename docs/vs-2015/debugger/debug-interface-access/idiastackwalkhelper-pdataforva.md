---
title: IDiaStackWalkHelper::p dataforva | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::pdataByVA method
ms.assetid: fafc38fe-74dc-4726-9a51-eebf3a673d7f
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5af921caa989d7279bb9f52751c452d91045cf3e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150094"
---
# <a name="idiastackwalkhelperpdataforva"></a>IDiaStackWalkHelper::pdataForVA
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Gibt den pData-Datenblock zurück, der der virtuellen Adresse zugeordnet ist.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT pdataForVA(   
   ULONGLONG  va,  
   DWORD      cbData,  
   DWORD*     pcbData,  
   BYTE*      pbData  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `va`  
 in Gibt die virtuelle Adresse der abzurufenden Daten an.  
  
 `cbData`  
 in Die Größe der abzurufenden Daten in Bytes.  
  
 `pcbData`  
 vorgenommen Gibt die tatsächliche Größe der Daten in Bytes zurück, die abgerufen wurden.  
  
 `pbData`  
 [in, out] Ein Puffer, der mit den angeforderten Daten gefüllt wird. Darf nicht `NULL` sein.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt bei Erfolg `S_OK` zurück. Gibt zurück, `S_FALSE` Wenn keine pData für die angegebene Adresse vorhanden ist. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 PData (der-Abschnitt mit dem Namen ". pdata") eines Kompilierungen enthält Informationen zur Ausnahmebehandlung für Funktionen.  
  
 Der Aufrufer weiß, wie viele Daten zurückgegeben werden sollen, sodass der Aufrufer nicht mehr gefragt werden muss, wie viele Daten verfügbar sind. Daher ist es zulässig, dass eine Implementierung dieser Methode einen Fehler zurückgibt, wenn der- `pbData` Parameter ist `NULL` .  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)

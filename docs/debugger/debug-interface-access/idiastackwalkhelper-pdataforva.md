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
ms.openlocfilehash: 6315032a36369eff7a5d43241ae4968a64ad42cc
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56685456"
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

## <a name="remarks"></a>Anmerkungen
 Der pdata-Abschnitt (Abschnitt mit dem Namen ".pdata-Datensatz") eine Kompiliereinheit enthält Informationen über Ausnahmebehandlung für Funktionen.

 Der Aufrufer weiß, wie viele Daten befinden, zurückgegeben werden, damit der Aufrufer nicht erforderlich verfügt, stellen Sie für wie viele Daten zur Verfügung steht. Daher ist es für eine Implementierung dieser Methode einen Fehler zurückgegeben, wenn die `pbData` Parameter `NULL`.

## <a name="see-also"></a>Siehe auch
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
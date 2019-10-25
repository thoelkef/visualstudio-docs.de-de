---
title: 'IDiaFrameData:: get_program | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_program method
ms.assetid: 9201409e-b4b1-4e2e-a9f8-d17678ac538b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 135f2b0a042dd74b573a0746831a48fb27e7c2a9
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743517"
---
# <a name="idiaframedataget_program"></a>IDiaFrameData::get_program
Ruft die Programm Zeichenfolge ab, die verwendet wird, um den Register Satz vor dem aufgerufenen der aktuellen Funktion zu berechnen.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_program ( 
   BSTR* pRetVal
);
```

#### <a name="parameters"></a>Parameter
 `pRetVal`

vorgenommen Gibt die Programm Zeichenfolge zurück.

## <a name="return-value"></a>Rückgabewert
 Gibt bei Erfolg `S_OK` zurück. Gibt `S_FALSE` zurück, wenn diese Eigenschaft nicht unterstützt wird. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Die Programm Zeichenfolge ist eine Sequenz von Makros, die zum Erstellen des Prologs interpretiert wird. Beispielsweise kann ein typischer Stapel Rahmen die Programm Zeichenfolge `"$T0 $ebp = $eip $T0 4 + ^ = $ebp $T0 ^ = $esp $T0 8 + ="` verwenden. Das Format ist die umgekehrte polnische Notation, bei der die Operatoren den Operanden folgen. `T0` stellt eine temporäre Variable im Stapel dar. In diesem Beispiel werden die folgenden Schritte ausgeführt:

1. Verschieben Sie den Inhalt von Register `ebp` in `T0`.

2. Fügen Sie `4` dem Wert in `T0` hinzu, um eine Adresse zu erhalten, den Wert von dieser Adresse zu erhalten und den Wert in Register `eip` zu speichern.

3. Legen Sie den Wert aus der in `T0` gespeicherten Adresse ab, und speichern Sie diesen Wert in Register `ebp`.

4. Fügen Sie `8` dem Wert in `T0` hinzu, und speichern Sie diesen Wert in Register `esp`.

   Beachten Sie, dass die Programm Zeichenfolge für die CPU und die Aufruf Konvention spezifisch ist, die für die durch den aktuellen Stapel Rahmen dargestellte Funktion eingerichtet ist.

## <a name="see-also"></a>Siehe auch
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
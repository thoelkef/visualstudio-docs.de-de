---
title: StackFrameTypeEnum | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- StackFrameTypeEnum enumeration
ms.assetid: 61e40163-eee0-4c1f-af47-cef3771bdc41
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 44f715c4f74d9b120b324e2d68417a24c9b42684
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62854830"
---
# <a name="stackframetypeenum"></a>StackFrameTypeEnum
Gibt den Stack-Frame-Typ.

## <a name="syntax"></a>Syntax

```C++
enum StackFrameTypeEnum {
    FrameTypeFPO,
    FrameTypeTrap,
    FrameTypeTSS,
    FrameTypeStandard,
    FrameTypeFrameData,
    FrameTypeUnknown = -1
};
```

## <a name="elements"></a>Elements
`FrameTypeFPO` Frame-Pointer ausgelassen; FPO-Informationen verfügbar.

`FrameTypeTrap` Kernel-Trap-Frame.

`FrameTypeTSS` Kernel-Trap-Frame.

`FrameTypeStandard` Standard EBP-Stapelrahmen.

`FrameTypeFrameData` Frame-Pointer ausgelassen; Frame-Daten-Informationen verfügbar.

`FrameTypeUnknown` Frame aus, der kein Debuginformationen vorhanden wären.

## <a name="remarks"></a>Hinweise
Die Werte in dieser Enumeration werden zurückgegeben, durch einen Aufruf der [idiastackframe:: Get_type](../../debugger/debug-interface-access/idiastackframe-get-type.md) Methode.

## <a name="requirements"></a>Anforderungen
Header: cvconst.h

## <a name="see-also"></a>Siehe auch
- [Enumerationen und Strukturen](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaStackFrame::get_type](../../debugger/debug-interface-access/idiastackframe-get-type.md)

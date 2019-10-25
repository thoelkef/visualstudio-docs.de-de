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
ms.openlocfilehash: 20b0c9dd106e5744a369ddaa6cb870788f7464d3
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738553"
---
# <a name="stackframetypeenum"></a>StackFrameTypeEnum
Gibt den Stapel Rahmentyp an.

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
`FrameTypeFPO` Frame Zeiger ausgelassen. Die verfügbaren Informationen zur Verfügbarkeit

`FrameTypeTrap` Kernel Trap Frame.

`FrameTypeTSS` Kernel Trap Frame.

`FrameTypeStandard` Standard-EBP-Stapel Rahmen.

`FrameTypeFrameData` Frame Zeiger ausgelassen. Informationen zur Frame-Daten sind verfügbar.

`FrameTypeUnknown` Frame, der keine Debuginformationen enthält.

## <a name="remarks"></a>Hinweise
Die Werte in dieser Enumeration werden von einem Rückruf der [IDiaStackFrame:: get_type](../../debugger/debug-interface-access/idiastackframe-get-type.md) -Methode zurückgegeben.

## <a name="requirements"></a>Anforderungen
Header: cvconst.h

## <a name="see-also"></a>Siehe auch
- [Enumerationen und Strukturen](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaStackFrame::get_type](../../debugger/debug-interface-access/idiastackframe-get-type.md)

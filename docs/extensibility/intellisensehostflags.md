---
title: IntelliSenseHostFlags | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IntellisenseHostFlags
helpviewer_keywords:
- IntelliSense, IntellisenseHostFlags enumeration
- IntellisenseHostFlags enumeration
ms.assetid: 0930640b-eb84-48ef-a8f7-d4268f55c99c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a0df05e7363db01bd4f16fee5d75141dc93df1c0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710274"
---
# <a name="intellisensehostflags"></a>IntelliSenseHostFlags
Gibt IntelliSense-Hostflags an.

## <a name="syntax"></a>Syntax

```cpp
enum IntellisenseHostFlags
{
    IHF_READONLYCONTEXT      = 0x00000001
    IHF_NOSEPARATESUBJECT    = 0x00000002
    IHF_SINGLELINESUBJECT    = 0x00000004
    IHF_FORCECOMMITTOCONTEXT = 0x00000008
    IHF_OVERTYPE             = 0x00000010
};
```

### <a name="parameters"></a>Parameter

|Member|BESCHREIBUNG|
|-------------|-----------------|
|`IHF_READONLYCONTEXT`|Der Kontextpuffer ist schreibgeschützt.|
|`IHF_NOSEPARATESUBJECT`|Kein Betrefftext. Kontextpuffer enthält IntelliSense-Target `!IHF_READONLYCONTEXT`(implies ).|
|`IHF_SINGLELINESUBJECT`|Betrefftext ist nicht mehrzeiligenfähig.|
|`IHF_FORCECOMMITTOCONTEXT`|Identisch mit `CanCommitIntoReadOnlyBuffer`.|
|`IHF_OVERTYPE`|Die Bearbeitung (im Betreff oder Kontext) sollte im Übertypmodus erfolgen.|

## <a name="requirements"></a>Requirements (Anforderungen)
 SingleFileeditor.idl

## <a name="see-also"></a>Weitere Informationen
- <xref:Microsoft.VisualStudio.TextManager.Interop>

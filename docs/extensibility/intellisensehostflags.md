---
title: IntelliSenseHostFlags | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IntellisenseHostFlags
helpviewer_keywords:
- IntelliSense, IntellisenseHostFlags enumeration
- IntellisenseHostFlags enumeration
ms.assetid: 0930640b-eb84-48ef-a8f7-d4268f55c99c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 882410d68c671a83b13bd14026e5bea4c31cb37e
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56683557"
---
# <a name="intellisensehostflags"></a>IntelliSenseHostFlags
Gibt die IntelliSense-hostflags an.

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

|Member|Beschreibung|
|-------------|-----------------|
|`IHF_READONLYCONTEXT`|Kontextpuffer ist schreibgeschützt.|
|`IHF_NOSEPARATESUBJECT`|Kein Betrefftext. Kontextpuffer enthält IntelliSense-Ziel (impliziert `!IHF_READONLYCONTEXT`).|
|`IHF_SINGLELINESUBJECT`|Betreff-Texts ist keine multi-Befehlszeile-fähig.|
|`IHF_FORCECOMMITTOCONTEXT`|Wie in `CanCommitIntoReadOnlyBuffer`.|
|`IHF_OVERTYPE`|Bearbeiten (in den Betreff- oder kontextfeldern) sollte im Überschreibmodus durchgeführt werden.|

## <a name="requirements"></a>Anforderungen
 SingleFileeditor.idl

## <a name="see-also"></a>Siehe auch
- <xref:Microsoft.VisualStudio.TextManager.Interop>
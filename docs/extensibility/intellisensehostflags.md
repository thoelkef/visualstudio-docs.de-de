---
title: IntelliSenseHostFlags | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IntellisenseHostFlags
helpviewer_keywords:
- IntelliSense, IntellisenseHostFlags enumeration
- IntellisenseHostFlags enumeration
ms.assetid: 0930640b-eb84-48ef-a8f7-d4268f55c99c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 582dc76bfd8b76ffa4d3664ab3e28f95fe2cef50
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/03/2018
ms.locfileid: "39500013"
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
 <xref:Microsoft.VisualStudio.TextManager.Interop>
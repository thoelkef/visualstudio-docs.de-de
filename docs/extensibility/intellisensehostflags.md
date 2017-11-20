---
title: IntelliSenseHostFlags | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IntellisenseHostFlags
helpviewer_keywords:
- IntelliSense, IntellisenseHostFlags enumeration
- IntellisenseHostFlags enumeration
ms.assetid: 0930640b-eb84-48ef-a8f7-d4268f55c99c
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d8e00768e544dbd6bb37a4de70e0f730fe967a70
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="intellisensehostflags"></a>IntelliSenseHostFlags
Gibt Flags für IntelliSense-Host.  
  
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
  
#### <a name="parameters"></a>Parameter  
  
|Member|Beschreibung|  
|-------------|-----------------|  
|`IHF_READONLYCONTEXT`|Kontextpuffer ist schreibgeschützt.|  
|`IHF_NOSEPARATESUBJECT`|Kein Betrefftext. Kontextpuffer IntelliSense-Ziel enthält (impliziert `!IHF_READONLYCONTEXT`).|  
|`IHF_SINGLELINESUBJECT`|Betreff kann keine multi-Befehlszeile.|  
|`IHF_FORCECOMMITTOCONTEXT`|Wie in `CanCommitIntoReadOnlyBuffer`.|  
|`IHF_OVERTYPE`|Bearbeitung (im Antragstellernamen oder Kontextmenü) sollte im Überschreibmodus erfolgen.|  
  
## <a name="requirements"></a>Anforderungen  
 SingleFileeditor.idl  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.TextManager.Interop>
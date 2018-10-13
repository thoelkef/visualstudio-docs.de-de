---
title: IntelliSenseHostFlags | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IntellisenseHostFlags
helpviewer_keywords:
- IntelliSense, IntellisenseHostFlags enumeration
- IntellisenseHostFlags enumeration
ms.assetid: 0930640b-eb84-48ef-a8f7-d4268f55c99c
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2fdc08f6e71a6da718f37e88f40d71df00ee89ab
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49190995"
---
# <a name="intellisensehostflags"></a>IntelliSenseHostFlags
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Gibt die IntelliSense-hostflags an.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
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
|`IHF_NOSEPARATESUBJECT`|Kein Betrefftext. Kontextpuffer enthält IntelliSense-Ziel (impliziert `!IHF_READONLYCONTEXT`).|  
|`IHF_SINGLELINESUBJECT`|Betreff-Texts ist keine multi-Befehlszeile-fähig.|  
|`IHF_FORCECOMMITTOCONTEXT`|Wie in `CanCommitIntoReadOnlyBuffer`.|  
|`IHF_OVERTYPE`|Bearbeiten (in den Betreff- oder kontextfeldern) sollte im Überschreibmodus durchgeführt werden.|  
  
## <a name="requirements"></a>Anforderungen  
 SingleFileeditor.idl  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.TextManager.Interop>


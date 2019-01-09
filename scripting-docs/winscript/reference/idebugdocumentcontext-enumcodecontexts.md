---
title: IDebugDocumentContext::EnumCodeContexts | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentContext.EnumCodeContexts
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentContext::EnumCodeContexts
ms.assetid: fb0aa64e-c458-4ef1-bcd8-5cebdc972549
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 47bf36a8d013ffbb3c09214d590960c833e53218
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2019
ms.locfileid: "54086267"
---
# <a name="idebugdocumentcontextenumcodecontexts"></a>IDebugDocumentContext::EnumCodeContexts
Listet die Codekontexte mit diesem Dokumentenkontext verknüpft ist.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT EnumCodeContexts(  
   IEnumDebugCodeContexts**  ppescc  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppescc`  
 [out] Die Codekontexte mit diesem Dokumentenkontext verknüpft ist.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Ein Dokument ist nur ein Codekontext, in der Regel zugeordnet, es sei denn, das Dokument einer Include-Datei oder einer Vorlage ist.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugDocumentContext-Schnittstelle](../../winscript/reference/idebugdocumentcontext-interface.md)
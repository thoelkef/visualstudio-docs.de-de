---
title: Idebugdocumenthelper | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.Init
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::Init
ms.assetid: 1dd5a01f-0779-4109-8c6c-f16f5a3835bf
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3b399f51fc042aa1ed297ab30a7bf2c9bc4befca
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58160013"
---
# <a name="idebugdocumenthelperinit"></a>IDebugDocumentHelper::Init
Die `Init` Methode initialisiert, ein Dokument Debughilfe mit einem Namen und die anfängliche Attribute.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT Init(  
   IDebugApplication*  pda,  
   LPCOLESTR           pszShortName,  
   LPCOLESTR           pszLongName,  
   TEXT_DOC_ATTR       docAttr  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pda`  
 [in] Die Debuganwendung, die in diesem Dokument zugeordnet.  
  
 `pszShortName`  
 [in] Eine mit Null endende Zeichenfolge, die den kurzen Namen des Dokuments enthält.  
  
 `pszLongName`  
 [in] Eine mit Null endende Zeichenfolge, die den langen Namen des Dokuments enthält.  
  
 `docAttr`  
 [in] Gibt Text Dokumentattribute.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode initialisiert, ein Dokument Debughilfe mit einem Namen und die anfängliche Attribute.  
  
 In diesem Dokument wird nicht angezeigt, in der Struktur bis `IDebugDocumentHelper::Attach` aufgerufen wird.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugDocumentHelper::Attach](../../winscript/reference/idebugdocumenthelper-attach.md)   
 [IDebugDocumentHelper-Schnittstelle](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [TEXT_DOC_ATTR-Konstanten](../../winscript/reference/text-doc-attr-constants.md)
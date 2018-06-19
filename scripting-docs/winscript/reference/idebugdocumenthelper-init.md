---
title: IDebugDocumentHelper::Init | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 45cd57e4ba9e86bf84f927f487c637d61aa5339b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24726320"
---
# <a name="idebugdocumenthelperinit"></a>IDebugDocumentHelper::Init
Die `Init` -Methode initialisiert eine Debug-Dokument-Hilfsprogramm mit einem Namen und anfängliche Attribute.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT Init(  
   IDebugApplication*  pda,  
   LPCOLESTR           pszShortName,  
   LPCOLESTR           pszLongName,  
   TEXT_DOC_ATTR       docAttr  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pda`  
 [in] Die Debuganwendung, die diesem Dokument zugeordnet wird.  
  
 `pszShortName`  
 [in] Eine auf Null endende Zeichenfolge, die den kurzen Namen des Dokuments enthält.  
  
 `pszLongName`  
 [in] Eine auf Null endende Zeichenfolge, enthält den langen Namen des Dokuments.  
  
 `docAttr`  
 [in] Gibt Text Dokumentattribute an.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode initialisiert eine Debug-Dokument-Hilfsprogramm mit einem Namen und anfängliche Attribute.  
  
 Dieses Dokument wird nicht angezeigt, in der Struktur bis `IDebugDocumentHelper::Attach` aufgerufen wird.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugDocumentHelper::Attach](../../winscript/reference/idebugdocumenthelper-attach.md)   
 [IDebugDocumentHelper-Schnittstelle](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [TEXT_DOC_ATTR-Konstanten](../../winscript/reference/text-doc-attr-constants.md)
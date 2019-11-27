---
title: 'Idebugdocumenthelper:: init | Microsoft-Dokumentation'
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
ms.openlocfilehash: 13e6379052707aa44c0fa52f4cb30db2c4c4fa99
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576861"
---
# <a name="idebugdocumenthelperinit"></a>IDebugDocumentHelper::Init
Die `Init`-Methode initialisiert ein debugdokumenthilfsprogramm mit einem Namen und anfänglichen Attributen.  
  
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
 in Die Debuganwendung, die diesem Dokument zugeordnet ist.  
  
 `pszShortName`  
 in Eine NULL-terminierte Zeichenfolge, die den Kurznamen des Dokuments enthält.  
  
 `pszLongName`  
 in Eine NULL-terminierte Zeichenfolge, die den langen Namen des Dokuments enthält.  
  
 `docAttr`  
 in Gibt Textdokument Attribute an.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode initialisiert ein debugdokumenthilfsprogramm mit einem Namen und anfänglichen Attributen.  
  
 Dieses Dokument wird erst dann in der Struktur angezeigt, wenn `IDebugDocumentHelper::Attach` aufgerufen wird.  
  
## <a name="see-also"></a>Siehe auch  
 [Idebugdocumenthelper:: Attach](../../winscript/reference/idebugdocumenthelper-attach.md)   
 [Idebugdocumenthelper-Schnittstelle](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [TEXT_DOC_ATTR-Konstanten](../../winscript/reference/text-doc-attr-constants.md)
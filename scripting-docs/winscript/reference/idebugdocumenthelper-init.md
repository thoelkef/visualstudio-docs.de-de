---
title: "IDebugDocumentHelper::Init | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentHelper.Init
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentHelper::Init"
ms.assetid: 1dd5a01f-0779-4109-8c6c-f16f5a3835bf
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHelper::Init
Die `Init`\-Methode initialisiert eine Debug\- Dokumentenhilfe mit einem Namen und Initialenattributen.  
  
## Syntax  
  
```  
HRESULT Init(  
   IDebugApplication*  pda,  
   LPCOLESTR           pszShortName,  
   LPCOLESTR           pszLongName,  
   TEXT_DOC_ATTR       docAttr  
);  
```  
  
#### Parameter  
 `pda`  
 \[in\] Die Debugsitzung zugeordnete Anwendung diesem Dokument.  
  
 `pszShortName`  
 \[in\] auf NULL endende Zeichenfolge, die den kurzen Namen des Dokuments enthält.  
  
 `pszLongName`  
 \[in\] auf NULL endende Zeichenfolge, die den langen Namen des Dokuments enthält.  
  
 `docAttr`  
 \[in\] Gibt Textdokumentattribute an.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Diese Methode initialisiert eine Debug\- Dokumentenhilfe mit einem Namen und Initialenattributen.  
  
 In diesem Dokument wird nicht in der Struktur, bis `IDebugDocumentHelper::Attach` aufgerufen wird.  
  
## Siehe auch  
 [IDebugDocumentHelper::Attach](../../winscript/reference/idebugdocumenthelper-attach.md)   
 [IDebugDocumentHelper\-Schnittstelle](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [TEXT\_DOC\_ATTR\-Konstanten](../../winscript/reference/text-doc-attr-constants.md)
---
title: TEXT_DOC_ATTR-Konstanten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- TEXT_DOC_ATTR
apilocation:
- scrobj.dll
helpviewer_keywords:
- TEXT_DOC_ATTR constants
ms.assetid: fd9c53a4-8f73-4c6a-abe5-6b831ecd5b1e
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d22b178d85d304f19e52727ef2c67d77f16da1b3
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58147383"
---
# <a name="textdocattr-constants"></a>TEXT_DOC_ATTR-Konstanten
Beschreiben die Attribute des Dokuments.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
typedef DWORD TEXT_DOC_ATTR;  
```  
  
## <a name="constants"></a>Konstanten  
  
|Konstante|Wert|Beschreibung|  
|--------------|-----------|-----------------|  
|TEXT_DOC_ATTR_READONLY|0x00000001|Das Dokument ist schreibgeschützt.|  
|TEXT_DOC_ATTR_TYPE_PRIMARY|0x00000002|Das Dokument ist die primäre Datei der dieser Struktur des Dokuments.|  
|TEXT_DOC_ATTR_TYPE_WORKER|0x00000004|Das Dokument ist ein Worker.|  
|TEXT_DOC_ATTR_TYPE_SCRIPT|0x00000008|Das Dokument ist eine Skriptdatei an.|  
  
## <a name="see-also"></a>Siehe auch  
 [Konstanten, Enumerationen und Strukturen für Active Script-Debugger](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)
---
title: DOCUMENTNAMETYPE-Enumeration | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- DOCUMENTNAMETYPE
apilocation:
- scrobj.dll
helpviewer_keywords:
- DOCUMENTNAMETYPE enumeration
ms.assetid: d36d550e-efb4-493d-8971-4de267005654
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 31e304cfbb0ed7cd19b832d7ed7c33ccc2c930c3
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2019
ms.locfileid: "54094769"
---
# <a name="documentnametype-enumeration"></a>DOCUMENTNAMETYPE-Enumeration
Beschreibt, welche Typen für ein Dokument abzurufen sind.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
typedef enum tagDOCUMENTNAMETYPE {  
   DOCUMENTNAMETYPE_APPNODE,  
   DOCUMENTNAMETYPE_TITLE,  
   DOCUMENTNAMETYPE_FILE_TAIL,  
   DOCUMENTNAMETYPE_URL,  
DOCUMENTNAMETYPE_UNIQUE_TITLE,} DOCUMENTNAMETYPE;  
```  
  
## <a name="members"></a>Member  
  
|Member|Beschreibung|  
|------------|-----------------|  
|DOCUMENTNAMETYPE_APPNODE|Ruft den Namen an, wie er in der Anwendungsstruktur angezeigt wird.|  
|DOCUMENTNAMETYPE_TITLE|Ruft den Namen an, wie er in der Titelleiste Viewer angezeigt wird.|  
|DOCUMENTNAMETYPE_FILE_TAIL|Ruft den Dateinamen ohne Pfad ab.|  
|DOCUMENTNAMETYPE_URL|Ruft die URL des Dokuments ab.|  
|DOCUMENTNAMETYPE_UNIQUE_TITLE|Ruft den Titel, die Enumeration für die Identifikation angefügtem ab.|  
  
## <a name="see-also"></a>Siehe auch  
 [Konstanten, Enumerationen und Strukturen für Active Script-Debugger](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)
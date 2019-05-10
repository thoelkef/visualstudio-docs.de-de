---
title: DOCUMENTNAMETYPE-Enumeration | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 5ee258602c47951f4731dc1378542cc83d57d72b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62955213"
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
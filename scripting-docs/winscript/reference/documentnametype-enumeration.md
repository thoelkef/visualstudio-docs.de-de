---
title: Documentnametype-Enumeration | Microsoft-Dokumentation
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
ms.openlocfilehash: 401eb759523ed1a33d24c3a298db0b3de2b7d5a7
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575873"
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
|DOCUMENTNAMETYPE_APPNODE|Ruft den Namen ab, wie er in der Anwendungs Struktur angezeigt wird.|  
|DOCUMENTNAMETYPE_TITLE|Ruft den Namen ab, wie er auf der Viewer-Titelleiste angezeigt wird.|  
|DOCUMENTNAMETYPE_FILE_TAIL|Ruft den Dateinamen ohne Pfad ab.|  
|DOCUMENTNAMETYPE_URL|Ruft die URL des Dokuments ab.|  
|DOCUMENTNAMETYPE_UNIQUE_TITLE|Ruft den Titel ab, der mit Enumeration zur Identifizierung angefügt wird.|  
  
## <a name="see-also"></a>Siehe auch  
 [Konstanten, Enumerationen und Strukturen für Active Script-Debugger](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)
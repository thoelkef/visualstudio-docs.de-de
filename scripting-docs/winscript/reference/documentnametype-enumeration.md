---
title: DOCUMENTNAMETYPE-Enumeration | Microsoft Docs
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
ms.openlocfilehash: a0bd21dddd209f21ae64ea2775bbaa0da226f077
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640580"
---
# <a name="documentnametype-enumeration"></a>DOCUMENTNAMETYPE-Enumeration
Beschreibt, welche Typen für ein Dokument abzurufen sind.  
  
## <a name="syntax"></a>Syntax  
  
```  
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
|DOCUMENTNAMETYPE_APPNODE|Ruft den Namen ab, wie er in der Anwendungsstruktur angezeigt wird.|  
|DOCUMENTNAMETYPE_TITLE|Ruft den Namen ab, wie er auf der Titelleiste angezeigt wird.|  
|DOCUMENTNAMETYPE_FILE_TAIL|Ruft den Dateinamen ohne Pfad ab.|  
|DOCUMENTNAMETYPE_URL|Ruft die URL des Dokuments ab.|  
|DOCUMENTNAMETYPE_UNIQUE_TITLE|Ruft den Titel angehängt Enumeration für die Identifikation ab.|  
  
## <a name="see-also"></a>Siehe auch  
 [Konstanten, Enumerationen und Strukturen für Active Script-Debugger](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)
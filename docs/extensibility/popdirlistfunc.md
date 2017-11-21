---
title: POPDIRLISTFUNC | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: POPLISTFUNC
helpviewer_keywords: POPDIRLISTFUNC callback function
ms.assetid: 0ee90fd2-5467-4154-ab4c-7eb02ac3a14c
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7d5279f16dbc8228f0f116c47e6faa3ab0093472
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="popdirlistfunc"></a>POPDIRLISTFUNC
Dies ist eine Funktion übergeben, um die [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) Funktion, um eine Auflistung von Verzeichnissen und (optional) um herauszufinden, welche in der quellcodeverwaltung sind Dateinamen zu aktualisieren.  
  
 Die `POPDIRLISTFUNC` Rückruf sollte nur für die Verzeichnisse und den Dateinamen aufgerufen werden (in der Liste übergeben, um die `SccPopulateDirList` Funktion), sind tatsächlich in der quellcodeverwaltung.  
  
## <a name="signature"></a>Signatur  
  
```cpp  
typedef BOOL (*POPDIRLISTFUNC)(  
   LPVOID pvCallerData,  
   BOOL bFolder,  
   LPCSTR lpDirectoryOrFileName  
);  
```  
  
## <a name="parameters"></a>Parameter  
 pvCallerData  
 [in] Benutzerwert übergeben, um [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md).  
  
 auf bOrdneroptionen  
 [in] `TRUE` Wenn der Name in `lpDirectoryOrFileName` ist ein Verzeichnis; andernfalls der Name ist ein Dateiname.  
  
 lpDirectoryOrFileName  
 [in] Vollständige lokale Pfad zu einem Verzeichnis oder Datei Namen, unter quellcodeverwaltung.  
  
## <a name="return-value"></a>Rückgabewert  
 Die IDE wird ein entsprechenden Fehlercode zurückgegeben:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|SCC_OK|Setzt die Verarbeitung fort.|  
|SCC_I_OPERATIONCANCELED|Beendet die Verarbeitung.|  
|SCC_E_xxx|Verarbeitet beendet alle entsprechenden Quelle-Steuerelement auftreten des Fehlers.|  
  
## <a name="remarks"></a>Hinweise  
 Wenn die `fOptions` Parameter von der `SccPopulateDirList` Funktion enthält die `SCC_PDL_INCLUDEFILES` kennzeichnen, und klicken Sie dann die Liste möglicherweise Dateinamen sowie Verzeichnisnamen enthalten soll.  
  
## <a name="see-also"></a>Siehe auch  
 [Rückruffunktionen implementiert, die von der IDE](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)   
 [Fehlercodes](../extensibility/error-codes.md)
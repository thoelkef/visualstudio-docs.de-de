---
title: Popdirlistfunc | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- POPLISTFUNC
helpviewer_keywords:
- POPDIRLISTFUNC callback function
ms.assetid: 0ee90fd2-5467-4154-ab4c-7eb02ac3a14c
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 77e4701d3d8ec54fd37d6483f55b10a28af65b15
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194050"
---
# <a name="popdirlistfunc"></a>POPDIRLISTFUNC
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dies ist eine Rückruffunktion, die der [sccpopulatedirlist](../extensibility/sccpopulatedirlist-function.md) -Funktion übergeben wird, um eine Auflistung von Verzeichnissen und (optional) Dateinamen zu aktualisieren, die sich unter Quell Code Verwaltung befinden.  
  
 Der `POPDIRLISTFUNC` Rückruf sollte nur für die Verzeichnisse und Dateinamen (in der für die Funktion angegebenen Liste) aufgerufen werden `SccPopulateDirList` , die sich tatsächlich unter Quell Code Verwaltung befinden.  
  
## <a name="signature"></a>Signatur  
  
```cpp#  
typedef BOOL (*POPDIRLISTFUNC)(  
   LPVOID pvCallerData,  
   BOOL bFolder,  
   LPCSTR lpDirectoryOrFileName  
);  
```  
  
## <a name="parameters"></a>Parameter  
 pvcallerdata  
 in Benutzer Wert, der [sccpopulatedirlist](../extensibility/sccpopulatedirlist-function.md)zugewiesen ist.  
  
 bfolder  
 [in] `TRUE` , wenn der Name in `lpDirectoryOrFileName` ein Verzeichnis ist, andernfalls ist der Name ein Dateiname.  
  
 lpdirector yorfilename  
 in Vollständiger lokaler Pfad zu einem Verzeichnis-oder Dateinamen, der sich unter Quell Code Verwaltung befindet.  
  
## <a name="return-value"></a>Rückgabewert  
 Die IDE gibt einen entsprechenden Fehlercode zurück:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|SCC_OK|Setzen Sie die Verarbeitung fort.|  
|SCC_I_OPERATIONCANCELED|Beendet die Verarbeitung.|  
|SCC_E_xxx|Jeder geeignete Quell Code Verwaltungsfehler sollte die Verarbeitung verhindern.|  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn der- `fOptions` Parameter der `SccPopulateDirList` Funktion das- `SCC_PDL_INCLUDEFILES` Flag enthält, enthält die Liste möglicherweise Dateinamen und Verzeichnisnamen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Von der IDE implementierte Rückruf Funktionen](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [Sccpopulatedirlist](../extensibility/sccpopulatedirlist-function.md)   
 [Fehlercodes](../extensibility/error-codes.md)

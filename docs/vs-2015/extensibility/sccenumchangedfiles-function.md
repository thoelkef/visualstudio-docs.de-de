---
title: Sccenumchangedfiles-Funktion | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccEnumChangedFiles
helpviewer_keywords:
- SccEnumChangedFiles function
ms.assetid: 76cac510-107b-4c1a-ba60-9c39b6db2e71
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 00ef98c93f02aa8e8a1b4ea53f1998d0ab6713a9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200129"
---
# <a name="sccenumchangedfiles-function"></a>SccEnumChangedFiles-Funktion
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn eine Liste lokaler Dateien angegeben ist, bestimmt diese Funktion, welche Dateien sich von den entsprechenden Versionen in der Quell Code Verwaltungs Datenbank unterscheiden.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
SCCRTN SccEnumChangedFiles(  
   LPVOID  pContext,  
   HWND    hWnd,  
   LONG    cFiles,  
   LPCSTR* lpFileNames,  
   LONG*   plIsFileDifferent  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 pContext  
 in Der Kontext Zeiger für das Quellcodeverwaltungs-Plug-in.  
  
 hWnd  
 in Ein Handle für das IDE-Fenster, das vom Quellcodeverwaltungs-Plug-in als übergeordnetes Element für alle bereitgestellten Dialogfelder verwendet werden kann.  
  
 cFiles  
 in Anzahl der im Array angegebenen Dateinamen `lpFileNames` . Gibt auch die Größe des `plIsFileDifferent` Arrays an.  
  
 lpfile-Namen  
 in Array der lokalen Dateinamen, die überprüft werden sollen.  
  
 plisfiledifferent  
 [in, out] Ein Array von-Werten, die den Differenz Status der einzelnen Dateien angeben (Array muss mindestens `cFiles` Einträge aufweisen). Ungleich 0 bedeutet, dass die Datei anders ist.  
  
## <a name="return-value"></a>Rückgabewert  
 Es wird erwartet, dass die Plug-in-Implementierung der Quell Code Verwaltung diese Funktion einen der folgenden Werte zurückgibt:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|SCC_OK|Operation erfolgreich abgeschlossen.|  
|SCC_UNSPECIFIEDERROR|Allgemeiner Fehler.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [API-Funktionen von Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-in-api-functions.md)

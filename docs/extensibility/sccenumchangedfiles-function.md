---
title: SccEnumChangedFiles Funktion | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccEnumChangedFiles
helpviewer_keywords:
- SccEnumChangedFiles function
ms.assetid: 76cac510-107b-4c1a-ba60-9c39b6db2e71
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 762bda21f8480224347bd0c8c202c282298e07cc
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31137130"
---
# <a name="sccenumchangedfiles-function"></a>SccEnumChangedFiles-Funktion
Basierend auf einer Liste von lokalen Dateien, bestimmt diese Funktion, welche Dateien in der Quellcode-Verwaltungsdatenbank Code die entsprechenden Versionen unterscheiden.  
  
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
 "pContext"  
 [in] Der Datenquellen-Steuerelement-Plug-in Kontextzeiger.  
  
 hWnd  
 [in] Ein Handle für die IDE-Fenster, das das Quellsteuerelement-Plug-in als übergeordnetes Element für alle Dialogfelder verwenden kann, die es bereitstellt.  
  
 cFiles  
 [in] Anzahl der im angegebenen Dateinamen der `lpFileNames` Array. Gibt auch die Größe des `plIsFileDifferent` Array.  
  
 lpFileNames  
 [in] Array der Namen der lokalen Datei zu überprüfen.  
  
 plIsFileDifferent  
 [in, out] Array von Werten, die den Unterschied Status der einzelnen Dateien (Array benötigen mindestens `cFiles` Einträge). Ungleich NULL bedeutet, dass die Datei unterscheidet.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Source Control-Plug-in-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|SCC_OK|Der Vorgang wurde erfolgreich abgeschlossen.|  
|SCC_UNSPECIFIEDERROR|Allgemeiner Fehler.|  
  
## <a name="see-also"></a>Siehe auch  
 [API-Funktionen von Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-in-api-functions.md)
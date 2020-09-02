---
title: Sccproperties-Funktion | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccProperties
helpviewer_keywords:
- SccProperties function
ms.assetid: 1bed38c9-73d2-4474-9717-f9dc26a89cbe
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f4e8452465873cb66883abd347406d17b469e90a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68199998"
---
# <a name="sccproperties-function"></a>SccProperties-Funktion
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Diese Funktion zeigt Quell Code Verwaltungs Eigenschaften für eine Datei oder ein Projekt an.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
SCCRTN SccProperties (  
   LPVOID pvContext,  
   HWND   hWnd,  
   LPCSTR lpFileName  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 pvcontext  
 in Die Kontext Struktur der Quellcodeverwaltungs-Plug-in.  
  
 hWnd  
 in Ein Handle für das IDE-Fenster, das vom Quellcodeverwaltungs-Plug-in als übergeordnetes Element für alle bereitgestellten Dialogfelder verwendet werden kann.  
  
 lpFileName  
 in Der voll qualifizierte Pfadname der Datei oder des Projekts.  
  
## <a name="return-value"></a>Rückgabewert  
 Es wird erwartet, dass die Plug-in-Implementierung der Quell Code Verwaltung diese Funktion einen der folgenden Werte zurückgibt:  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|SCC_OK|Eigenschaften wurden erfolgreich angezeigt.|  
|SCC_I_RELOADFILE|Das Versionskontrollsystem hat die Dateieigenschaften geändert, sodass die IDE diese Datei erneut laden soll.|  
|SCC_E_PROJNOTOPEN|Das angegebene Projekt wurde nicht in der Quell Code Verwaltung geöffnet.|  
|SCC_E_NOTAUTHORIZED|Der Benutzer ist nicht autorisiert, die Eigenschaften dieser Datei oder des Projekts anzuzeigen.|  
|SCC_E_FILENOTCONTROLLED|Die angegebene Datei oder das angegebene Projekt befindet sich nicht in der Quell Code Verwaltung.|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Ein unbekannter oder allgemeiner Fehler ist aufgetreten.|  
  
## <a name="remarks"></a>Bemerkungen  
 Das Quellcodeverwaltungs-Plug-in zeigt die Eigenschaften in einem eigenen Dialogfeld an.  
  
 Die Eigenschaften werden durch das Quellcodeverwaltungs-Plug-in definiert und können sich vom Plug-in zum Plug-in unterscheiden. Wenn das Plug-in es dem Benutzer ermöglicht, die Eigenschaften der Quell Code Verwaltung einer Datei zu ändern, sollte zurückgegeben werden, `SCC_I_RELOAD` um der IDE zu signalisieren, dass diese Datei bzw. das Projekt erneut geladen werden muss.  
  
## <a name="see-also"></a>Weitere Informationen  
 [API-Funktionen von Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-in-api-functions.md)

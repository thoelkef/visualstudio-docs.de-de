---
title: POPLISTFUNC | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- POPDIRLISTFUNC
helpviewer_keywords:
- POPLISTFUNC callback function
ms.assetid: b2199fd5-d707-4628-92dd-e2a01e2f507a
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a8b193eae0e41f48c0f947bbf8af596084a1544f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47522748"
---
# <a name="poplistfunc"></a>POPLISTFUNC
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [POPLISTFUNC](https://docs.microsoft.com/visualstudio/extensibility/poplistfunc).  
  
Dieser Rückruf wird bereitgestellt, um die [SccPopulateList](../extensibility/sccpopulatelist-function.md) von der IDE und wird durch das Quellcodeverwaltungs-Plug-in verwendet, um eine Liste der Dateien oder Verzeichnisse zu aktualisieren (ebenfalls angegeben wird, um die `SccPopulateList` Funktion).  
  
 Wenn ein Benutzer wählt die **erhalten** Befehl in der IDE, die IDE zeigt eine Liste aller Dateien, die der Benutzer abrufen können. Leider können weiß die IDE nicht, die genaue Liste aller Dateien, die der Benutzer erhalten kann; nur das plug-in enthält diese Liste. Wenn andere Benutzer das Quellcodeverwaltungsprojekt Dateien hinzugefügt haben, sollten diese Dateien in der Liste angezeigt, aber die IDE nicht, welche sie. Die IDE erstellt eine Liste der Dateien, die er davon ausgeht, dass der Benutzer abrufen kann. Bevor sie diese Liste, die dem Benutzer angezeigt wird, ruft es die [SccPopulateList](../extensibility/sccpopulatelist-function.md) `,` bietet das Quellcodeverwaltungs-Plug-in eine Möglichkeit zum Hinzufügen und Löschen von Dateien aus der Liste.  
  
## <a name="signature"></a>Signatur  
 Das Quellcodeverwaltungs-Plug-Ins ändert die Liste durch Aufrufen einer IDE implementierte Funktion mit dem folgenden Prototyp:  
  
```cpp#  
typedef BOOL (*POPLISTFUNC) (  
   LPVOID pvCallerData,  
   BOOL fAddRemove,  
   LONG nStatus,  
   LPSTR lpFileName  
);  
```  
  
## <a name="parameters"></a>Parameter  
 pvCallerData  
 Die `pvCallerData` übergebene Parameter vom Aufrufer (der IDE von) der [SccPopulateList](../extensibility/sccpopulatelist-function.md). Das Quellcodeverwaltungs-Plug-in sollte nichts über den Inhalt dieses Parameters voraussetzen.  
  
 fAddRemove  
 Wenn `TRUE`, `lpFileName` ist eine Datei, die die Liste der Dateien hinzugefügt werden sollen. Wenn `FALSE`, `lpFileName` ist eine Datei, die aus der Dateiliste gelöscht werden soll.  
  
 nStatus  
 Status des `lpFileName` (eine Kombination aus der `SCC_STATUS` Bits, finden Sie unter [Datei Statuscode](../extensibility/file-status-code-enumerator.md) Einzelheiten).  
  
 lpFileName  
 Vollständigen Verzeichnispfad der Datei hinzufügen oder aus der Liste löschen.  
  
## <a name="return-value"></a>Rückgabewert  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`TRUE`|Das plug-in kann weiterhin das Aufrufen dieser Funktion.|  
|`FALSE`|Es wurde ein Problem auf der Seite der IDE (z. B. eine Out-of Situation Arbeitsspeicher). Die Plug-in-soll Vorgang beendet werden.|  
  
## <a name="remarks"></a>Hinweise  
 Für jede Datei, die das Quellcodeverwaltungs-Plug-In hinzufügen oder aus der Liste löschen möchte, ruft diese Funktion auf, übergibt die `lpFileName`. Die `fAddRemove` Flag gibt an, eine neue Datei hinzugefügt oder eine alte Datei zu löschen. Die `nStatus` Parameter enthält den Status der Datei. Wenn es sich bei SCC-Plug-In hinzufügen und Löschen von Dateien abgeschlossen ist, gibt er aus der [SccPopulateList](../extensibility/sccpopulatelist-function.md) aufrufen.  
  
> [!NOTE]
>  Die `SCC_CAP_POPULATELIST` Funktion Bit ist für Visual Studio erforderlich.  
  
## <a name="see-also"></a>Siehe auch  
 [Von der IDE implementierte Rückruffunktionen](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [Quellcodeverwaltungs-Plug-ins](../extensibility/source-control-plug-ins.md)   
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)   
 [Dateistatuscode](../extensibility/file-status-code-enumerator.md)


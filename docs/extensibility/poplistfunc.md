---
title: POPLISTFUNC | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- POPDIRLISTFUNC
helpviewer_keywords:
- POPLISTFUNC callback function
ms.assetid: b2199fd5-d707-4628-92dd-e2a01e2f507a
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: dc15af65c6541df5ef77a3bdc85ee0e59fa20991
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="poplistfunc"></a>POPLISTFUNC
Dieser Rückruf wird bereitgestellt, um die [SccPopulateList](../extensibility/sccpopulatelist-function.md) von der IDE und wird durch die quellcodeverwaltung-Plug-in verwendet, um eine Liste der Dateien oder Verzeichnisse zu aktualisieren (ebenfalls angegeben wird, um die `SccPopulateList` Funktion).  
  
 Wenn ein Benutzer wählt die **abrufen** Befehl in der IDE die IDE zeigt eine Liste aller Dateien, die der Benutzer abrufen können. Die IDE weiß leider nicht die genaue Liste aller Dateien, die der Benutzer erhält möglicherweise; nur das plug-in enthält diese Liste. Wenn andere Benutzer das Quellcodeverwaltungsprojekt Dateien hinzugefügt haben, sollten diese Dateien in der Liste angezeigt, aber die IDE weiß nicht über diese. Die IDE erstellt eine Liste der Dateien, die wahrscheinlich, dass der Benutzer abrufen kann. Bevor sie diese Liste, die dem Benutzer angezeigt wird, ruft der [SccPopulateList](../extensibility/sccpopulatelist-function.md) `,` Kontrolle der Quell-Plug-in eine Möglichkeit zum Hinzufügen und Löschen von Dateien aus der Liste.  
  
## <a name="signature"></a>Signatur  
 Die Datenquellen-Steuerelement-Plug-in ändert die Liste durch Aufrufen einer Funktion IDE implementiert, mit dem folgenden Prototyp:  
  
```cpp  
typedef BOOL (*POPLISTFUNC) (  
   LPVOID pvCallerData,  
   BOOL fAddRemove,  
   LONG nStatus,  
   LPSTR lpFileName  
);  
```  
  
## <a name="parameters"></a>Parameter  
 pvCallerData  
 Die `pvCallerData` Parameter vom Aufrufer (IDE) übergeben, um die [SccPopulateList](../extensibility/sccpopulatelist-function.md). Die Datenquellen-Steuerelement-Plug-in sollte keinerlei wissen über den Inhalt dieses Parameters voraussetzen.  
  
 fAddRemove  
 Wenn `TRUE`, `lpFileName` ist eine Datei, die Liste der Dateien hinzugefügt werden sollen. Wenn `FALSE`, `lpFileName` ist eine Datei, die in der Dateiliste gelöscht werden soll.  
  
 nStatus  
 Status des `lpFileName` (eine Kombination aus der `SCC_STATUS` Bits; Siehe [Statuscode "Datei"](../extensibility/file-status-code-enumerator.md) Einzelheiten).  
  
 lpFileName  
 Vollständigen Verzeichnispfad des Dateinamens hinzufügen oder aus der Liste löschen.  
  
## <a name="return-value"></a>Rückgabewert  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`TRUE`|Das plug-in können weiterhin das Aufrufen dieser Funktion.|  
|`FALSE`|Auf der Seite der IDE (z. B. eine Out-of Arbeitsspeicher Situation) ist ein Problem aufgetreten. Das plug-in soll Operation beendet werden.|  
  
## <a name="remarks"></a>Hinweise  
 Für jede Datei, die die Datenquellen-Steuerelement-Plug-In hinzufügen oder aus der Liste löschen möchte, sie diese Funktion aufruft, übergibt der `lpFileName`. Die `fAddRemove` Flag gibt an, eine neue Datei, um die Liste hinzuzufügen oder eine alte Datei zu löschen. Die `nStatus` Parameter enthält den Status der Datei. Wenn SCC-Plug-In hinzufügen und Löschen von Dateien abgeschlossen ist, gibt Sie aus der [SccPopulateList](../extensibility/sccpopulatelist-function.md) aufrufen.  
  
> [!NOTE]
>  Die `SCC_CAP_POPULATELIST` Funktion Bit für Visual Studio erforderlich ist.  
  
## <a name="see-also"></a>Siehe auch  
 [Rückruffunktionen implementiert, die von der IDE](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [Datenquellen-Steuerelement-Plug-ins](../extensibility/source-control-plug-ins.md)   
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)   
 [Statuscode "Datei"](../extensibility/file-status-code-enumerator.md)